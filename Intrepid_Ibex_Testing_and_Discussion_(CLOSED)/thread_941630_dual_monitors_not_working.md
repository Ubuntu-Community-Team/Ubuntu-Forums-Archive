---
title: "dual monitors not working"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Shardsofmetal on 2008-10-08
I have an Acer Aspire 6920 laptop. I have an external 19-inch monitor plugged in. I set it up so that the external monitor is to the right of my notebook monitor, and everything appears as if it's working, but it's sending no output to the monitor. Also, it shows its max resolution as 1280x960 when it's really 1440x900. I'm using Kubuntu, but that shouldn't matter as unless I'm wrong, this an an issue with X. Can anybody help/does anybody know what is wrong? Thanks

---

### Post by olavjunior on 2008-10-08
I've had a lot of issues with xrandr (screen resolution applet). See my post at launchpad [https://bugs.launchpad.net/~olav-ekkje](https://bugs.launchpad.net/~olav-ekkje)

My advice would be to try to just use the extended monitor and not the laptop and see if that helps getting the monitor on. Else, try starting x with the monitor plugged in. If not, I've just tried over and over again, and suddently things work out the way I want. But yes, it's messy... Good luck!

---

### Post by philinux on 2008-10-08
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by olavjunior on 2008-10-08
Well, screen resolution applet automatically adjust your virtual size

---

### Post by Shardsofmetal on 2008-10-08
I will try the first option to add the single chunk of text to xorg.conf a little later and see if that works (right now I'm backing up my Windows files). I have in the past tried and failed manually configuring dual monitors, and I hope this time I will be successful (it's probably the last thing that I still consider Windows superior in). I have one question though, it says at that article that with a virtual desktop larger than 2084x2084, 3D acceleration is disabled. If I have a larger horizontal resolution, but a smaller vertical resolution, and there are still less total pixels, will 3D acceleration still be available? Thanks

---

### Post by olavjunior on 2008-10-08
I don't know how the pixels gets calculated. But you'll find out right.. Just wondered, do you use dvi/hdmi or vga? Also let me know you're xorg if you manage, cause I didn't! And I'm sick and tired of the f... up xrandr. I would rather struggling with xorg.conf then some wheel of fortune xrandr! Cause that's what it is, it's a mess :(

---

### Post by Shardsofmetal on 2008-10-08
The setup I would like to have is my laptop display being at the left. It has a resolution of 1366x768. To the right of that, connected by VGA, is my TV/monitor with a resolution of 1440x900. I'm using the most recent beta of Kubuntu. Right now, I am unable to get the GUI tools for configuring the displays to work. My monitor now has output, but no matter what I tell the display applet, the monitor just clones the main display (when the full resolution is set, it becomes the main monitor, with my laptop showing as much of it as it can fit). Also, every few seconds my computer resets the output to my monitor. I don't know if it's activating my monitor's re-align function every time, but it is annoying nonetheless. I tried the first suggestion from that wiki page, and it hasn't seemed to work. Before trying to manually configure, I want to know if having displays of different sizes (and aspect ratios, 16:9 and 16:10) will create any problems. So that's what I'm dealing with, any advice? Thanks again

---

### Post by Shardsofmetal on 2008-10-09
Anybody have any ideas?

---

