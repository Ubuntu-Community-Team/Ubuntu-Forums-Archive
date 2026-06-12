---
title: "Partitioning problems, Live USB 11.10"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by ineededausername on 2012-01-17
While attempting to install Ubuntu from a USB, I had several problems with partitioning.

Ubuntu installer: something like "Error while creating partition" (When creating /dev/sda6)
Gparted: Input/output error while determining whether /dev/sda6 is mounted. (After deleting /dev/sda6, then creating /dev/sda6)
Gparted: Input/output error while determining whether /dev/sda2 is mounted. (When I try to resize an NTFS partition)

Also, the disk itself has no problems: 			 				The screen rotation button on the panel does not work by default,  although the screen rotation in the Display Settings widget works well  enough. (I added the widget to the panel.) However, when the screen is  rotated, the pen input seems to be rotated as well (and as I said the  finger input is not right). I have hopes that these have already been  resolved but haven't tried yet. 			 		

ubuntu@ubuntu:~$ sudo badblocks -v /dev/sda
Checking blocks 0 to 156290903
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

What am I doing wrong?

edit: Note that the live CD is not an option, since I do not have an optical drive.

---

