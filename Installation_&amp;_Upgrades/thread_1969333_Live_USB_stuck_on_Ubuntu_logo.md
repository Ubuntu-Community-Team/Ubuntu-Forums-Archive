---
title: "Live USB stuck on Ubuntu logo"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by sasasas on 2012-04-29
Hello,

I bought a brand new hard drive and decided to install ubuntu on it. I am a beginner with Linux and might have destroyed my hard drive :(

Please help me to recover my hard drive and install linux on it. 

I first burnt an image of the ubuntu live cd onto a usb. Using the usb with the new hard drive I got to the screen that says Try or Install. I clicked on Install. It went through the steps until it said ext4 file system failed. I then rebooted and deleted all the partitions and quit. After restarting, the system is stuck on the ubuntu logo. It does not go any further. What should I do?

---

### Post by oldfred on 2012-04-29
Some systems seem to lock-up after issues. Try a total power off, or if a laptop remove battery. Then in BIOS choose to boot USB. 

What system is it and what video card do you have? It would be best to try ubuntu first to make sure you do not have any major issues.

I prefer to partition in advance and then use manual install. Ubuntu will normally install to one large / (root ) partition and swap. Better to have /home separate or separate data partitions. Or you may want other partitions.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by sasasas on 2012-05-11
Hello,

I replaced the hard drive with a new one, but ubuntu does not load from the usb drive. I went into bios and there is no usb listed in the boot devices. All I have is CD, FDD, LAN and Harddrive. What do I do now? Please help me install ubuntu.

---

### Post by efflandt on 2012-05-11
Note that USB only shows up as a boot device in CMOS setup if USB flash or drive is actually plugged in during boot.  Or the BIOS splash screen likely has a hot key (F-12 or Esc) to select which device to boot from.  For some computers (like Dell) even if you set USB to boot before hard drive in CMOS setup, you still usually need to use the hotkey during BIOS splash to select boot device.

When you put the live/install iso on the USB, did you set it up for persistent data (is there a casper-rw file on it)?  If you had persistent data and shut down improperly (by using computer power button instead of selecting shutdown from Linux), maybe something got corrupted in persistent data.

I wonder if you were actually booting from the hard drive with the partitions removed instead of USB.  But you must have figured out how to boot from USB originally.

---

### Post by sasasas on 2012-05-12
I reset defaults in the bios and it brought up the usb as a boot device. I used gparted to partition the drive. The install process is running for 3 hours now and still has not finished. How long does an install usually run? 

The hard drive is 300Gb.

primary /boot ext3- 200mb
primary / ext3- 20gb
primary /swap - 3gb
extended 
/tmp ext3 - 5gb
/var ext3 - 12gb
/home - rest of the space

---

### Post by sasasas on 2012-05-12
It seems to be stuck on ubuntu CRON[23209]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Can I skip this package?

---

### Post by oldfred on 2012-05-12
I install from an ISO on a hard drive to a partition on another drive in less than 15 minutes. I had not used a CD for ages and tried that again and it was about half an hour including updates from Internet (is high speed Comcast). System is 6 years old dual core. I find install from Flash is faster than CD, but install from hard drive is faster still.

I would not skip anything. Did you verify ISO was valid? Did you run the try also just to make sure it works on your system? If you checked the download updates and have a slow Internet connection that could make it slower. Are you using a Ethernet connection, not wireless?

I do not recommend any separate partitions except for possibly servers. If just starting you can have the default of / (root) & swap although we often suggest a separate /home to make it easier to upgrade with a clean install.

I think Herman does not even use a partition for swap as he uses a swap file. I still use a swap partition.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by sasasas on 2012-05-12
I ran the try, before install. It seems to be moving now but still slow. I switched from wireless to cable. I have high speed internet. It has been 4 hours and counting.

I created the partitions by reading on the internet. There are so many variations that I just picked one and went with it.

---

### Post by oldfred on 2012-05-12
Most of those partitions layouts are old and/or for servers.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by sasasas on 2012-05-12
Well, the installation is still churning through. About 6 hours now. Can I switch off the machine, redo the partitions and then try the install again?

---

### Post by oldfred on 2012-05-12
Only if there is nothing to save, as stopping will leave it unbootable. If starting over there really should not be problem. 

Do you not have much RAM. I did an install to a very old system with only 256K  several years ago with the full Ubuntu and it took very long like yours. I left it overnight & it did work, but was too slow. I did not know then that I did not have enough system for the full Ubuntu.

---

### Post by sasasas on 2012-05-13
I quit the installation midway and used gparted to delete all partitions and start anew. I did the partitions like you suggested and went through the installation again. I noticed that there was a format filesystem option that I had left unchecked in the previous try. That must have caused the issue. Now the intall ran through successfully in about 15mins. I'm up and running with 12.04 or whatever the latest version is. Thanks for the help.

---

