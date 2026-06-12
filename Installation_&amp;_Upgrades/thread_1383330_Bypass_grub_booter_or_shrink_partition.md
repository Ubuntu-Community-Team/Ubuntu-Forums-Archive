---
title: "Bypass grub booter or shrink partition"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by obvious_hat on 2010-01-17
Hey, I've recently bought windows seven to upgrade my vista. However when I selected it on the booted installer it said that it couldn't do it from there. Me being my idiotic self, I thought that the ubuntu partition was interfering, I now realise that it meant that I needed to run it from vista. Anyway, I deleted the ubuntu partition and expanded the windows partition to fill the whole hard disk. However, now, the grub booter has stopped me from getting to windows to do so, which, quite annoys me.  I tried to install ubuntu again, but, gparted keeps telling me that it can't shrink the volume of the windows partition, which means I can't install ununtu without destroying my files on windows; this kinda defeats the purpose of keeping my files.

Tl;dr: I want to bypass the grub booter or find some third party bootable software to shrink a partition so I can install ubuntu. Thanks in advance

---

### Post by John Bean on 2010-01-17
Boot a Ubuntu live CD, then:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This restores the default MBR (ie removes GRUB) and allows Windows to boot normally.

After booting Windows to "clean" the NTFS partition (defrag it while you're there!) you should find that Gparted will now work as expected.

---

### Post by obvious_hat on 2010-01-17
Thankyou, very very much! that really helped!

---

### Post by Mark Phelps on 2010-01-19
But, to be safe, do NOT use the Ubuntu installer to shrink the Vista partition; instead, use the Vista Disk Management utility to do that.  This prevents the problem where, in some cases, GParted shrinkage of Vista partitions has resulted in filesystem corruption preventing future Vista booting.

---

