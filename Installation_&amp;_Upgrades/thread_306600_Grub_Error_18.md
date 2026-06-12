---
title: "Grub Error 18"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by dlugirapfr on 2006-11-25
At first I must say: sorry my englsih is bad ](*,) 

I have PenitumIII 800MHz and 30GB disk.
My disk has 5 partitions
1st with winxp (6GB) FAT32
2nd with smth (13GB) FAT32
3th with smth (5.5GB) FAT32
4th i make swap for linux (300MB)
5th ext3 for linux

I installed Ubuntu 6.06 and after reboot i cannot run any system cause i had grub error 18. I mount all partitons in linux instaltion and i alwayas have this same error. To run my winxp i had to do fdisk /mbr.
What I must do now to run Ubuntu ? When I had mandrake there was boot floppy but in Ubuntu i cannot find it.

Please help and thanks for any answers.

---

### Post by spd106 on 2006-11-25
It looks like you have a problem bios, check out this page for a possible solution [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by dlugirapfr on 2006-11-25
Now I must recover all data cause i make mistake in making partition :( Thanks for yor answer

---

### Post by lub0 on 2006-11-27
Hi spd106,  

I notice that howto you give the link to only really applies to ppl who have a fairly good working knowledge of linux..

when installing ubuntu 6.06 its not very flexible with choices on what bootloader you would like to use and so on..

I recently sent for the free shipping ubuntu cd, version 3.06 LTS..

I have a pretty old pc, 400Mhz P3.

Anyhoo up until yesterday i had slack 10 installed and working sweetly. I have 2 hard drives, 1 is a 6GB windows 2000 installation the other is a 40GB which i have 2 partitions on. This is the one which had the lilo on..

I have windows ME on 1 partition and slack 10 on the other.

I ran the live ubuntu cd, everthing went well until i actually tried to install it.

While installing at about 17% i get an error saying:

The test of the filesystem with FAT32 in partition #2 of IDE1 master (hda) Found uncorrected errors, go back or continue?

When i go back it just starts the installation again and i get the same error!! If i continue it finishes without anymore errors..

When i reboot i get the Grub error 18 message...? Now i searched the error 18 on google but the answers i got were about HD parameters and bios settings...? Whoosh as it went over my head : /

I cant boot the system at all unless i use the slackware boot floppy i had from before.. Then i have got no XWindow at all.. *sighs*

I finally noticed the exclamation mark beside the FAT32 partition while trying the manual disk setup utilty in ubuntu, after the umpteenth time of re-installing.. ubuntu cannot read this filesystem??

When i am logged in using the live cd i have X and it reads the FAT32file system fine.. Anyone any idea's???? Sorry for this being so long winded, but i am trying to supply as much info as possible

thx in advance for any help

lub0

---

### Post by spd106 on 2006-11-29
Linux has had FAT32 support for many years now, so ling that it is considered stable to use for read and write. The only problem is when it is used with a windows boot at the same time (dual boot) and the data becomes fragmented. This is usually solved by running the defragment tool from windows.

The Grub Error 18 message has to do with access to the hard drive. If you don't know much about the physical construction of hard drives i.e sectors, cylinders, tracks etc. Then I suggest that you have a look on-line for a beginners guide. The wikipedia probably has a good write-up.
Basically when the PC boots it is under the control of the BIOS, which is written by the motherboard manufacturer. If the BIOS doesn't support reading the area on the hard drive that grub points to then it fails and you get this message.
Often the easiest way around it is to create a small boot partition at the beginning of the drive.

---

