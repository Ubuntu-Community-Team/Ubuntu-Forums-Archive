---
title: "Partitioning, again :)"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by Pablo_Escobar on 2005-10-12
While waiting for Breezy release a big problem of mine came back to haunt me.

Last time I've installed Hoary (3 months back) I wanted to setup a seperate /home partition. 
In the installer I've made "/" and swap partition, but when I wanted to make "/home" it borked some error. I wonder. 
AFAIK You can only setup 4 primary partitions. Here is hom my SATA drive looks like:
These are my primary partitions:
sda1 - NTFS - (circa 6GB) WinXP (Yes, I still dual boot sometimes)
sda2 - EXT3 - "/" (circa 9 GB) Ubuntu
sda3 - SWAP - circa 1,2 GB

Then comes the extended partitions time:
sda5 - FAT32 - (circa 30GB)
sda6 - FAT32 - (circa 40GB)
sda7 - FAT32 - (circa 20GB)

My question is why can't I make another primary partition form my "/home" ?
Do I have to loose WinXP partition (I'm willing to do it :) ) to make a free slot for primary partition.

This problem has been tested for me on several installers (Fedora, Slackware, Ubuntu) and none of them could create it :(

Any thoughts would be appreciated :)

---

### Post by Alexander Kirillov on 2005-10-12
[QUOTE=Pablo_Escobar]While waiting for Breezy release a big problem of mine came back to haunt me.

Last time I've installed Hoary (3 months back) I wanted to setup a seperate /home partition. 
In the installer I've made "/" and swap partition, but when I wanted to make "/home" it borked some error. I wonder. 
AFAIK You can only setup 4 primary partitions. Here is hom my SATA drive looks like:
These are my primary partitions:
sda1 - NTFS - (circa 6GB) WinXP (Yes, I still dual boot sometimes)
sda2 - EXT3 - "/" (circa 9 GB) Ubuntu
sda3 - SWAP - circa 1,2 GB

Then comes the extended partitions time:
sda5 - FAT32 - (circa 30GB)
sda6 - FAT32 - (circa 40GB)
sda7 - FAT32 - (circa 20GB)

My question is why can't I make another primary partition form my "/home" ?
Do I have to loose WinXP partition (I'm willing to do it :) ) to make a free slot for primary partition.

This problem has been tested for me on several installers (Fedora, Slackware, Ubuntu) and none of them could create it :(

Any thoughts would be appreciated :)[/QUOTE]


This is not a problem with Linux. It is a general restriction of IBM PC disk partitioning scheem:  you can only have at most 4 primary partitions (because partition table must be no more than 64 bytes). See 
[http://en.wikipedia.org/wiki/Hard_disk_drive_partitioning](http://en.wikipedia.org/wiki/Hard_disk_drive_partitioning)
There is no way to have more than 4 primaries, whether you use Linux tools to create them, Windows, PartitionMagic....

But then, what is wrong with placing /home in an extended partition? I did it - and have no problems.

---

