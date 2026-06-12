---
title: "multiple screen setup with large virtual screen height"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by volkium on 2009-12-19
Hi,

I'm having trouble creating a virtual desktop out of two screens. It may be a bit unrealistic but would be great for working on documents. Okay, here it comes:

Ubuntu 8.10 installed on notebook (Fujitsu Siemens Lifebook with Intel video)
Screen is 1280x800
connected via VGA: Samsung 245b with pivot function enabled (have to remove a screw in the stand...)
resolution is 1920x1200

Now I want the Samsung to be "on top" of the laptop screen so I would get a virtual desktop of the dimension 1280x2720.

Sadly the screen resolution setup utility overlaps the screens as is shown in the first attached picture. If the Samsung is not pivoted and the resulting virtual screen is 1920x2000 everything works fine.

Xrandr gives me the output as in the second attached picture. Basically I'm looking for a way to correct the offset of the LVDS screen to 0 1920 so the line should be:
LVDS ... 1280x800+0+1920 ...

My /etc/X11/xorg.conf is pretty dull, nothing special here, only "Default" stuff and frankly I never liked the idea of editing it ( ;-) ) if there's a more comfortable way of dealing with settings.

I've read in some forums that one has to increase the allowed virtual screen size because above 2048x2048 is not allowed. Also I've found rumors about the intel drivers or hardware not enabling larger virtual screens. Though you can configure the two side by side with 3200x1200. 

Can anyone give an explanation how to do it?

btw, who else thinks that the "devolution" to 16:9 in screen sizes is crap? Who needs width, I need heigth to work ergonomically ;-) Does really everybody only uses their laptop to watch movies???

---

