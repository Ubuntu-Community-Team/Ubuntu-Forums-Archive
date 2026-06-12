---
title: "Dual Boot problem Windows NTOSKRNL not found"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by shrimphead on 2007-06-27
Hi all hope you can help me with a particularly sticky problem.

I'm trying to set up a dual boot system of Ubuntu 7.04 and Windows XP on a machine at home. The specs are:

Core 2 duo E6600
MSI 975X Powerup edition Mobo.
250Gb Maxtor SATA HDD

The drive is partitioned as follows:

/dev/sda1   138Gb Windows (NTFS)
/dev/sda2   100Gb Ubuntu (ext3)
/dev/sda3   4Gb swap

There is a separate data drive that is also on a 250Gb Maxtor but this has been removed for the purposes of installation.

The problem is this:
After installing the OS's Windows refuses to boot saying NTOSKRNL.EXE cannot be found. Ubuntu boots normally.

I have tried various fixes to get this to work. Firstly I have tried doing Boofcfg /rebuild from the windows recovery console. Then I tried copying over a new kernel from the windows CD to no avail. Strangely this drive works as normal when I use it in my Athlon 64 based PC, both operating systems boot fine.

Also if I run fixmbr from the windows recovery console windows boots fine. however I then cannot boot ubuntu.

I am at a loss as to why this setup works in one pc but refuses to boot windows in another and it's driving me bats :lol:

Please help as my girlfriend *really* needs this PC for her work!

thanks in advance

---

### Post by shrimphead on 2007-06-28
Quick update:

the Super grub disk can boot both partitions, but I still have no idea how to fix the mbr of the drive.

---

