---
title: "new computer, ubuntu won't boot"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by iamah on 2008-10-11
Hi, I got this new computer, and for the first time in a long time I can't boot into a live cd...

I get Busybox, (initramfs)... Is there a workaround?

The hardware: 
XFX nforce 750a SLI
amd x2 5200
ECS geforce 9800gt
dual ddr2 800 kingston

:confused:

---

### Post by iamah on 2008-10-11
well, its not solved but I found another thread, altough I couldnt find a solution... I have 1 sata hd and 1 sata dvd

---

### Post by zekica on 2008-10-11
Can you try setting sata in bios to work in compatibility mode? You may have a new sata controller which is not yet supported in ubuntu. 


You can also download a beta version of ubuntu 8.10, and see if it works without changes in your bios. However, it is not recommended to install a beta version as it may crash with updates.

---

### Post by Rorke on 2008-10-11
you could like the thread, then I could find it too!

---

### Post by iamah on 2008-10-14
This worked for me
[http://ubuntuforums.org/showthread.php?p=4809508#post4809508](http://ubuntuforums.org/showthread.php?p=4809508#post4809508)
well, I could run the cd and install, but when running from hd i got busybox again... i think its just a matter of finding where to speify those options

---

### Post by Arthur Millar on 2008-10-19
sata hdd + ide DVD/RW
I set my ide settings to legacy IDE 
slave setting did'nt matter

---

