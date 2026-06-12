---
title: "no root file system is defined"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Switch92 on 2009-12-07
I'm trying to install Ubuntu 9.10 but I receive this message:

"no root file system is defined.  please correct this from the partitioniing menu."  This occurs in step 4 of 7 of the install process.  I have tried installing in both the "try Ubuntu" and "install Ubuntu now" options.  

I've been with Ubuntu for four years and have never had an issue with any of the previous versions.  I'm trying to install on a brand new Intel system.  I thought perhaps Ubuntu couldn't "see" the hard drive but it sees it in the partitioning manager (Gparted) and the disk manager (Palimpset).  I formatted the partition with ext2.  Why is it doing this?  Anyone have any ideas?

---

### Post by darkod on 2009-12-07
You might be trying to continue to step 5 without setting mount point for / and hence the message. When you say you created ext2 partition was it during step 4 or earlier when booted with the LiveCD? It is not enough to create partition in advance (in fact it's better not to create them in advance), but you have to tell the installer to use it and for what.
Any why ext2 and not ext4?

---

### Post by Switch92 on 2009-12-07
darkod,

first i had XP installed with some raw space open for Ubuntu to grab.  That didn't work because it didn't see the open space.  Then I created a partition beforehand (which I see you discouraged.)  I then just had the raw space there for Ubuntu didn't use.  So I then created the partition using ext2 because that was the default choice.

---

### Post by darkod on 2009-12-07
OK, but you need at least two partitions in fact, / and swap. Also, did you go into manual partitioning at step 4 and select mount point / for the created partition? I think that was the error, and when you try to continue it gives message no / defined.
Start the process again booting with the ubuntu cd, selecting Install Ubuntu. At step 4 select Manual Partitioning. It will show you your hdd and all the partitions and unallocated space if you have any.
Delete this ext2 partition that you created. It will turn into unallocated space. Click that space and create new logical partition, ext4 and select / for mount point. Calculate the size of this partition so that you have enough space left for swap in the unallocated space. swap should be the size of your ram or at least 2GB. After creating partition for / there should be unallocated space left for swap, so just create another logical partition in the whole remained space, select swap as filesystem and swap area as mount point.
After that the installer should continue without problems.

---

### Post by Switch92 on 2009-12-07
ok, HOW do i do that?  when i get to step 4 the only option that is available is "revert".  i would love to set the partition sizes manually but i never see an optioin to do so.

---

### Post by darkod on 2009-12-07
Don't you have the Specify Partitions Manually option like on the picture? (it's not selected in this picture, just shown for example)

---

### Post by Switch92 on 2009-12-07
not at all!  i wish i did...  look at my attachment

---

### Post by snowpine on 2009-12-07
Hi Switch, before you do anything else, I would recommend checking the integrity of the CD for errors. (This is an option on the first screen after you boot from the Live CD.)

Your screenshot is not the normal behavior for the installer; I would be worried that a malfunctioning partitioner could lead to all sorts of trouble. :(

---

### Post by Switch92 on 2009-12-07
dang it...  i did the MD5 checksum deal and it matched up...  i'll try what you suggest snowpine.

---

### Post by darkod on 2009-12-07
I've seen that. I didn't understand you previously. Traces of raid settings can do that. If you are not running raid, boot with the cd, Try Ubuntu option and in terminal do:
sudo apt-get remove dmraid

Afterwards reboot with the cd again and go with Install Ubuntu and if that was your problem you'll be fine.

---

### Post by Switch92 on 2009-12-07
ok...  so i had to do a few things to get this to work.  verify i had a good disk, check.  deleted the "raid" that the ubuntu disk was seeing, check.  deleted all partitions, and re-created.  from step 4, go back to step 3, then forward to step 4 so that the installer's partitioner can detect the file system's changes. apparently the installer doesn't sense dynamically that the partitions have been created (or altered).  so now i'm good to go.  thank you guys for your help.

---

### Post by darkod on 2009-12-08
> **Switch92 said:**
> ok...  so i had to do a few things to get this to work.  verify i had a good disk, check.  deleted the "raid" that the ubuntu disk was seeing, check.  deleted all partitions, and re-created.  from step 4, go back to step 3, then forward to step 4 so that the installer's partitioner can detect the file system's changes. apparently the installer doesn't sense dynamically that the partitions have been created (or altered).  so now i'm good to go.  thank you guys for your help.

Glad you got it sorted. Just for the record, when you say the partitioner can't detect system change. I'm even surprised it allowed you to do it that way. The installer is designed on purpose so that you can abort the process up until clicking Install in step 7. If you click Quit in any of the steps, it's supposed to leave your system as it was, with no change.
So going back-forward in the install steps shouldn't have even allowed you to change partitions. :) All the partition changes should be executed only after you click Install in step 7.
The easiest way for that is booting the cd with Try Ubuntu and using Gparted (in System-Administration). That's very powerful partition manager. But even there, all operation you make are just created as scheduled in the bottom part of the screen. Until you click the large green tick mark in the menu towards the top of the screen, nothing is executed. This is sort of protection to prevent you with one wrong click to delete a wrong partition and lose your data.
That's why sometimes it may look like it's not sensing the changes. It's actually a great tool. :)

---

### Post by psy^ on 2010-06-18
> **darkod said:**
> I've seen that. I didn't understand you previously. Traces of raid settings can do that. If you are not running raid, boot with the cd, Try Ubuntu option and in terminal do:
sudo apt-get remove dmraid

Afterwards reboot with the cd again and go with Install Ubuntu and if that was your problem you'll be fine.

^after booting from cd, this fixed my 'no root file system' error when trying to install, much appreciated.

---

