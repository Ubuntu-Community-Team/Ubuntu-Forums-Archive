---
title: "Dell Inspiron Display Issue"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by MontyM on 2006-04-13
Well I got through the install using an external CRT display.  But I cannot switch to the LCD display.  ATI Mobility Radeon X300 1920x1200

Any suggestions?

Thanks Again

Monty

---

### Post by FredSambo on 2006-04-13
did you install all of the updates?  i had a similar issue, but once i installed the updates which came with the latest kernel, it fixed the issue for me on one my dell inspiron lappys at work.

i was all like, "woah it worked!"

---

### Post by brim4brim on 2006-04-13
I had the string you need to do this but I can't remember what it is.  It's in the forums somewhere so can search for it.  no apci I think is part of it but there's a string to tell the installer not to detect your video card so it uses generic drivers which will get it working.  I had this problem with my laptop when I went to install Ubuntu.

However if you want your 3d card to work properly, you'll need to install the drivers for it.  If you have an ATI card your pretty much out of luck here.  The ATI laptop support is dire last time I tried to install the drivers, I couldn't use Gnome anymore and ended up at the terminal.  However if you have nVidia you can use the generic driver installation or use your external CRT now and then update the drivers from Synaptic probably or if they aren't the latest drivers, you can get the .run installer from nVidia's website.

Opps just saw your using ATI X300, I have X600 and have never gotten 3D working properly.  There are a number of threads on the issue here.  You maybe able to get the X300 working (I'm pretty sure I saw someone got it working, try a forum search).  Otherwise you'll need to find the post with the options like I said at the start of the post meaning you'll have limited Open GL support (as in, you probably won't even be able to run an Open GL screensaver with a proper framerate).

---

