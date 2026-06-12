---
title: "ASUS R510J issue witch touchpad -Ubuntu 16.04 -multitouch and scroll did not working"
date: 2016-10-26
forum: Installation &amp; Upgrades
---

### Post by denail2 on 2016-10-26
Hello

I just installed newest version of Ubuntu on my laptop ASUS R510J and I notice that touchpad don't work like it should be.
Multitouch and scrolling is not working, also r.m. button (taping two fingers on touchpad).
I trying to find some proper solution on Internet, but without any good results.
synclient VertEdgeScroll=1
Couldn't find synaptics properties. No synaptics driver loaded?
sudo apt-get install xserver-xorg-input-synaptics

This is information which I get by command   sudo libinput-list-devices   and it quite streange, because I did not usign any Logitech mouse.
Device:           PS/2 Logitech Wheel Mouse
Kernel:           /dev/input/event6
Group:            8
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat*adaptive

I also used around 2-3 years ago Ubuntu, and such kind of problem never exist.
Any advice will be appreciate,  thanks you all!

---

