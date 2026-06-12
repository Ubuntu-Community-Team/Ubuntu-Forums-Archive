---
title: "I want to dualboot but my condition is a bit unusual"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by dragoshsd on 2008-03-27
This is how my partitions look like at the moment: [http://img85.imageshack.us/img85/9798/xyzhddeq9.jpg](http://img85.imageshack.us/img85/9798/xyzhddeq9.jpg)
I would like to install Ubuntu on the space that is currently reserved for my C: partition (the boot.ini file is there, and also a winxp installation that i no longer need), while keeping my windows instalation from D: unharmed. I do not have any experience with linux/ubuntu so you can see why I got stuck when I tried to install Ubuntu 7,10. Any help would be appreciated.

---

### Post by mikewhatever on 2008-03-27
C:\ is almost full, so you can't resize it and if you delete it, your Windows on D:\ will become unbootable. It looks like you'll need toreinstall XP to C:\ first.

---

### Post by dragoshsd on 2008-03-27
If I delete C: and then install Ubuntu to a new partition there, won't Grub be able to make my D: windows be bootable again?

---

### Post by dstew on 2008-03-27
Grub can only boot a "bootable" operationg system. If your D: partition Windows installation is bootable from your BIOS, then grub can boot it too. If D: is not bootable, grub cannot make it bootable. You said your boot.ini file is in your C: partition, so it seems that you usually boot that partition. If you delete it, you might not be able to boot D:

You can test if the D: partition is bootable by using a Windows CD recovery console. You can test if grub can boot the D: partition without installing it. You can use a [supergrub disk]("http://supergrub.forjamari.linex.org/") to try to boot D:, or even a [grub boot floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy"). With a grub boot floppy, you get a grub command line, and you can enter the commands to try to boot on it, like```
root (hd0,1)
makeactive
chainloader +1
boot
```Come to think of it, you can do the same from an Ubuntu Live CD. Just issue the command```
sudo grub
``` in the terminal, and you will get a grub command line.

---

### Post by mikewhatever on 2008-03-27
> **dragoshsd said:**
> If I delete C: and then install Ubuntu to a new partition there, won't Grub be able to make my D: windows be bootable again?

No, because the files needed to boot it reside on C:\. As you said, your condition is unusual. Here is a thread dealing with the similar setup [http://ubuntuforums.org/showthread.php?t=722468](http://ubuntuforums.org/showthread.php?t=722468)

---

