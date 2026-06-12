---
title: "Installing 7.04 and having problems"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by zotamis on 2007-09-06
Hey all, Im trying out Ubuntu and im trying to install it.  The install hangs and I have a pinkish-white screen.  

any clues?

---

### Post by merlinus on 2007-09-06
Sounds like a video card problem.  Post system specs.

-merlin

---

### Post by reckless2k2 on 2007-09-06
can't he boot using a vesa option to bypass this? i can't remember. maybe i'm thinking knoppix.

---

### Post by Pumalite on 2007-09-06
You are thinking Mepis.

---

### Post by zotamis on 2007-09-06
specs

its a HP pavilion ze4900 laptop

CPU 	1.5-GHz Intel Celeron M
Operating System 	Windows XP Home
RAM/Expandable to 	512MB DDR/1GB
Hard Drive 	4200-rpm 40GB
Optical Drive 	8X DVD-ROM/24X CD-R/24X CD-RW/24X CD-ROM
Display/Resolution 	15-inch/XGA
Graphics/Video Memory 	Intel Extreme/64MB shared
Wireless Networking 	802.11b/g
Ports 	Two USB 2.0, FireWire, VGA, headphones, mic
PC Card Slots 	One Type II
Memory Card Slots 	None

well thats the specs I got off the website

---

### Post by reckless2k2 on 2007-09-07
there is a boot parameter you can pass. your dilema is not uncommon:

> If your screen begins to show a weird picture while the kernel boots, eg. pure white, pure black or colored pixel garbage, your system may contain a problematic video card which does not switch to the framebuffer mode properly. Then you can use the boot parameter fb=false video=vga16:off to disable the framebuffer console. Only the English language will be available during the installation due to limited console features. See the section called “Boot Parameters” for details.

That came from here:

[https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html)

i was thinking it was video=vesa but that must be a knoppix thing. i know a lot accept that though. i think your issue is the framebuffer gimmick. definitely try the fb-false.

can someone chime in if you have to use the alternate disc for this? i think you will need the alternate disc. you might even be able to install with no problems with the alternate disc rather than the livecd if that is what you are using.

---

### Post by merlinus on 2007-09-07
The Alternate cd will not have video problems, since it is text-based.

-merlin

---

