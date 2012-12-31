---
layout: project
title: jQuery Simple Slider
tagline: Unobtrusive Numerical Slider
version: 1.0.0
github_repo: jquery-simple-slider
download_url: https://github.com/loopj/jquery-simple-slider/zipball/master
extra_head: |
    <script type="text/javascript" src="js/simple-slider.js"></script>
    <link rel="stylesheet" href="css/simple-slider.css" type="text/css" />
    <link rel="stylesheet" href="css/simple-slider-volume.css" type="text/css" />
    <style>
    [class^=slider] { display: inline-block; margin-bottom: 0}
    </style>

---


Instant Demo
------------
<input type="text" data-slider="true" data-slider-theme="volume" />
<span style="vertical-align: top"></span>
<script>
$("[data-slider]")
  .bind("slider:ready slider:changed", function (event, data) {
    $(this).nextAll("span").html(data.value.toFixed(3));
  });
</script>


Drag the slider above. More demos can be found [here](demo.html).


Overview
--------
Simple Slider is a jQuery plugin which allows your users to select a value
from a numerical range by simply dragging a slider.

Features
--------
- Configurable without editing any JavaScript
- No external dependencies, apart from jQuery
- Compact size, only 4kb
- Unobtrusive JavaScript, active using `data-slider="true"` on any input
- Easy to skin/style purely in css, no images required
- Slider value goes directly into your input element, for easy use in normal html forms
- Supports both pre-defined values and a continous ranges
- Supports smooth sliding and snap-to-value sliding


Screenshots
-----------
<div style="text-align: center">
  <img src="budget-slider.jpg" style="margin-bottom: 5px"><br>
  The slider's default style, as used to select a budget on [Bugsnag](https://bugsnag.com).
</div>

<div style="text-align: center; margin-top: 40px; margin-bottom: 40px">
  <img src="volume-slider.jpg" style="margin-bottom: 5px"><br>
  A slider using the volume style.
</div>


Installation
------------

Include jQuery and the Simple Slider JavaScript and CSS files on your page,
then activate Simple Slider on your text input using the `data-slider` attribute:

{% highlight html %}
<!-- Include jQuery -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>

<!-- Include Simple Slider JavaScript and CSS -->
<script src="yourfiles/simple-slider.js"></script>
<link href="yourfiles/simple-slider.css" rel="stylesheet" type="text/css" />

<!-- Activate Simple Slider on your input -->
<input type="text" data-slider="true">
{% endhighlight %}

You can also manually turn any text input into a Simple Slider in JavaScript 
as follows:

{% highlight javascript %}
$("#my-input").simpleSlider();
{% endhighlight %}


Getting Slider Values
---------------------

The value the user selects with the slider is immediately available inside the
`value` attribute of the text input you attached the slider to. This means you
can include Simple Slider in your HTML forms and the the selected value will
automatically be send to your server when the form is submitted.

If you would like to get the slider's value using javascript, you can register
for the `slider:changed` event:

{% highlight javascript %}
$("#my-input").bind("slider:changed", function (event, data) {
  // The currently selected value of the slider
  alert(data.value);

  // The value as a ratio of the slider (between 0 and 1)
  alert(data.ratio);
});
{% endhighlight %}


Configuration
-------------

You can configure Simple Slider by either using `data-slider-*` unobtrusive
javascript settings, or by passing in a configuration object when initializing
the plugin manually.

data-slider-range
:   The range representing the start and end of the slider. Eg. 
    `data-slider-range="10,1000"`

data-slider-step
:   The interval to move when dragging the slider. Eg. `data-slider-step="100"`

data-slider-snap
:   Setting this to true makes the slider snap to each step when dragging,
    otherwise dragging will be continuous. Eg. `data-slider-snap="true"`

data-slider-values
:   A pre-defined list of values to allow sliding for.
    Eg. `data-slider-values="0,100,500,800,2000"`

data-slider-equal-steps
:   Setting this to true makes the spacing between each always value equal
    when used with `data-slider-values`. Eg. `data-slider-equal-steps="true"`

data-slider-theme
:  The CSS theme to use when rendering this slider. Setting this value adds
   a suffix to the CSS class of the slider. Eg. `data-slider-theme="volume"`


Events
------

You can bind to the following jQuery events using `bind`, for example:
`$("#my-input").bind("slider:ready", function (event, data) { ... })`

slider:ready
:   Fired when the slider is loaded and attached to your input field.

slider:changed
:   Fired when the value of your slider changes.

All Simple Slider events pass 2 parameters into your function, `event` and
`data`. `event` is a regular jQuery event object. `data` contains the 
following properties:

value
:   The current value of the slider.

ratio
:   How far, as a percentage, the slider is from start to end (0 - 1).

el
:   The generated outer HTML element representing the slider.


Methods
-------
`selector.simpleSlider("setValue", value);`
:   Sets the value of the slider.

`selector.simpleSlider("setRatio", ratio);`
:   Sets the ratio (see above) of the slider.


Reporting Bugs or Feature Requests
----------------------------------
Please report any bugs or feature requests on the github issues page for this
project here:

<https://github.com/loopj/jquery-simple-slider/issues>


License
-------
Simple Slider is released under the MIT license.