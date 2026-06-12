---
title: "Boot preference needs changed"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by Cee64E on 2010-12-13
This is probably a common question but I haven't seen anything that quite relates.

I have a dual booted PC with WinXP Pro and Ubuntu 10.10.  The Ubuntu is the recent addition.  

The boot choice menu pops open on startup just fine and I can boot to either system with no problem.  What I would like to change is the default boot.  Right now it defaults to Ubuntu after ten seconds of no input.  I would like it to default to XP while I learn the ins and outs of Ubuntu and track down drivers and such.  Anyone know how I might do this?

---

### Post by Quackers on 2010-12-13
If you install Startup Manager via synaptic package manager you can set the default operating system. However, this may be over-written in the future. To do it permanently you would need to edit the GRUB_DEFAULT=0 line in the file /etc/default/grub. The guide below gives more info.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

