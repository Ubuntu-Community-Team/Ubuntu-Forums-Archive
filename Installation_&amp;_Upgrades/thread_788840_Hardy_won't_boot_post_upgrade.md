---
title: "Hardy won't boot post upgrade"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by epidemiks on 2008-05-10
Hi, 
I just updated to 8.04 from 7.10.

I'm running XP on a second drive and can still boot into it from GRUB no probs.

Upgrade went smoothly, no obvious issues, but upon reboot I get:

```
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 acion 0x2 frozen
ata1.01: cmd C8/00.08.00.../fo tag 0 dma 4096 in
Buffer I/O error on device sdb, logical block 0

```
and end up at a Busybox prompt.
Any ideas how to fix? 
Thanks!

---

### Post by epidemiks on 2008-05-10
Hmm.
I can boot into the 2.6.22-14 rt kernel, but having some graphics problems - nvidia geforce 7600gs res issues which i'm working on, but still won't boot into the -17 kernels..
whats the difference between the -14 and -17 kernel

---

### Post by RDL89 on 2008-05-10
I have the very same thing you describe. My screen resolution is about 640 x 480. I've tried everything.I have an nvidia graphics card. 

If I try to boot into kernel 2.6.24.17 I get kernel panics, but if I go into 2.6.22.14 I can boot, only to run into the screen resolution issue. I can't even get to the the "system" link in the menu bar, too many other things are in the way.

---

### Post by mdmcginn on 2008-05-10
Lots of similar problems, described in [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

---

### Post by epidemiks on 2008-05-11
RDL89: I sorted the graphics with EnvyNG, though i could get to my menus even in 640x480 (which does not look good on a 22" ws lcd)

mdmcginn: all hdd's are ide, and its 8.04 is already installed, just won't boot now.. 
its a long thread, so i'll have a good scour through. cheers

---

