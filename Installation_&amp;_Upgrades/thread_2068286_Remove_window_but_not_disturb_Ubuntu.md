---
title: "Remove window but not disturb Ubuntu"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by Confused2570 on 2012-10-08
Hello! Right, I've been using ubuntu for a while now as a dual boot with windows xp. I like it enough now and I want to remove windows completely. I don't want to lose any of my data on my current ubuntu installation. Is there any way I can delete the windows partition without having to completely reinstall ubuntu?

---

### Post by rhlegion on 2012-10-08
I don't know if it would work or not but try maybe looking into using a partition tool to just delete windows partition and expand your current ubuntu partition :)

They have live cd's you can make with Gparted

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by varunendra on 2012-10-09
Assuming it is not a WUBI installation, but a normal one on its own partition, +1 to what *rhlegion* suggested. Just delete or format the xp partition using gparted. You can then either expand an existing partition to cover that space, or use it as a separate data partition for Ubuntu. If you choose to format, rather than merging it in an adjacent partition, I'd suggest to format it as ext4, since the system is going to be Linux-only.

The gparted tool is already included in the Ubuntu live cd.

If you choose to 'expand' a partition to merge the existing XP partition in it, BE CAREFUL to NOT move the LEFT edge of your 'root' partition, as doing so will render the installation unbootable (although that can be easily fixed by reinstalling just GRUB, but why bother?). [COLOR=DarkRed]Also, be informed that resizing a partition from its LEFT edge often takes enormous amount of time, even if the partition is empty, while deleting-recreating will be done almost instantly.[/COLOR]

To avoid accidental mistakes, it is better to install and run gparted from within the existing installation. While connected to internet, you can install it with
```
sudo apt-get install gparted
```

---

### Post by Confused2570 on 2012-10-09
That worked! Thanks to both! :)

---

