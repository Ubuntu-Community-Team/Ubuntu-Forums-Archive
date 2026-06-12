---
title: "Multi-boot on RAID5"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by Yitzach on 2012-01-23
I'm fairly certain no one else has done this trick in this manner.
I  have a copy of XP from my aluma mater (free). I have a copy of Win7  upgrade and Office 2010 from my graduate university for cheap. And I'm  tired of Microsoft putting out crap OS's (Vista and Win8 by appearances)  so I have Ubuntu. I would like to have them as multi-boot on my  computer.
My computer has a 3 500 GB drives in a fake RAID 5. The  motherboard is Gigabyte Z68XP-UD3. I partitioned the RAID into 65 GB, 10  GB, and the rest sections. Win7 resides on the 65GB C drive. XP resides  on 10 GB D drive. Ubuntu will go on what is left on the E drive. If I  need to nuke it one more time, XP will get 5GB more. I have nuked it 3  times so far trying to get XP and Win7 on the computer.
To get here:
1. Use XP partition tool to divide RAID5 into 65 GB (C), 10 GB (D), everything else (E)
2. Format C and install XP without booting into it. (RAID5 drivers not properly copied)
3. Format D and install XP without booting into it. (RAID5 drivers not properly copied)
4. Upgrade C to Win7 and boot into it.
5. Copy drivers for RAID5 into 3 spots of XP because they all look like they could be the correct spot and and each has its merits.
6. Boot into D for the first time.
7. Install drivers and programs that come with them into Win7 and XP.
8. Install other programs and update.
9. Initialize RAID5 with Intel Rapid Storage.
10. Install Ubuntu 11.10
About  7 seconds into the Ubuntu installer boot up, it stops moving forward  shortly after it detects the RAID5. I have previously installed Ubuntu  11.10 on the computer as the sole OS so I know what it takes to install  it on the system.
Are these the correct steps? Should I have put  installing Ubuntu a little higher up on the steps to say in between 6  and 7? Is there something that I need to do to XP or Win7 before  installing Ubuntu so it doesn't hang at 7 seconds?

Computer ("some" assembly required):
OSs: Win7 64-bit (65 GB partition), XP 32-bit (10 GB partition), Ubuntu 11.10 64-bit (the rest partition)
Motherboard: Gigabyte Z68XP-UD3
CPU: Intel i7-2600K
RAM: 32 GB (I know XP can only address 4GB of it)
HDD: 3 Hitachi 500GB in fakeRAID5
GPU: EVGA Nvidia GeForce GTX 460 v2

---

### Post by darkod on 2012-01-23
I have two questions.

1. Are you using the Alternate Install CD and not the Desktop, as recommended for raid? Yes, I know desktop can also see a fakeraid array but the recommendation to use alternate isn't for nothing.

2. You said "everything else E:" which sounds like one huge ntfs partition (because only windows assigns letters). That means during the ubuntu install you are shrinking that ntfs partition at the same time. Right so far? If you already plan to triple boot, why assign the rest of the disk to ntfs partition and shrink immediately? Can the shrinking create your problem maybe?

---

### Post by Yitzach on 2012-01-23
E is automatically assigned to the partition by Windows independent of format. I was hoping it would play nice and I would not have to format it before installing. But something made me change my mind and format it NTFS (858 GB). It will be Ext4 when I get done with it. I'm not sure if it has even bothered to look for partitions yet much less shrink their contents. Now that it is NTFS, one of my OS's as placed some system data on it taking an unauthorized 32 GB.
It looks to be the desktop version as I got it directly from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) without going anywhere else. I don't recall if I actually ran across the recommendation to use the alternate version before I downloaded it. I'll examine the possibility that it might solve the problem shortly.
I don't happen to have a proper USB thumb drive immediately present. You wouldn't happen to know what might happen if I used the SD card in my cell phone as a thumb drive by any chance?

---

### Post by darkod on 2012-01-23
Sorry, but you are wrong. In windows a letter is only assigned to a partition once it is created, and only in a format it can understand (in other words ntfs, I doubt you will be using fat32 these days :) ). If the space is left as unallocated (unpartitioned) it never has a letter. Also if a partition is a format it can't understand, it doesn't allocate a letter (I just checked in my dual boot).

In fact, there is no problem creating a NTFS partition in that huge space, as long as you leave unpartitioned space with the size you want to allocate to ubuntu.

For the alternate image, look carefully in this list and select the one you want, 32bit or 64bit:
[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

Also in the text at the top, look at the section named Alternate Install CD and note where it says:
LVM and/or RAID partitioning

PS. Just to warn you on the alternate install, the installer is text based, not GUI. It looks like the XP installer. But it installs the same desktop OS as the standard, live CD (Desktop image). Don't get confused, you still end up with the same OS just the installer is text based.

---

### Post by Yitzach on 2012-01-23
Don't insult my ability to observe facts, it knows what RAW format is and what can do with it (nothing). Both XP and Win7 called it E before I had it formatted NTFS. It was partitioned, not formatted.
I borrowed a proper data stick instead of using my cell phone. I checked the MD5 sum. After I selected the new partition rules and told it to write changes to disk, it says "Operation not permitted during write on /dev/md126"

---

### Post by Yitzach on 2012-01-24
I tried something a little different. I deleted E from XP because Win7 was using it as Page File. Then I tried to install Ubuntu and it stopped moving forward after the partition setup with out saying anything more. It did it once, I'm not sure why. I tried few more times and it gets back to the "Operation not permitted during write on /dev/md126."
The OEM mode doesn't help.
Does Ubuntu call "configure the RAID" what Intel calls "initialize the array"? The install said changes can't be made after the configure process has happened. Intel says the array has been initialized.

---

### Post by Yitzach on 2012-01-24
Tried Wubi. This time it booted and had the following thing to say after failing to load correctly:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules: ls /dev/)
ALERT! /dev/disk/by-uuid/98FAD695FAD66F4E does not exist. Dropping to a shell!!

BusyBox v1.18.4 (ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

It completely correct, the only drive listed in that directory is 18SE-0233.

---

### Post by Yitzach on 2012-01-26
This might help: it calls the RAID array "RAIDmd126 device #:RAIDactive device#(read-only)RAIDraid5 device #sda[2]RAIDsdb[1] device #sdc[0]RAID126 device #" I see this thing about "read-only" Would this prevent it from partitioning the drive or any of the other brick walls I've ran into?
That device mentioned above was 18EA-0233. I tried to change the device but nothing helped it. I have nuked it again and am attempting to start with Ubuntu. The errors persist. As you have my motherboard make and model, you can download the manual and check for settings in the BIOS that might cause me problems.

---

### Post by Yitzach on 2012-04-21
So I've made some compromises with the system trying to get it to no longer be a $1700 paperweight. I now have Win7 and Ubuntu on one drive and the other 2 in RAID0. I'm dropping the XP and upgrading the 2 programs that would have been ran in that OS. I managed, after some difficulty to get Win7 to see and understand the RAID0. The whole thing has been formatted NTFS. Ubuntu is still playing dumb. There is a point in the alternate install where it asks if you want to activate serial ATA something or other right before the partitioner. I told it 'no' this time because it had problems with the RAID5 configuration and I didn't want to find out the hard way that was the problem. Now that I can get into the OS, I have no idea how to get the OS to see much less play with or otherwise store anything on the RAID0. How might I be able to "activate the serial ATA" thing after the install?

---

### Post by Yitzach on 2012-04-22
I screwed up the video driver install so I had to reinstall Ubuntu. This time I told it to activate the serial ATA RAID devices and I mounted /home to it. Apparently, it doesn't know how to activate the serial ATA RAID device after installation because it said the drive with /home on it couldn't be mounted. That causes some problems because the passwords are stored there and so I couldn't login. GUI did work. Windows does confirm that the install disk does know how to interact with the SATA RAID because the RAID0 is now a "RAW" format instead of NTFS. I assume it means ext4 because that is what I told the install to do to it.
I tried the fix broken system with the install disk. I thought I managed  to set up the software RAID. In the process, I managed to move /home to  the disk with the OS and leave /home/Documents on the RAID. I can login  as me but I can't get to the GUI and the RAID is still not being  mounted.
If install knows, why doesn't Ubuntu? Since install does know, Ubuntu should but isn't configured to do so. How would I fix Ubuntu to play with the RAID?

---

