---
title: "GRUB Still not working after boot repair"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by allen.coley on 2014-01-13
Basic problem:
Flashing cursor on boot

What got me here:
Installed Ubuntu Server 12.04 to a USB Thumbdrive
Configured bunch of stuff for media server
Installed new 4 TB Drive
Used fdisk (cause I'm a dummy)
Moved all my old media from a 1TB drive to the 4TB
Started to move all my old media from a 2TB drive but the 4TB ran out of space
Found out about GPT
Jumped through hoops and got the 4TB to GPT and expanded to the whole drive. No data loss (woo hoo)
everything was horrible slow, blamed USB drive install
Used Clonezilla to backup the USB drive and restore to a 1 TB drive
Repartitioned 1TB drive to have 100GB at the beginning for the root and 20GB at the end for SWAP (going to put the other partitions in later, I deleted them because I'm having boot trouble and figured get them out of the way)
I can mount the sda1 and see all of my data (root, grub, opt, etc, all that jazz)
Won't boot.
Ran boot-repair live
Says it installed and it is good to go
Reboot, flashing cursor.
Cried a little
Tried it again using advanced options to purge the old
same
Cried a little more
Tried boot-repair with just recommended
tried again
same
cried more
gave up
came here

Here is the paste from boot repair
[http://paste.ubuntu.com/6745878/](http://paste.ubuntu.com/6745878/)

---

### Post by allen.coley on 2014-01-13
I'm moving /boot to it's own partition. Will post results

---

### Post by oldfred on 2014-01-13
I would not use ext3, but use ext4.

You need a bios_grub partition for grub to install correctly. But that is a 1 or 2MB unformatted partition with the bios_grub flag. You seem to have sdb1 flagged as bios_grub but it is formatted, so not usable for grub. And then you have another, sdb6. Only one per hard drive. Also that partition is not aligned. You need all partition starts to be divisible by 8.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

