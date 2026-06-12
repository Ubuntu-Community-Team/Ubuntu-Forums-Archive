---
title: "Please Help - 2 SATA Drives Disappearing During Install"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by vadimolen on 2007-03-13
Hello,

I wanted to start off by saying thanks to everyone who works on Ubuntu and everyone who helps out here, I'm slowly moving my entire family off of Windows and we couldn't be happier!

I was starting to get more comfortable with Ubuntu after installing it on my girlfriend's laptop, and then Kubuntu on my own, so I decided that what I needed was a home file and print server.  I read up on Samba and Cups and decided to give it a shot. 

I bought/used the following hardware:
-20GB PATA Seagate hard drive for /
-160GB SATA Seagate hard drive for storage
-250GB SATA Western Digital hard drive for storage
-AMD Sempron 64 3000+ (Manilla Core, 1.6Ghz)
-ASUS M2V-MX Motherboard (VIA K8M890)
-512MB Kingston DDR2 RAM

I decided to use the Ubuntu Edgy Alternate CD so that I could use a software RAID-1.  I ran the installer ("text-mode" option) and had no problems until I got to the partitioner.  At first it found all of the drives and everything was fine.  

I created a 160GB partition on the 250GB WD drive and set "use for" to software RAID.  The other 90GB I used to create an ext3 partition for storage and set a mount point of /share/normal. I then created a 160GB partition on the 160GB Seagate drive and also set "use for" to software RAID.  Finally, I choose "Guided Partitioning" for the entire 20GB drive to install the file system.  

I went to set up software raid, and it told me that it first needed to write the changes to the 20GB drive.  I said ok and it went about doing it's thing.  After a few minutes, the background changed from blue to red and it said that it could not create a file system on the 20GB drive. I didn't see another option, so I restarted the computer.

At this point I was worried that it had messed up the 20GB drive and so I booted into a gparted liveCD and formatted the 20GB drive to be an ext3 partition.  gparted didn't see the SATA drives at all, but I wasn't thinking about that.

So, I boot the alternate install CD again to try the install again, and this time the partitioner doesn't even see the SATA drives!  I tried powering down, unplugging them, plugging them back in, even using different SATA ports on the motherboard (it has SATA and SATA2), but no luck.  Also, they are found in the BIOS.

So, can anyone help me get the installer to find the drives?  Thanks again, and sorry for the verbosity! 

-Vadim

---

### Post by vadimolen on 2007-03-15
(bump).  Can anybody help?

---

