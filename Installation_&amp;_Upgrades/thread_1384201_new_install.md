---
title: "new install"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by richarjohn on 2010-01-18
i am running  hardy heron 8 .04 and having a few problems with the terminal, and the monitor graphics are not very good  22 monitor hanns.g hdmi hg216d  so i would like to do a reinstall with the latest vision 9 .1o 
i am running a grub duel boot  windowsxp anb ubuntu how do i go about installing the new version do i just upgrade or does it have to be a fresh install and how do i uninstall the present vision

 pentium4 cpu3 ghz 1gig ram  22montor nvidia geforce fx5500 any help

 i would very grateful
                     regards richard

---

### Post by mikewhatever on 2010-01-18
You can't upgrade directly from 8.04 to 9.10, so it's a reinstall is necessary.

Uninstalling 8.04 isn't needed, just format its partition, and it's gone. Be sure to backup your files before doing that.

---

### Post by audiomick on 2010-01-18
If you have /home on a separate partition, you can re-mount it to the new install, thereby retaining your data and settings.

If you don't there is a guide here
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
on how to set it up.

---

### Post by richarjohn on 2010-01-19
all the ubuntu o/s is on one partition do i need to use the termial to reformat this partition

---

### Post by presence1960 on 2010-01-19
> **richarjohn said:**
> all the ubuntu o/s is on one partition do i need to use the termial to reformat this partition

***_Back up any data you do not want to lose_***. Then from ubuntu Live CD open a terminal and run ```
gksu gparted
```
This will open gparted and you can format the partition. Once completed you can install the new ubuntu version to that same partition. leave the swap partition alone as the installer will recognize it and mount it as part of the install process. When install is complete you can move your data back.

---

