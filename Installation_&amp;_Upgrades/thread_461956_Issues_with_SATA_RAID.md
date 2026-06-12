---
title: "Issues with SATA RAID"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by gilbertr on 2007-06-02
I have been struggling with this for a while now and need some help...

I am installing Dapper LTS on the following system :

M/B : D946GZis
CPU : Pentium D915 2.8GHz
RAM : 1GB
ODD : IDE DVD-ROM
HDD : 2 x S-ATA 80GB
distri : Dapper 6.06.1 LTS Server 64-bit (have also tried 32bit)

I want to use software RAID1 on the 2 SATA drives and ideally with LVM.

The basic scenario is that first of all, I cannot get Dapper to boot at all unless I use the pci=nommconf parameter.  In itself not a major issue but as this is a LTS release, would like to see the issue resolved.

Secondly, I create 2 RAID1 arrays MD0 and MD1.
MD0 I will use as my boot partition and is 300MB in size.
MD1 I will use as physical drive for my LVM.

I am able to create the MD0 set and no problem so far.
However, when I generate MD1, the system creates the RAID array but my HDD LED suddenly lights constantly. (At this point no mention of LVM yet !)

If I choose to ignore the fact that my hdd led is constantly on while the hdd's are idle and continue to set up LVM, I receive the following error :

"Error informing the kernel about modifications to partition /dev/md/1p1  -- invalid argument. this means Linux won't know about any changes you made to /dev/md/1p1 ntil you reboot-- so you shouldn't mount it it or use it in any way before rebooting."

If I choose to ignore the error, I seem to be able to continue the installation.

However,

The combination of these three issues (nommconf, hdd led always on and LVM error) make me very concerned about the stability of the system and instability I cannot afford...

Going to another distribution is not much of a solution as I would like to stick with LTS because of the supposed support....
I have already tried feisty where I don't have the PCI issue but the hdd led issue appears there also, so I haven't tried any further...

Is there anyone who can help me ? Thanks.

---

### Post by gilbertr on 2007-06-02
Small update,

The fact that the HDD leds don't light up when creating the first RAID array, doesn't seem to have anything to do with the fact that it is created first.

It seems to be related to the array size.

If the first array created is anything larger, like 1GB or 80GB, then the same symptoms occur.

HELP !!

---

