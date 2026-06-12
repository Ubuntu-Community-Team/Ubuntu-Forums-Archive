---
title: "grub boot edit"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by james2b on 2008-03-31
I have Windows XP installed on the internal IDE drive alone, and then I put Ubuntu 7.10 onto my external SATA hard drive. I then reduced the windows main C partition and installed the newest PCLinuxOS next to XP in newly created partitions on that internal hard drive, and it did make a new GRUB boot menu, but did not include the Ubuntu on the list. Since I did print out the original /boot/grub/menu.lst file from Ubuntu, how can I add the correct line of boot information for Ubuntu 7.10, so that I can select to boot up either Linux from either the internal or the external drives? I know where and how to do the GRUB file change, but not what to include in the boot line, such as; /boot/vmlinuz - 2.6.22-14 - generic root =UUID=(a long entry), or do I need all these items listed in the grub, (title, root, kernel, initrd ) which is what I have printed for menu.lst. ?

---

### Post by zvacet on 2008-03-31
In your menu list you will see 

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

Below is one of your OS (one which shows as second) and below that add 

 title Ubuntu
rootnoverify (hd??)
chainloader +1

**(hd??)**= correct signature of your Ubuntu partition.

Save your menu list and reboot.That should do it.

---

### Post by james2b on 2008-03-31
Will the GRUB edit be the same in PCLinuxOS as it is in Ubuntu 7.10 grub menu.lst ?

---

### Post by zvacet on 2008-03-31
Read [this.](http://oldwiki.mypclinuxos.com/Dual-booting_another_Linux_with_PCLinuxOS)

---

