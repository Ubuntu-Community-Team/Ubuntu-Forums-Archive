---
title: "changing resultion"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by amirpasha on 2007-08-15
Hi
I am a newbie,

hardware preferences:
[LIST]
[*]os verison: **Ubuntu 7.04**
[*]graphic adaptor: **MSI GeForce 5200** (with 128MB of memory)
[*]monitor: **Hansol 17" (710D)**
[/LIST]

Well, I've installed proper driver for my graphic adaptor using Automatix, and well it seems that my graphic adaptor is recognized correctly, and I enabled desktop effects,

the problem I have that bothers me a lot is the only available resolution is **800x600**! ](*,) (it is the only resolution available in **Screen Resolution** program ](*,) ) and I could not change it to a higher resolution. 
well with my graphic adaptor and monitor...

by the way I have no problem in Windows XP and I could easily switch to 1280x1024 or 1024x768 (and many more resolutions).

How could I solve this problem?

---

### Post by Pumalite on 2007-08-15
Installing proprietary driver, probably 'Legacy': [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by dongthao on 2007-08-15
Try to add the expected resolution to your xorg.conf file (/etc/X11/xorg.conf), remove the others at all and reboot.

---

