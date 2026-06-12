---
title: "Blank screen after installing Ubuntu 9.10"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by csk8tr on 2010-01-29
I just got done installing Ubuntu 9.10 (64-bit) on an Acer AS1810T laptop. The install part works just fine and I get through the reboot. However, there is a weird video flicker thing that happens after the machine comes back up. It appears to boot and I see text going across the screen. During a normal boot, the screen goes blank and then the text appears smaller (refreshes the resolution). However at this point, the screen goes blank and then flickers white (or light gray) for 1 second, then goes blank again for 5-6 seconds and then flickers for 1 second. It gets caught in this "loop" indefinitely. If I hit the power button, I'm able to see text with things shutting down. Not sure what the problem is, but if I had to guess, it's the video card (Intel GMA 4500M HD) or the fact that I have the hard drive set to AHCI instead of IDE. Another thing to point out is, when I boot from the USB drive and choose the Live version, it boots up with no issues.
 
Any thoughts or ideas?

---

### Post by nightwolf2k5 on 2010-02-03
I have a similar problem in that my screen sometimes goes blank and sometimes loads with weird colours. Only after several reboots does my system come to being normal.

Probably a graphics card issue.

I tried following the below link but with no avail. Maybe it could work for you.
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen) 

Note: There is no xorg.conf file, but when you will be editing a new file will pop up. And if you think of trying workaround c, there is no menu.lst file either. It has been replaced by grub.conf

Hope it helps.

---

