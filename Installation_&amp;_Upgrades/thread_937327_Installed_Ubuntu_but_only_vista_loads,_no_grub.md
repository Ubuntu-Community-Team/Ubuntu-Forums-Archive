---
title: "Installed Ubuntu but only vista loads, no grub?"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by bebopcola on 2008-10-03
SO I am trying to have a dual boot setup I already had vista installed, on my main 750 gig hard drive I left around 160 gigs unpartitioned and I had Ubuntu use that unused space. I also have another 120 gig hard drive with windows files only.

Anyways the install seemed to go smoothly and then I restarted and boom vista starts loading no grub boot loader. I am pretty sure Ubuntu installed grub

So I launched from the live cd did a sudo fdisk -l

here is my output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd207d207

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14024   112640000    7  HPFS/NTFS
/dev/sda2           14024       19457    43646976    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f6b9b85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       70116   563200000    7  HPFS/NTFS
/dev/sdb2           70117       91201   169365262+   5  Extended
/dev/sdb5           70117       90340   162449248+  83  Linux
/dev/sdb6           90341       91201     6915951   82  Linux swap / Solaris

I also tried something from a guide to reinstall grub on  different hard drive

I typed


sudo grub
root (hd0,0)  *** on a side note is there a guide on Linux hard drive naming vs grub hard drive naming? ***
setup (hdo)   *** Error 17: Cannot mount selected partition




I hope one day all this will make perfect since to me, right now i am very lost.


Any help is greatly appreciated!!!

---

### Post by meierfra. on 2008-10-03
Try switching the boot order in the bios.

---

### Post by nitecon on 2008-10-03
I have had this happen to me before, when you did the initial install did you change anything in the advanced settings?  For instance if you changed the bootloader location to be anything else than /dev/sda then it will load the regular vista boot loader since vista installs to the mbr.

If you did install it to /dev/sda5 or /dev/sda6 etc then you will not be able to dual boot since the vista loader takes precedence at /dev/sda.  Easiest way to fix this is to just redo an install of ubuntu and when you get to the advanced options section make sure grub is to be installed on /dev/sda.

The other option is to manually configure grub if you can't spend the time to redo an installation.

---

### Post by nitecon on 2008-10-03
meierfra is right though you can just change your boot drive in the bios.

---

### Post by bebopcola on 2008-10-03
Thank you for the suggestions. I think I will try a fresh install and make sure grub is installed in the right location.

I am pretty sure my hard drive boot order was ok

when I last installed ubuntu I noticed it did not detect the (longhorn) mbr ... it should see it, right?

---

### Post by meierfra. on 2008-10-03
Please try switching the boot order. It probably fixes your problem in no time.

---

### Post by bebopcola on 2008-10-03
This is the guide I followed when installing ubuntu

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by bebopcola on 2008-10-03
O man I feel silly I changed the hdd boot order and bam! grub was there I selected ubuntu and it started up without any problems.

Thank you everyone for helping out a Linux nub

---

