---
title: "Grub to MBR"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mpgarate on 2007-05-28
I had multiple ubuntu installations on 1 partition HD, and I just formatted one of the partitions to remove a ubuntu installation on it. after a restart, I got grub error 23. After a google, im assuming thats because it still wanted to look for and boot the partition I just formatted, but could not. How can I modify and apply to the master boot record an updated grub bootloader?

---

### Post by confused57 on 2007-05-28
You can use the live cd to install whichever Linux distro's grub that you want to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mpgarate on 2007-05-28
thanks! I took the easy way out, backed up my files, and re formatted the drive :(

---

