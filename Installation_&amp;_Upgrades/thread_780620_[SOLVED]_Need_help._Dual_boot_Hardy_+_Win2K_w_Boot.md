---
title: "[SOLVED] Need help. Dual boot Hardy + Win2K w/ Bootmagic"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by cmbcne on 2008-05-03
Hi.

I have:
P-III, 550 MHz, 512 MB Ram, Two IDE hard drives:
drive 1 has Win2K installed
drive 2 I use for Linux.
drive1/Win2K has Partition Magic and Boot Magic installed.

Over the past couple of years I've installed more than a dozen flavours of Linux, the most recent being Kubuntu 7.10.

I have just tried to install Ubuntu 8.04, Xubuntu 8.04, and Kubuntu 8.04 (KDE4 remix).  All three have failed with the same problem.

Problem:  During the install, I choose "manual" partitioning.  I choose to install *buntu to /dev/hdb1 (format as EXT3) with /dev/hdb2 being used for swap.  I tell it to install GRUB to /dev/hdb (I've also tried /dev/hdb1).  Boot Magic recognizes the partition and shows it on the boot menu (I added it with the name "HERON").  When I choose Win2K from the boot menu it boots OK, but if I choose HERON, the screen goes black and nothing happens.

In Win2K Partition Magic gives an error ("Error #510 The version of the file system is not supported") when I select the properties of the EXT3 partition.

Does anyone have an idea what may be wrong.

PLEASE PLEASE do not suggest I put LILO or GRUB in the MBR of the first disk.  I'm looking for help in getting it working using Bootmagic on the first disk passing control to GRUB on the second disk.

---

### Post by cmbcne on 2008-05-05
Follow-up to original post:

I blew away both partitions on the second drive and used Partition Magic to re-create them.  I then used Ubuntu 8.04 ***alternative*** install and it worked.  During the install, I chose to place grub in /dev/sdb1, just as I did with the regular install disks.  This means the regular install did not put grub where I told it to.

From this I draw one of two conclusions:
(A) The original partition had somehow become damaged, or
(B) The regular install disks are incapable of properly placing grub if it's not on the first drive's MBR.

Since the partition has worked fine to install three different distros (Kubuntu, plus 2 non-*buntu) within the last two months, I'm not leaning towards the first explanation.  This leaves me to conclude that the regular install disks for Ubuntu, Kubuntu, and Xubuntu are flawed in their design -- hence the need to release an alternate disk in the first place.

To the *buntu design team: why not fix the problem on the main disks rather than doing a text based alternate?

Opinions??

---

