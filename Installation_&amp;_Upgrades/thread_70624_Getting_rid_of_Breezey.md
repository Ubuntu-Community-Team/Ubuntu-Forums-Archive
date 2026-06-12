---
title: "Getting rid of Breezey"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by schermozzel on 2005-09-30
Ok so I made space on my computer and installed the breezey preview alongside hoary. However I only had a play with it but then went back to using hoary until breezey is released because it has all my settings on it. Grub's default OS is breezey.

I want to get rid of breezey preview and update GRUB so that the default will be Hoary again. How do I do this?

Please explain in simple terms as I'm a newbie. Thanks!

---

### Post by mlomker on 2005-09-30
> How do I do this?

You can edit the /boot/grub/menu.lst file to set the default and remove the lines for Breezy if you want to.  **gksudo gedit** and then open the file to edit it.

I assume that you installed Breezy to its own partition and you could reformat it so that it is blank.

Use **sudo fdisk -l** to see what partition it is.  Then you could **sudo mkfs.ext3 /dev/XXX** to reformat it.

---

### Post by schermozzel on 2005-10-04
Where is grub located? When I installed breezy I think I reinstalled grub. If it's located on one of the breezy partitions I'll delete it when I reformat it won't I?

I managed to change the default to hoary [it's easy to do in breezy. I found a thing in system to do it]

---

### Post by mlomker on 2005-10-04
> I managed to change the default to hoary [it's easy to do in breezy. I found a thing in system to do it]

Grub is located in the MBR (master boot record) it exists on a part of the drive that is not a partition.

---

### Post by schermozzel on 2005-10-04
ahh good so If I now use partition magic  i can get rid without killing grub.

Thank you!

---

### Post by schermozzel on 2005-10-04
Right ok. Partition Magic (obviously) lables the partitions different so I'll have to do it through linux instead. How do I find out which swap partition is which.  The command **sudo fdisk -l** gives me this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5555    44620506    7  HPFS/NTFS
/dev/sda2            5556       15934    83369317+   f  W95 Ext'd (LBA)
/dev/sda3           18925       24321    43351402+  83  Linux
/dev/sda4           15935       18924    24017175   83  Linux
/dev/sda5            5556       15571    80453488+   b  W95 FAT32
/dev/sda6           15572       15803     1863508+  82  Linux swap / Solaris
/dev/sda7           15804       15934     1052226   82  Linux swap / Solaris

The last 2 are the swap partitions for hoary and breezy. How do I find out which is which?

---

### Post by dcraven on 2005-10-04
Boot into Hoary. Open the file /etc/fstab and see which partition is being used as swap it will say "swap" under the type column in that file. The other one in the list you just posted must be the one used by Breezy.

~djc

---

### Post by schermozzel on 2005-10-04
Right sda6 is hoary and sda7 is breezy

I will now delete sda4 and sda7 as they are breezy ones!

Thanks!

---

