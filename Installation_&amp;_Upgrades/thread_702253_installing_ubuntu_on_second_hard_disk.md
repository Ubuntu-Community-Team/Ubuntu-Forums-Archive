---
title: "installing ubuntu on second hard disk"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by rajkhand on 2008-02-20
My existing system

Asus A7N8X Deluxe, AMD Athlon 2000+, 1 GB RAM
Boot sequence
SCSI (SATA HDD)
IDE
CDROM

1 SATA drive 160GB
1 IDE drive 40 GB

Existing Partions
Sata C: & D: each 80GB NTFS
IDE G:&  H: each 20GB FAT32

The C: drive has Win XP Professional SP2 and is the boot drive

Now I want to install Ubuntu 7.10 on Drive G: 
WITHOUT Partitioning the IDE drive so my data residing on partition H: is not disturbed 
I don't mind erasing formating the G: partitions and creating necessary ubuntu  partitions in the space occupied by it.

Can someone  please guide me how to install and also how I can read write this drive from Win XP?
Oh, I forgot to add that at the time of booting I should have a choice for XP or Ubuntu

TIA
Raj

---

### Post by Nibes on 2008-02-20
Hello. 

Start the system with windows. defragment the hard drive. then reboot using the Ubuntu's Live CD. Then you will be able to see a install icon in the desktop of ubuntu's live Cd. 

Click!: then Make your choices : Country, language, time zone, Keyboard, then choose what disk you want to use for the instalation. keep answer the rest of questions. In a few minutes you will have ubuntu's in your selected drive. 

The instalation process will create a Grub menu which will appear the next time you start your system. there will be a choice in the menu to start windows or ubuntu. you will have only to choose which one you want to work with. by default the grub menu will choose Ubuntu in 10 seconds. 

in future you can choose to hide the Grub menu. or change the options from the menu to start windows has default. 

well I hope this helps. Peace out. 
Nibes.

---

### Post by rajkhand on 2008-02-20
Hey that was quick! Thanks but will this process not disturb my H: partition?

regards
Raj

---

### Post by ajgreeny on 2008-02-20
What is on the D drive as it sounds as if it might be better too put Ubuntu there.  Whichever you chose you will need to do more or less exactly what Nibes says.  When you get to the partitioning section of install, chose manual and then you can set up partitions, a minimum of / or root and swap is required, though many people likt to have a separate /home partition, which makes life a great deal easier if you accidentally mess things up whilst trying linux out for the first time and have to reinstall;  that way you don't lose your data files.  If you do chose the current G drive it should be easy to find at this partitioning stage as it will be the one in the IDE drive with nothing on it.  (Does it have nothing on it?  If there are files on it they will be lost when the ext3 partitions are made and formatted)

However, if you're not very au-fait with partitioning I suggest you just make a / and swap partition, / as big as you can and swap of half to 1GB.  In theory it should be 1-2 times the size of your ram, but that was really for past ages of lower ram in most machines.

Good luck and I hope it all works out for you.

---

### Post by rajkhand on 2008-02-21
Thanks, the D: drive is having my XP data and I'll give it a shot today to install ubuntu on my G: drive.

regards
Raj

---

### Post by Sweatbandman on 2008-02-21
Hiya,

I hope you don't mind me asking a similar question! :)

I have an external Hard Drive (500GB) and I was wondering If I should partition it and put Ubuntu on there, Question is (I couldn't be any newer if I tried) how do I partition the hard drive and how much space should I give it for Ubuntu?

Sorry for hi-jacking the thread!

---

### Post by ajgreeny on 2008-02-22
To be honest it is much easioer to put ubuntu on to an internal hard disk than an external disk.  The problem with an external disk is that by default the ubuntu installer will put grub, the bootloader, on the MBR of the first internal disk, but it will point to a file on the ubuntu drive for the grub configuration.  If the external drive is not attached and switched on the computer will not boot at all.  This can be overcome by putting grub onto the external disk at install time but it is not at all obvious how to do this with the desktop (ie, live CD).  It is easier with the Alternate install CD, however, I suggest you read a bit more about ubuntu and linux before you try an external drive.  Just repartition your main (windows?) drive to make space for ubuntu and put it on there and it will make life a lot easier for a beginner.

---

