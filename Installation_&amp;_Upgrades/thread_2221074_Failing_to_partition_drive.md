---
title: "Failing to partition drive"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Jay_Robinson on 2014-04-30
I am attempting to install Lubuntu 64-bit 14.04 to a new Western Digital WD10EZEX on a Biostar MCP6PB M2+ w/AMD Sempron. I am getting a read error during installation on \dev\sda. I've tried manually creating the partitions, and can't even create the partition table. I booted to gparted and it got a read error trying to create the table as well.


The system (minus the new drive) has been running XP for ages. From XP (running off an older drive), I was able to create and slow format a primary NTFS partition on the new drive. This did not change the behavior described above.


I have used two different SATA cables and motherboard ports, including the ones belonging to the old drive. Just to make sure I don't have a bad install, I tried two different Lubuntu install discs, burned from two separately-downloaded iso's, and in two different CD drives, before also trying gparted.


I'm at a complete loss - did Amazon ship me a bad drive? Is there something about the drive that Lubuntu doesn't like? Is there something about the drive controller or other system hardware that Lubuntu doesn't like? Do I need to do something special about the drive partitioning for this drive? Any advice is appreciated.


J

---

### Post by sudodus on 2014-04-30
Welcome to the Ubuntu Forums :-)

Please specify some more details about the computer

Computer: brand name and model (or motherboard)
CPU (sempron model and frequency MHz)
RAM (size)
Graphics chip/card model
Wifi chip/card

And it will be easier to help.

Also please describe your problem in detail.

How far does it work?
 What installer are you trying: the desktop installer (with a graphical interface) or the alternate installer with a text menu interface?
Did you check the iso file(s) with md5sum. See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Are you trying to make a dual boot installation, or do you intend to let Lubuntu use the whole drive?

There are many things to find out, before we know what is the problem.

---

