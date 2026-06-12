---
title: "partitions not recognised"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by markymark on 2006-10-28
I would like to install ubuntu to my machine along side other OSs and have a linux partition ready to use. Unfortuntely, the installer does not recognise my partitions. It thinks there are no partitions at all on the disk. I think this may be a parted problem because gparted live cd has a similar problem and so does debian. 

My partitions were written by cfdisk, when I installed zenwalk some time ago. Other installers (mandrake, slackware, zenwalk etc.) seem to recognise the partitions.
With cfdisk the partitions are given as...

      cfdisk 2.12r

                              Disk Drive: /dev/hda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   NTFS             [^A]            10734.00
    hda5                    Logical   NTFS             [^E]            45370.65
    hda10                   Logical   Linux ext3                        7057.30
    hda6        Boot        Logical   Linux ext3                        6292.34
    hda7                    Logical   Linux swap                        1044.62
    hda8                    Logical   Linux ext3                        4186.67
    hda3                    Primary   W95 FAT32 (LBA)                    205.64
    hda9                    Logical   Linux ext3                        5132.58

I wanted to use the free partition hda10 for ubuntu.

Is there a way of getting ubuntu onto my machine, without using 
the installer. e.g. copying a basic system and using the net to install
the rest?
:-?

---

### Post by ribena on 2006-10-28
Hi Mark,

Having similar problems myself - see here: [http://ubuntuforums.org/showthread.php?p=1676755](http://ubuntuforums.org/showthread.php?p=1676755)

Anyone got any ideas?

Rob

---

### Post by govedarov on 2006-10-28
[http://ubuntuforums.org/showthread.php?t=286854](http://ubuntuforums.org/showthread.php?t=286854)

similiar problem here as well, setup finds no devices.

---

### Post by markymark on 2006-11-01
this was solved, see
[http://ubuntuforums.org/showthread.php?p=1676755](http://ubuntuforums.org/showthread.php?p=1676755)

---

### Post by noranthon on 2006-11-25
The so-called solution involves using Knoppix.

I have filed [a bug report]("https://launchpad.net/distros/ubuntu/+bug/71894").

---

