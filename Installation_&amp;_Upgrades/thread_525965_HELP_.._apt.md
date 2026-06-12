---
title: "HELP .. apt"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by Kareem-saed on 2007-08-14
Hey .. I'm kinda new to ubuntu and I'd really really really appreciate helping me in this ... Here's the problem:
I have a 80 GB hard disk 'n a Dell Inspiron 6000 with XP and Ubuntu 7.04 installed .. The hard was partitioned as follows:
20 GB for Windows ... NTFS
50 GB for my data ... NTFS
5 GB for UBUNTU ... EXT3 !!!! , Kinda small that's the lesson I've learned now :( 

Anyway, I was installing some packages over ubuntu and then I noticed that the 5GB partition is full, so I intended to resize the 50GB partition to 40GB and merge the new empty 10GB with the old 5GB .. I tried to use GNOME PARTITION EDITOR for this task but it failed to resize the NTFS partition ..
I rebooted to XP, installed partition magic, resized the 50GB partition and created a new EXT3 10GB partition but Partition Magic coudn't merge the 2 EXT3 partitions !!!!
So, I installed Paragon Partitioner but it asked for reboot ... And here every thing begins

After reboot I got Grub error 15 .. I used the ubuntu live cd to reinstall the grub, then the boot list came up but only XP boot works and when I choose to boot ubuntu it gives me Grub error 17 !!!
I booted on XP and opened Paragon Partitioner "I didn't use it till then :)", and I merged the 2 EXT3 partitions and I restarted the machine.

What happened after the reboot is that the boot list disappeared and there was always Grub error 17 .. AGAIN, I used the live cd to reinstall GRUB, I restared and the GRUB ERROR WERE GONE 4EVER.

NOW THE PROBLEM IS, when I select XP from the boot menu it loads perfectly, but when I choose to boot ubuntu it tries to perform "sfck -> System File ChecK" and it fails then it tells me that "apt" is not installed and i need to install it using "apt-get install apt" !!!!!!!!!!!!!!!!!!!!!!!!!!!!

HELP PLZ !!!!!

---

