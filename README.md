anim
====

Anim is a tiny and bare bones animation library weighing in at `2.8 KB` in plain code, `1.5 KB` when minified and `0.9 KB` when minified and gzipped.

Usage:
=====
``anim(node, prop, to, duration, ease, from, unit)``

* **node**: the node to animate
* **prop**: the CSS property to animate; in JavaScript notation ("margin-left" --> "marginLeft")
* **to**: the end value of the CSS property. Can be number or string with optional units. e.g., 100, "100px", "50%", "3em"
* **duration**: time in seconds to run animation. e.g., 3.5 is 3.5 seconds

optional parameters are:
* **ease**: easing function name. Choose from "ease-in", "ease" (means: ease-in-out), "lin" (means: linear), and undefined means "ease-out".
* **from**: the starting value of the CSS property. If not supplied, it is read from the node
* **unit**: the unit of measurement. e.g., px, em, %, pt. This can be provided in the "to" parameter too

This function returns an object with one method ("then") which functions similar to Deferred (Promise/B), which gives you a callback function that is called after the animation is done.

Examples:
=====
    anim(box, "opacity",    0.2,    2);
    anim(box, "height",     300,    2,   "ease-in");
    anim(box, "height",     "14em", 2,   "ease-in");
    anim(box, "height",     14,     2,   "ease-in", null, "em");
    anim(box, "marginLeft", "2%",   2,   "ease-out");
    anim(box, "fontSize",   "20pt", 2.5, "lin",    12);
    anim(document.body, "scrollTop", 500, 5);

    //run 2 animations one after the other
    anim(box, "height", 300, 2).then(function() { anim(box, "width", 300, 2) });
