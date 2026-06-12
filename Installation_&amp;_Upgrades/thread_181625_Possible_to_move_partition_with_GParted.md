---
title: "Possible to move partition with GParted?"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by Paradoxdruid on 2006-05-24
I'm currently trying to get my Ubuntu running Koala mini PC from [System76](http://www.system76.com) to dual-boot with WinXP (I use the Koala as a great multimedia center, and want to try playing Windows-only games on my TV as well).

I downloaded and used a liveCD with GParted, and was able to resize my current ext3 partition, leaving 20 GB of unpartitioned space.  But the ext3 partition is at the beginning of the drive.  I've heard that Windows often has "issues" with not being the first partition on a drive.  Is this something I need to beware of still?

And if so, is it possible to use GParted (or another tool) to move where a partition is on a drive without formating that partition?  Say, move the 20 GB of unpartitioned space to the front of the drive, moving the ext3 partition to near the end (The swap is already at the end).  Gparted seems to include "Move" with "Resize", but it won't seem to work for me.

Thanks for any advice!

---

### Post by Sutekh on 2006-05-24
I can't remember where the table is in GParted, but here it is on the web

[http://gparted.sourceforge.net/screens/gparted_10_big.jpg]("http://gparted.sourceforge.net/screens/gparted_10_big.jpg")

ext3 partitions can't be moved. Can you resize it to go to the end of the drive, then resize it away from the beginning of the drive?


In regards to Windows and the first partition. Ubuntu's bootloader GRUB is capable of fooling Windows into believing that it is on the first partition. If Windows isn't installed however, the way will be hard.

When you install Windows, whether it allows you to on the end of the drive or if you re-arrange the ext3 partition and put Windows at the front of the drive, it will take out GRUB and replace it with its own bootloader. You will need to get GRUB back by following this link

[Ubuntu Wiki - Recovering Ubuntu After installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

Once GRUB is back you can trick the Windows installation into believing it is on the first partition (unless you resize the ext3 partition and it *is *on the first partition) by using the **map** commands in the GRUB menu entry for Windows. When you recover GRUB his should be automatic. GRUB is quite capable of detecting the Windows installation and making the neccessary adjustments.


All this is way ahead assuming you can install Windows at the end (or beginning) of the drive, then get GRUB and Ubuntu back.

---

### Post by aysiu on 2006-05-24
This is what I would do:

1. Resize the current Ubuntu partition to be as small as possible. This must be done with a live CD. ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` While you're in GParted with a live CD, create a new Ext3 partition. Pay careful attention to the partition numbers. 

2. Then edit your sources.list on the live CD to include the Universe repositories and ```
sudo apt-get update
sudo apt-get install partimage
sudo partimage
``` and copy the Ubuntu partition from the first partition to the one you just created in GParted.

I believe there's a function in PartImage, where you can copy the boot loader, too, but you can always restore Grub to the MBR later using the instructions Sutekh linked to.

Mount your newly copied partition and edit the /etc/fstab file ```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` to reflect the number changes in the partitions... for example, / may now be mounted at /dev/hda5 instead of /dev/hda1.

3. Install Windows on the first partition. Make sure it works.

4. Restore Grub to the MBR.

---

