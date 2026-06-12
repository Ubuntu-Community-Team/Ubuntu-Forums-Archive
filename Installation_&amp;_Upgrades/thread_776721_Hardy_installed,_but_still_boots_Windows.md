---
title: "Hardy installed, but still boots Windows"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by NinjaMidget25 on 2008-04-30
I wanted to do a dual boot Ubuntu/Windows XP system while I am preparing to transition to a 100% linux environment.

The install went fine with no errors, but I don't get the grub boot loader menu when I boot the computer.   It just goes straight into XP.   How can I fix this?

---

### Post by Pumalite on 2008-04-30
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by warb on 2008-04-30
I had the same problem. I installed Kbuntu on the disk it wanted,but it was not the disk Vista is on. Install went fine,
but a reboot took me to Vista. Looks like GRUB did not install
on the MBR. Tried to boot from the disk Kbuntu was installed on
got Grub 
Error 22

Any Ideas?

Thanks.

---

### Post by NinjaMidget25 on 2008-04-30
Ok, I did everything according to the instructions in that thread and grub installed without errors, but I still boot directly into XP

I'm not sure if this matters, but during the install, my XP install showed up as a vista/longhorn partition.   I did have Vista installed on this computer...which is why I downgraded to XP and decided to start moving to all linux.

---

### Post by Pumalite on 2008-04-30
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by NinjaMidget25 on 2008-04-30
Going off the instructions on the grub page, in the example the command and response is
```
grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

```

I get no filesystem type when I enter my root info

---

### Post by NinjaMidget25 on 2008-04-30
ok, strange problem, but it works now.    I have 3 SATA drives in my computer.   When I disconnected all but the primary drive that my os's are installed on, I got the grub loader.   I had to spend a couple minutes trying the drives on various sata channels, but now all of my drives are connected and I can boot into xp or hardy.   I don't know what the problem was, but I suspect it was related to an issue that I had when I installed vista, and I think it kept installing the mbr to my 500gb secondary drive.  Anyway, it works now and I'm that much closer to being windows free....w00t!

Thanks for the help

---

