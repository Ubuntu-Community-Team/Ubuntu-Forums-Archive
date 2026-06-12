---
title: "Dual Boot"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Miykel on 2012-02-24
G'Day;  I've been searching all over the place but can't find this answer, if someone knows the link or has any suggestions I would greatly appreciate the help;
  The problem is I have Ubuntu 11.10 install using Wubi but want to install it using the disc, when I do I loose W7, the Windows boot loader is not there and grub doesn't have the W7 option, I read a page somewhere about using the W7 disc to repair the Windows boot loader after installing Ubuntu but can't find the page anywhere. Ant help would be greatly appreciated.
regards Miykel

---

### Post by oldfred on 2012-02-24
Its reinstalling the grub2 boot loader after a Windows install that is usually the issue.

Have you installled to a partition as the wubi boot loader has to boot thru the Windows boot loader. But a full install to a partition boots with grub2's boot loader.

If a full install to a partition have you run this:
sudo update-grub

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Miykel on 2012-02-25
G'Day and thanks oldfred for the reply and the links, I got the OS installed fine but I couldn't do anything with Grub, tried everything in the links but no good, either ended up with no bootloader at all and just booted into Ubuntu or straight into windows, so I'll have to stick with grub I guess, thanks again for your help.
Regards  Miykel

---

