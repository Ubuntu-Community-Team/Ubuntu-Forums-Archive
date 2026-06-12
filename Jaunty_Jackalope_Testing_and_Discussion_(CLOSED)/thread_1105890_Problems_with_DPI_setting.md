---
title: "Problems with DPI setting"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tom56 on 2009-03-25
Hi

I have a 1280x800 14.1 screen on my laptop. According to [http://www.raydreams.com/prog/dpi.aspx](http://www.raydreams.com/prog/dpi.aspx) I should set my DPI to be 107. I did this in System->Preferences->Appearance->Fonts->Details, by changing the DPI setting from 96 to 107. Now everything looks pretty big (ie too big for should be a reasonable resolution). However, if I check in OpenOffice by holding up a sheet of paper to the screen it does match. What have I done wrong?

Tom

P.S. Other threads recommend running xdpyinfo|grep dots, which gave me the following:
```
tom@tom-laptop:~$ xdpyinfo|grep dots
  resolution:    101x101 dots per inch
```
Which is odd because I thought it should say 107.
P.P.S. It should be noted that even at 96 DPI, things looked a lot bigger than they did in 8.10

---

### Post by dentaku65 on 2009-03-25
> **tom56 said:**
> Hi

I have a 1280x800 14.1 screen on my laptop. According to [http://www.raydreams.com/prog/dpi.aspx](http://www.raydreams.com/prog/dpi.aspx) I should set my DPI to be 107. I did this in System->Preferences->Appearance->Fonts->Details, by changing the DPI setting from 96 to 107. Now everything looks pretty big (ie too big for should be a reasonable resolution). However, if I check in OpenOffice by holding up a sheet of paper to the screen it does match. What have I done wrong?

Tom

P.S. Other threads recommend running xdpyinfo|grep dots, which gave me the following:
```
tom@tom-laptop:~$ xdpyinfo|grep dots
  resolution:    101x101 dots per inch
```
Which is odd because I thought it should say 107.
P.P.S. It should be noted that even at 96 DPI, things looked a lot bigger than they did in 8.10

I set the DPI at 86 on my screen 1024x768 and the stuff (windows, fonts.. etc) looks pretty nicer and best fit than 96

---

### Post by MacUntu on 2009-03-25
There's nothing wrong. If you don't like the bigger fonts, you simply choose smaller font sizes. Setting the DPI to the DPI of your screen only assures that a 10pt font is really 10pt big on screen (as you noticed with your OpenOffice experiment). If you don't care you can (mis)use the DPI setting for scaling, though.

---

### Post by tom56 on 2009-03-25
Turns out this is a known bug. Since it's marked high it seems it should be fixed before release.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/310353](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/310353)

---

### Post by loomsen on 2009-03-25
Here are my settings, actually I notice quite some difference switching the Hinting.

If you choose subpixelsmoothing the hinting will be set to slight. So I manually set it to full, and now I'm fine. (This was a change from Hardy -> Intrepid... In Hardy setting subpixel smoothing enabled full hinting, since Intrepid its slight.)

Guess a shot will show best:

[[img]http://www.ubuntu-pics.de/thumb/11518/screenshot_008_3qJhFV.png[/img]](http://www.ubuntu-pics.de/bild/11518/screenshot_008_3qJhFV.png)

---

