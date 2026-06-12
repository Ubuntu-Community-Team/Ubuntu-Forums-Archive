---
title: "Grub loading error 2"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Corinne on 2010-03-16
Hi all, I hope somebody can help me with my installation of kubuntu 9.10. I am new at Ubuntu, I was a Suse user until now. I wanted to install kubuntu 9.10 this morning, there was no error message while installing it, but if I start up now I only get

Grub Stage 1.5
Grub loading please wait
Error 2

I found out so far that error 2 is an error with not detecting a disk, but I'm not sure how to solve that. I started the computer again with the live disk. Which information do you need to be able to help me? So far I was looking at the Grub version, its 1.97~beta4. If I try to look at 

sudo fdisk -l  

i get
Unable to seek on /dev/sda

Thanks for any help!

---

### Post by dstew on 2010-03-16
Did you have a previous Linux installation on that computer? The reason I ask is that the error message is from grub legacy, not grub 2 (which is version 1.97 ... yes, that is strange. Grub legacy was version 0.97). My guess is that there is a grub legacy boot loader in your hard disk MBR, and a stage 1.5 in the first track, which are "hard coded" to find the grub stage 2 in a particular block address on the disk. But, if you have a new Kubuntu installation there, that was set up to use grub 2, poor old grub legacy gets confused.

The fdisk error suggests there are disk errors of some kind, possibly a corrupted partition table, or file system. If the seek fails, it is unlikely that the usual file system analysis and restore program **fsck** will help.

What I would do in this case is boot a [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") and see if the disk can be seen, and if there are any partitions on it that are recognizable. if not, I would run the [testdisk]("http://www.howtoforge.com/data_recovery_with_testdisk") program from the Gparted Live CD command line, and see if I can repair the partition table.

If still no joy, I would get the disk manufacturer's diagnostic software and see if there are low-level format or hardware issues. For Seagate disks, there is a bootable [Seatools for DOS disk]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD") that I use a lot. (It's not really "for DOS", that is just the name they give it because it runs off of a bootable FreeDOS CD.)

Once you think the disk is OK, try installing again. I am not familiar with the Kubuntu installation, but I guess it is similar to Ubuntu. If so, unless you click on the Advanced tab in step 7, grub should go into the MBR and replace the old boot loader.

Also, check your Kubuntu Live CD for errors. I think that is an opening menu option.

---

### Post by peakrc on 2010-11-26
I found a simple solution to this problem on my machine...Disable "Quick Boot" in the BIOS. Hope this works for you as well as it did for me.

PeAK

---

