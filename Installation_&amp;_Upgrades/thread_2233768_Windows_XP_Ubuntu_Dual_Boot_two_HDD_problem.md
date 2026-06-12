---
title: "Windows XP/ Ubuntu Dual Boot two HDD problem"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by FenTigger on 2014-07-10
Hi,

I've installed Ubuntu 14.04 on an old PC I have laying around. It has 2 hard drives, and for some reason I can't remember, Windows XP SP3 named the bigger 250Gb drive, which is the boot drive D:\ while the smaller 40 Gb drive is C:\. This never presented an issue previously. I've installed Ubuntu and it only gave me the choice of instaling it on the smaller drive which is /dev/sda and was partitioned in two, one NFTS and one ext4 partion. Now when I try to boot into Windows at startup, it can't find Windows as it seems to point at /dev/sda.

Is there any way to edit the dual boot program (Grub?) to correctly point it at /dev/sdb for WinXP?

Thanks, this is my first experience with Linux so be gentle :) any help gratefully received.

---

### Post by Bashing-om on 2014-07-10
FenTigger; Hi ! Welcome to the forum .

OH boy, we do see this a lot, in that Window's nomenclature of a "partition" on a hard disk is drive\A:, drive\B: or drive\D:. When in reality these are but partitions on a single hard disk.
Whereas ubuntu designates a drive (1st) as 'sda' (Serial Device a) and a partition on the hard disk, 'sda' as a number as in sda1, sda3, sda8 ( 1st, 3rd, 8th partition)
'sdb' would be the 2nd hard drive, 'sdc' the 3rd.

So let's make sure we are on the same page and speaking as ubuntu understands the hard disk.
Boot up the liveDVD to a terminal:
Post back the output - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And perhaps get prepared to invoke data recovery procedures.

But, let's look
[INDENT][INDENT][INDENT]before we leap
[/INDENT][/INDENT][/INDENT]

---

