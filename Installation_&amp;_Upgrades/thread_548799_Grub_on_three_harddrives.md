---
title: "Grub on three harddrives"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by growingtedium on 2007-09-11
The problem is that my BIOS absolutely insists on booting from my SATA drive - but that disk hasn't got any operating system on it - I have two other drives for that.  I've had the NTLoader on that drive previously but would prefer GRUB.  It's all one big FAT32 partition.  The question is can I install grub onto my data drive without losing the data, and if so, how do I go about doing that?  I've installed grub  onto that drive before during a graphical Ubuntu installation but it didn't seem to take.  The computer would load up and say GRUB and hang.  If I can get the grub menu to load and find the configuration files I'll be set.
Thanks!

---

### Post by Pumalite on 2007-09-11
Usually in BIOS you can change the boot order to whatever you want...???

---

### Post by growingtedium on 2007-09-11
I know it.  I've got a miserable Dell bios.  It lets me control whether or not harddrives (lumped into one)  are booted from, and I can disable harddrives, but not the boot order of the drives.  If I disable the hd, it won't show up in the OS, so it's clearly not the ideal solution.  I updated my BIOS from version 3 to 7 in the hopes that it would improve the situation, but it was nearly identical.

---

### Post by Pumalite on 2007-09-11
Grub usually installs in what is considered sda1 in the BIOS by default, so it might be OK. ( but I'm not sure). Someone will come to confirm or deny this.

---

