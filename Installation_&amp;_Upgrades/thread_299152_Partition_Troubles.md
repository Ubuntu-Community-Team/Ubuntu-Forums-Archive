---
title: "Partition Troubles"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by rossjman1 on 2006-11-13
I ordered the Ubuntu 6.06 LTS cds, and they came in the mail today, so now I'm trying to install it. When I used Breezy (on my older computer) I would just format the entire drive and run Linux only. I have duel booted DamnSmallLinux, Dos, and Windows 95 on a different computer, but I am having troubles duel booting WinXP and 6.06. So here's my situation. I booted the disk up, everything works fine (except for small resolution, but I can fix that later), but the installer won't let me set up the partions the way I want. Here are the partitions already on my drive:
/dev/sda1 (~52 GB) : Windows XP and programs and documents
/dev/sda2 (~4GB) : Windows recovery partition set up by the manufacturer

Here's what I want the drive to look likeL
/dev/sda1 (~36 GB) : Windows XP and programs
/dev/sda2 (~4 GB) : Windows recovery partition
New Partition 1 (~8 GB) : Ubuntu and programs
New Partition 2 (256 MB) : Linux-swap
Extended Partition with Logical (~6 GB) : Music and documents

Not too much to ask right? When I get to the last partition (it could be any of the new ones) I get this error:

"It is not possible to create more than 4 primary partitions

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions."

Are there any suggestions as to how to partition this, or should I just load up Knoppix and use GParted to partition the drive, then install Ubuntu? Thanks in advance.

---

### Post by rbprogrammer on 2006-11-13
create an extended partition and include everything Linux related on the Linux extended partition.  i don't know how much you know about partitions, i don't know much either, but i know an extended partition can include many more partitions.

try this:
[http://linux.about.com/cs/linux101/g/Extended_partit.htm](http://linux.about.com/cs/linux101/g/Extended_partit.htm)

or even do a google search for partitions, extended partitions, logical partitions, etc...

---

### Post by yabbadabbadont on 2006-11-13
The extended partition is itself a primary partition and must be included in the four primary partition limit.  If you do that, it looks like you are trying to configure five primary partitions.  Put your root and swap partitions inside the extended.  They will work perfectly fine from there.

Edit: Too slow... :D

---

### Post by rossjman1 on 2006-11-13
Hmm, I thought that the linux-swap had to be a primary partition. Anyways, I tried it but got an error when trying to create the first partition, so I'm going to try one more time.

---

### Post by rossjman1 on 2006-11-13
Error again. It's not worth it to risk my existing Windows setup and recovery partition. Thanks for your help anyway, though.

---

