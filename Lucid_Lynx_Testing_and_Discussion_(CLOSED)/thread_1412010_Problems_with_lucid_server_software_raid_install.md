---
title: "Problems with lucid server software raid install"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2010-02-20
I was trying a software raid1 install of lucid server on a test machine, it kept on failing at grub installation. I thought is was a hardware problem, but after experimenting in virtual machines this does not seem to be the case.

As far as I can tell I did the partitioning properly (I attached a screen shot, just to make sure), but grub installation is letting the install fail.

I noticed a couple of bug reports on this issue:
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/485604](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/485604)
[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/506670](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/506670)

In the comments in these bug reports a BIOS boot partition is being mentioned:
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

It is all quite confusing to me; 
*So is this a bug in the installer (that is going to be fixed)?
*Should I use a BIOS boot partition as a workaround or as a permanent solution?
*Anybody got experience with this BIOS boot partition (should it be on one drive or both when using raid1, ignore them during installation etc.)?
*Maybe a different (better) solution altogether?

Any help much appreciated...

---

### Post by whoop on 2010-02-21
Reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/525425)

---

### Post by nanog on 2010-03-03
A useful how to: [http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)



Raid1 needs a setup like this:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9f16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91085   731640231   fd  Linux raid autodetect
/dev/sda2           91086       91201      931770   fd  Linux raid autodetect

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db8e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91085   731640231   fd  Linux raid autodetect
/dev/sdb2           91086       91201      931770   fd  Linux raid autodetect

Disk /dev/md0: 749.1 GB, 749199491072 bytes
2 heads, 4 sectors/track, 182910032 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 954 MB, 954007552 bytes
2 heads, 4 sectors/track, 232912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aa0e8fb

---

### Post by whoop on 2010-03-10
fresh install still fails (server and alternate):
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425)
upgrading from 9.10 to 10.04 also needs some work:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/536747](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/536747)

---

