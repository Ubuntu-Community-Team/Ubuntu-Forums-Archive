---
title: "Blank screen installing 8.04 on Samsung Q1B"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by max5926 on 2008-05-25
I replaced Windows XP with Ubuntu 8.04 on my desktop time ago. I'm very satisfied and now, after porting all my documents and software to Ubuntu, I'm trying to remove XP tablet edition and install Ubuntu on my Samsung Q1B. I searched on the web and I found several pages describing "how to" and with explanations about after installation issues.
Than I start to install Ubuntu. In first I prepared an USB bootable pen and tested it on my desktop. All fine. I putted pen in Q1B, changed bios setting to boot from pen and started installation.
Loader start correctly, I see Ubuntu startup menu, I choose option (live or live install), Ubuntu show startup windows with running progress bar but, after few seconds, instead of showing gnome X11 screen, screen becomes blank and back light shut off.
I tried to launch "live install" and "live" passing parameters vga=xxx (I tried all codes reported in kernel parameters) with same result.
System is not halted. It respond to power switch and start shutdown.
Problem is only, I think, on screen resolution.


Anyone can tell me which is my mistake?

---

### Post by prestidigination on 2008-08-04
***BUMP***
I'm having the same problems. The Q1b has no CD so this is an install from USB. The hard drive is also listed as a USB device at sda1. 
I've tried the alternate CD installation to at least get an install so I can manually set the x conifg. The alternate CD installation refuses to let me mount the usb stick as a cd. The instructions provided at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) offer no usable resolutions.
The live CD on usb at least gets as far as loading X but with a blank screen.

---

