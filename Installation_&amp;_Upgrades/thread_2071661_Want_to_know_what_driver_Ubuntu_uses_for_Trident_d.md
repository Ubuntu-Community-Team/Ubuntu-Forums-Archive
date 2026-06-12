---
title: "Want to know what driver Ubuntu uses for Trident display"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by Lloyd Ewing on 2012-10-16
I have an older Toshiba laptop computer which uses the Trident 9540 chip set for the display.  Installing Lucid 10.04 goes well, but the system hangs during the restart.  I can boot to the command line from Grub.  Is there some way to find out what driver Ubuntu uses for this display?  lshw doesn't show a driver so it must not be loaded when I get to the command line.

There are known bugs in the Trident display driver for Ubuntu.  One of the bugs causes the system to go into an infinite loop when X is started.

From searching the net I find out that there were at least two Linux drivers for the Trident chips, Xfree86 and a "framebuffer driver".  I would like know how to find out what driver Ubuntu uses.

These are the details in case anyone wants more info about my problem:  
The Toshiba 7200CT laptop has a 600 MHz Pentium 3 processor, and the specifications say that the video is a "Trident CyberBlade e-4 128-bit graphics accelerator". The most likely cause of my problem is this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/223774](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/223774)
Creating an xorg.conf file indicates (and lshw) say that my video is: "BoardName Cyber 9540" Searching for trident "9540" and "e4" seems to indicate that they are synonymous.

Many thanks for any help,
Lloyd

---

### Post by papibe on 2012-10-16
Hi Lloyd Ewing.

> **Lloyd Ewing said:**
> Is there some way to find out what driver Ubuntu uses for this display?
Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by Lloyd Ewing on 2012-10-16
This is the result:

01:00.0 VGA compatible controller [0300]: Trident Microsystems Cyber 9540 [1023:9540] (rev 52)
Kernel modules: tridentfb

Doing a quick Google search for "tridentfb" looks like this driver is the "frame buffer" version.
[http://wiki.gentoo.org/wiki/Trident](http://wiki.gentoo.org/wiki/Trident)

Wonderful!  Now I need to find out how (if) I can install the Xfree86 driver, but probably I should post another question for that.

Thanks!
Lloyd

---

