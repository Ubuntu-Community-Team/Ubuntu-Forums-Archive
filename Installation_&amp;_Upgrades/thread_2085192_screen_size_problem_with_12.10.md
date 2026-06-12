---
title: "screen size problem with 12.10"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by paddy2706 on 2012-11-17
This week I finally upgraded from 11.04 to 12.10 after I had reverted from 12.04 in April, because of this very problem.

My screen dimension is correctly recognized by X:
```
[   833.413] (II) intel(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
``` and also  by xrandr: ```
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
```, but these dimensions are not used!

```
xdpyinfo | egrep 'dimensions|resolution'
  dimensions:    1280x800 pixels ([COLOR=Red]338x211[/COLOR] millimeters)
  resolution:    96x96 dots per inch
```

I am not sure if this is the very problem, but when I open a new terminal, it is huge!
[[IMG]http://img248.imageshack.us/img248/2684/bildschirmfotovom201211.png[/IMG]](http://imageshack.us/photo/my-images/248/bildschirmfotovom201211.png/)Uploaded with [ImageShack.us](http://imageshack.us)

Before, there was enough space to have four terminals alongside, and there was still some space, now this is impossible, because they will always overlap.

I have not figured out, how to force Ubuntu 12.10 to use the right dimensions and/or specify another resolution (that would be fine too).

Thank you for any suggestion!

paddy2706

---

