---
title: "Ubuntu Live-CD *can* see HDD, but installer cannot!"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by ediblespread on 2010-05-27
Hi there,

I'm currently trying to install Ubuntu 10.04 on a 320GB Seagate (I think) HDD. I'm following the guide here - [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902) - as I have another HDD with Windows 7 on it and want to dual-boot off of both HDDs.

However, I'm having real problems with installing Ubuntu. At the moment, the 320GB disk has two partitions. On is most of the disk (~90%), Windows XP. The other is an old Ubuntu, 8.04 or thereabouts. When I pop in the Ubuntu 10.04 disk, it attempts to install, then quickly gives me a "The installer has encountered an unrecoverable error" message and sends me to a Live-CD session. 

In the Live-CD session, I can tell that it can see my 320GB disk, as it appears in the list of 'places' and I can access it. However, when I run the installer from inside the Live Session, it gets as far as the partitioning/formatting step (step 4?) and then it just shows me a blank list of choices - it does not list either my hard-drive or any of my partitions!

(Note that the Windows 7 HDD is not plugged in atm, as specified by the guide I'm following.)

Both disks are SATA disks, the one plugged in at the moment is (as far as I know) a Seagate disk. I can't remember the motherboard off of the top of my head, but can find out if required. Processor is a Core 2 Duo, ~2.44GHz, and the graphics card is a NVidia 8800GT.

Any help would be much appreciated!

EDIT: Just to note, I did do a md5 checksum on the image when I dl'ed it, and it was correct, but I haven't checked that the disk was properly burned. I will do that now, but I doubt that this is the problem, since it isn't corrupted or anything, just... not working. XD.

---

### Post by darkod on 2010-05-27
This usually happens if the disk was used in raid earlier and has raid metadata settings remains. It might have them even if you are not aware.

From live mode:

sudo dmraid -r -E /dev/sda

If that asks you to remove some settings, that was your problem. Do it, and it should work fine.

And just a note, in my personal opinion unplugging another hdd can create some smaller issues sometimes. Most times it would work out OK, but depending on specific setup grub might get confused which disk is hd0 and which hd1 later when you plug the other one back. As long as you are careful your other disk is safe. When installing an OS it needs to know you have another hdd in the system, IMHO.

---

### Post by ediblespread on 2010-05-27
Thanks darkod, that worked perfectly. Installer can now see my hard-disk, and seems to be proceeding happily. Thanks!

PS: What is the correct way to mark this solved? When I first posted the thread it gave the option to add a prefix, but I can't seem to see that option when editing my first post now. Should I just type the prefix into the subject myself?

---

### Post by darkod on 2010-05-27
> **ediblespread said:**
> Thanks darkod, that worked perfectly. Installer can now see my hard-disk, and seems to be proceeding happily. Thanks!

-Stephen

PS: What is the correct way to mark this solved? When I first posted the thread it gave the option to add a prefix, but I can't seem to see that option when editing my first post now. Should I just type the prefix into the subject myself?

Above the first post, in Thread Tools. Because it's your thread, only you have that option in the Thread Tools menu.

---

### Post by ediblespread on 2010-05-27
Ah, yes, got it. Thanks again, and have a good day!

---

