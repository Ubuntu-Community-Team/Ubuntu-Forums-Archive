---
title: "&quot;dev/sda1&quot; marked as boot and HP menu shows before GRUB. Safe to delete anyway?"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by tadness on 2012-12-10
Hi, all. Basically, I've been using Ubuntu exclusively for around 2 years now, but I want to regain most of my hard drive space after realizing Windows Vista took up so much. I'm a fairly novice user, so I still get a bit nervous using the terminal and stuff.

I have an old HP Pavilion DV7 laptop (technically it's a desktop now) which I installed Ubuntu on via a LiveCD, and upon booting it shows the HP boot options, with the option to change BIOS settings, etc, *then* it shows the regular GRUB menu.

Here is the output of sudo fdisk -l:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc83795b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   496419528   248209733    7  HPFS/NTFS/exFAT
/dev/sda2       598075392   625135615    13530112    7  HPFS/NTFS/exFAT
/dev/sda3       496420862   598075391    50827265    5  Extended
/dev/sda5       496420864   593825791    48702464   83  Linux
/dev/sda6       593827840   598075391     2123776   82  Linux swap / Solaris
```From what I can figure, sda1 is Vista and sda2 is the Windows recovery partition.

My main question is, seeing as how /dev/sda1 is set with the boot flag, is it still safe to just use a LiveCD version of gparted and delete it, or would that screw up my whole boot process? The fact that the HP menu shows up first before GRUB, and that little asterisk under sda1 are the only things leaving me _extremely_ nervous about just deleting it outright.

---

### Post by Wim Sturkenboom on 2012-12-11
You can find plenty of information about the boot flag and the fact that Linux does not need it. e.g. [http://ubuntuforums.org/showthread.php?t=1850805](http://ubuntuforums.org/showthread.php?t=1850805) Personally I would not hesitate to remove that partition.

You don't need a live CD to delete that partition (as long as it's not mounted). You don't even have to delete it. With fdisk, change the type to linux and next format it with mkfs.

Next you decide how to use it; easiest is probably to mount it somewhere in your current home directory. Alternatively you can make it your home partition which is a little more work.

---

