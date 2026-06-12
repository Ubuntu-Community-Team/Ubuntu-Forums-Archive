---
title: "Ubuntu and Windows XP Partitions"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by arne-boettger on 2014-01-11
Hello,

at the moment i have an Ubuntu System and I want to use it further but also I need Windows XP and not with VirtualBox.
So I am thinking about installing both on different partitions. This means I would have to install Windows fist. 
I have 200gb of data I need to save, but no acces to a external disk. At the moment i have two Partitions: 
1. with Ubuntu with like 30gb, 2. with home files, with 287gb.
Is there any way, I could install Windows and Ubuntu with keeping my files? - like making a third  partition from the rest space of the second partition?

Or is there a way op installing Windows without VirtualBox on a third Partition made from my second with keeping my Ubuntu system? Maybe that i can not use a Dual Boot but maybe an other way using Windows with Ubuntu without VirtualBox?

Greetings
Arne Böttger

---

### Post by oldfred on 2014-01-11
While Windows likes to be first partition, it only has to have a primary partition to boot from or sda1 thru sda4. Windows sometimes corrupts extended partition if its primary partition is after the extended partition so best to keep it before that on drive.
Windows will install its boot loader, you you must have an Ubuntu live installer to reinstall grub.

Systems seem to know if you have backups. If you have not backed up it has you make mistakes and erases data, But if you have backed up then it works without issue. (not really but seems that way). :)

Post current partition table.
sudo parted -l

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

XP expires in April, so I would not expect to use it after that for anything on Internet.

---

### Post by TheFu on 2014-01-11
Sure, you can shrink partitions, make room for Ubuntu, create 2 new partitons (/ and swap), the install Ubuntu into those. During the install select "do something else" at the partitioning screen.

However, I would be remiss if I didn't clearly state that partitioning work is risky and that before starting this a 100% backup is required. You can do this stuff without a backup, but when something bad happens, it is all your fault.

**Nothing can replace good backups that can actually be restored.**

BTW, if you have lots of data and it needs to be shared between Linux and Windows, create a "data" partition with NTFS and use that.  Don't put any programs or anything sensitive there, just data.

Go for it, but after you have backups to different physical storage.

---

### Post by arne-boettger on 2014-01-12
Ok, thanks for Your Advices. I will try to get Laptops from Friends to temporarly store my files.
After that I would make 3 Partitions: 1 small for Ubunt, 1 not so small for XP, 1 big with as NTFS. 
Could I use the big NTFS partition as a /home partition as well, and still use it to store files from XP?

---

### Post by TheFu on 2014-01-12
> **arne-boettger said:**
> Could I use the big NTFS partition as a /home partition as well, and still use it to store files from XP?

Nope. The "HOME" needs to be on a Linux formatted partition.  Permissions, ownership, groups and all the other bits are critical. NTFS doesn't support everything needed (or Linux won't use it).

Put media files on the NTFS, not HOME, not settings. Things like music, videos, are best on NTFS if dual boot is your intent.  If network sharing is the plan, then use EXT4 and setup Samba for other systems to access via CIFS over the network.

---

