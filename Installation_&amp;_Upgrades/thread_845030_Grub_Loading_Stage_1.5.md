---
title: "Grub Loading Stage 1.5"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by juzar on 2008-06-30
Hi, I just installed UBUNTU 6.06 via a live CD on my GATEWAY laptop and when I reboot it shows a message "GRUB LOADING STAGE 1.5" and gets stuck...please guide me through this problem...

---

### Post by didac on 2008-06-30
Boot again with the LiveCD, start a terminal and post the results of:

```

fdisk -l

```

Then go to /media folder, open the icon for your hard disk there and go to boot/grub Copy the contents of menu.lst and post it here

---

### Post by juzar on 2008-06-30
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2329    18707661   83  Linux
/dev/hda2            2330        2432      827347+   5  Extended
/dev/hda5            2330        2432      827316   82  Linux swap / Solaris

this is the output of fdisk -l

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> Hi, I just installed UBUNTU 6.06 via a live CD on my GATEWAY laptop and when I reboot it shows a message "GRUB LOADING STAGE 1.5" and gets stuck...please guide me through this problem...

HEY!!

DO NOT CROSS POST!

You have posted this in both *Installation & Upgrades* and *Absolute Beginners Talk*.

You are wasting people's time by getting two separate lots of people independently giving you the same advice.  Have some respect for others, please.

---

### Post by juzar on 2008-06-30
SORRY everyone managed to cross post by mistake the same thread is there in the beginner's thread....sorry once again

---

