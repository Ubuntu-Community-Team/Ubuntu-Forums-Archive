---
title: "Full Install on USB pendrive Help"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by byoumans on 2007-08-27
I'm working in an environment temporarily that will not let me have net access using my company XP laptop, but will let me connect if I boot to Linux. I've been using a LiveCD + persistence with USB then went to LiveUSB/persistence for a couple days, but it has been flaky. First it stopped recognizing the FAT32 partition on sdb1 I was using to move files between WindowsXP and the Linux environment; then it somehow corrupted the LiveUSB install on sdb2 and wouldn't let me log on with my created user account.

I've got a 4 GB USB pendrive and really only want Firefox, networking, and OpenOffice.

Is there a way to do a "real" install on the USB stick, as in, not a Live install? 

I tried just now to boot up using a LiveCD, partitioned my USB stick as follows:

/dev/sdb1: 500MB FAT32 for file transfer and storage.
/dev/sdb2: 2.5GB ext2 for / partition
/dev/sdb3: 1GB swap partition

Then clicked install from the LiveCD desktop. Went through, things looked ok, then on step 5 when it was going to install GRUB or something on hd1 I got nervous. I can't let the install touch my laptop harddrive on sda at all; it's encrypted per work rules, etc, and I don't want the Ubuntu USB install touch it at all. 

IAm I doing this correctly? Is it going to do anything on sda at all? Thanks for any help.

---

### Post by MQMike on 2007-08-27
I’ve not done it, but have been interested and have noticed various references on it.
A google would turn up what there is.  The first link here is known to be quite reputable (expert).  I haven't looked much at the second one yet.
[http://ubuntuforums.org/showthread.php?t=476302](http://ubuntuforums.org/showthread.php?t=476302)
[http://lifehacker.com/software/linux/boot-linux-from-a-flash-drive-225652.php](http://lifehacker.com/software/linux/boot-linux-from-a-flash-drive-225652.php)

About GRUB, if it's the bootloader used, you want to make sure it is specified to the MBR of the UFD.  And I would start by partitioning/formatting the UFD using GParetd first.
Maybe the links will point the way.  I also need to try this here soon as time permits.

---

### Post by wislon on 2007-08-27
I had fantastic success with the first link there given by MQMike. The only thing I have to do when I boot off the flash disk is to remember to add the 'persistent' parameter to the command line at boot time when it asks you how you want to boot (I think I just use "live persistent").

Good luck with it! :)

---

### Post by byoumans on 2007-08-27
Well thanks for the replies, but those links are to installing the LiveCD on a USB, so you have a LiveUSB. I've tried that, as I explained in my first post, and it was flaky.,

What I would like to do is an actual, full install on my USB flashdrive as if it were a hard drive. Not a Live install. I've done the Live install about 6 different times in the last week, and every time it has worked fine the first 1 or 2 times I boot to it, then it stops working and flakes out after that, and I have to boot to LiveCD and do it over. Except I'm tired of doing it over and want a better solution :)

---

### Post by Licurgo on 2007-08-28
Byoumans:
I've had the same problem.
Why are you interested in a a full install?
If you make a full install you can only work in a single computer (hardware configuration)
So if you install a live CD and persistent you can use it in every computer you want to and have your information in your hand.
Have you tried another way instead? Have you tried _[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-us](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-us)_
I hope this work for you as is working for me
:guitar:

---

