---
title: "grub problem after install"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by mwolfe on 2007-07-16
I had installed ubuntu 6.10 on this computer a long time ago and everything installed just fine. Eventually i upgrded to 7.04 and it worked pretty good but i had a few minor problems (completely unrelated to this post)
So anyways, I downloaded 7.04 desktop cd and burned it, booted into live distro and installed.
I installed on the same partition as it was on before (Ext3) and had it format before installing. (I've installed ubuntu many times on other systems so i have plenty of experience)

However, after it finished copying files it asks to restart. Upon restart, i get a grub error 15.
So i booted live cd to reinstall grub. I used this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
and other similar articles as a reference, and i get the following.
```

grub> find /boot/grub/stage1
Error 15: File not found

```
So i checked my sdb3 filesystem. There is no /boot/grub folder (actually i'm checking /media/disk/boot as thats the drive where i have
linux installed)
the boot folder exists but no grub folder. It seems grub isnt even installing or somthing.. I can't figure out whats going on but i've ran the installer twice now with the same problem.  Any ideas?

---

### Post by Pumalite on 2007-07-16
If using 'Live CD', at step 5 or 6 it gives you opportunity to choose where to install Grub through 'Advanced Tab' Did you use it? Where did you install Grub: MBR or own partition?

---

### Post by mwolfe on 2007-07-16
the second time around i did.. I chose what it had listed already, which said
(hd0)

and thats all it said. I'm not sure if i needed to specificy hd0,3 or what..

---

### Post by mwolfe on 2007-07-16
is there a way that i can install grub without going through the full installation process?

---

### Post by Pumalite on 2007-07-16
Follow this:

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by mwolfe on 2007-07-16
THanks for the suggested download.  Unfortunately (but also fortunately) i have no patience and i simply tried again. 
I clicked the advanced tab, which is on step 7, and changed it from (hd0)
to (hd0,3)
and installed, and sure enough it works fine now. 
I have no idea why ubuntu wanted to install the mbr in the wrong place.. Previous versions didnt do this. Oh well.

---

### Post by Pumalite on 2007-07-16
Glad you got it working!

---

