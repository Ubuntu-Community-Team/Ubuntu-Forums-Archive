---
title: "Server install partition questions"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by emueyes on 2018-04-28
I have an install of Mint 17.1 with Ubuntu 14.04.3 LTS and wish to upgrade it to Ubuntu Server. I have several questions, I'll just ask them, I know they probably need separate threads but the answers are hopefully one liners.


The hardware is an Asrock Q1900DC-ITX with a 1T disk. It's to be used as a server for UPnP. I may well add much more storage starting with a spare 4T HDD.


The 1T disk is currently setup like this


Model: ATA WDC WD10JFCX-68N (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  100GB   100GB   primary   ext4            boot
 3      100GB   992GB   892GB   primary   ext4
 2      992GB   1000GB  8276MB  extended
 5      992GB   1000GB  8276MB  logical   linux-swap(v1)


/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sda3 on /AV type ext4 (rw) 


all my data is on /AV


My questions:


Will the data on /dev/sda3 be affected by installing Ubuntu onto /dev/sda1 if I choose to manually set up partitions?


The system currently uses BIOS booting, will the disk be affected if I change it to UEFI?


I don't know why the swap partition is set up like that. Again, will the data on /dev/sda3 be affected if I remove that extended partition and create another primary partition (assuming I stay with BIOS booting) ?


I was going to use 16.04 LTS but now see that Ubuntu Server 18.04 LTS is available, should I use that instead?


I'm trying to avoid it but might I be better off just backing up my data and starting fresh?


Thanks

---

