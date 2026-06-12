---
title: "Partition help"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by flummoxed on 2006-03-11
Alright, here's the deal. I was running ubuntu breezy 5.10 on my SATA 80gb hdd. I want to try dapper, so I decided to burn an .ISO and try to resize the breezy partition to 40GB, and use the other 40 for dapper (approximately). So I resized it, then did what I thought was installing dapper to the new partition. It was going fine, until it gave me a sudden error during "select and install software". Now breezy won't boot, and dapper isn't installed. I didn't think to look at which partition was my breezy partition before I changed it, but I'm pretty sure it's number 5. Here's waht the partion table looks like:

#1 primary 255.0mb ext3 /media/sda1
#5 logical 39.9GB lvm
#6 logical 1.7 swap
#3 primary 38.2GB ext3 /media/sda3

The swap file and the 38.2 ext3 partition were created when I resized the breezy partition, then sit it to use the "largest continuous free space" for a new partition. Unfortunately, I have no idea what all the different file system types mean (ext3? what the?). I know what a swap partition is, but I never created one when I isntalled breezy, I didn't think it was necessary.

So now my question is: what do I do? If I try to write the changes to the partitions again it tells me I have no root file system specified or something liek that. Is my breezy partition gone, along with all my data? I backed up what I needed, so it's not a real worry, it's just annoying.

---

### Post by Lux Perpetua on 2006-03-11
> #1 primary 255.0mb ext3 /media/sda1
**#5 logical 39.9GB lvm**
#6 logical 1.7 swap
#3 primary 38.2GB ext3 /media/sda3You seem to have Breezy on an LVM partition. Was partition #1 mounted as /boot in your Breezy system or something? What happens if you try to boot into Breezy?

By the way, ext3 is the file system format that Linux uses. It just refers to the way your files and directories are organized on your physical disk. 

LVM is "logical volume management," and I'm a little confused as to how have acquired it if you don't know what it is. :-)

---

