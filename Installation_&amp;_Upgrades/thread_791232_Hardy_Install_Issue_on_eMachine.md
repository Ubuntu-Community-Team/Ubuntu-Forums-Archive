---
title: "Hardy Install Issue on eMachine"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by krieggegenpaz on 2008-05-12
Hello all,
  I can't quite figure out this problem that I'm having trying to get Ubuntu 8.04 installed on an eMachine T3265. The problem comes when I hit the disk partitioner. The live CD boots all the way and starts to install just fine, but when it hits the partitioner and gets cracking away at making the first partition, it stops around 5% and never progresses. While the partitioner is trying to run, I hear the disk inside the machine spinning and seeming like it's working, and then it will sound like it powers down. Then it starts running again, this continues, no progress for over an hour. One attempt produced an error saying that it couldn't create the partitions and then wouldn't show the device in the partitioner menu when it took me back to the menu. I have tried to boot the system with "noapic nolapic pci=noacpi", because that fixed a similar issue a while back on an HP machine. I'm fresh out of ideas, anyone had a similar issue they were able to overcome? 

Here are some specs on the system:

CPU:  	AMD Athlon™ XP 3200+ Processor
QuantiSpeed™ Architecture operates at 2.200GHz
512KB L2 Cache & 400MHz FSB
Chipset: 	NVIDIA® nForce™2
Memory: 	512MB DDR (PC 2700)
Hard Drive: 	160GB HDD
Optical Drive: 	DVD ± RW Drive (Write Max: 4x DVD±R, 2.4x DVD+RW, 2x DVD-RW, 16x CD-R and 10x CD-RW disks, Reads 12x Max. DVD-ROM disks, Reads 40x Max. CD-ROM disks); 48x Max. CD-ROM Drive; 3.5" 1.44MB FDD; 8-in-1 Media Reader (USB 2.0, Secure Digital™ (SD), Smart Media, Compact Flash, Memory Stick®, Memory Stick PRO, Micro Drive, Multimedia Card)
Video: 	NVIDIA® GeForce®4™ MX graphics (1 AGP 8x slot available)
Sound: 	nForce™ 6-channel Audio

---

### Post by bobnutfield on 2008-05-12
Hello

This sounds (but may not be) a problem with the disk itself, possible bad sectors preventing a partition from being written.  Are you installing with the LiveCD?  If not, try loading a live CD (any will do, Knoppix, or GParted live cd if you have it).  See if:

1.  The partition shows up as it should from the LiveCD

2.  Try to partition and write a filesystem to the parttion from the live cd.

If you fail using the LiveCD, that is pointing to a problem with the disk itself.  There are disk checking tools on the Live CD.  The Gparted LiveCD (available from the site) has gotten me out of a couple jams in the past.

Bob

---

### Post by housam on 2008-05-12
Try to partition your HDD manually before installing ubuntu using the Gparted tool ( on the live CD - or download the [[COLOR="Red"]_newer version_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") and burn it to a cd to make a bootable live cd of it ). then start the installation and choose the manual way when it comes to partitioning and assign the already created partitions .

---

### Post by jadedoto on 2008-05-12
I seem to have a similar problem. My machine:

AMD Athlon XP 2800+
Integrated GeForce4
nForce2 chipset 

I can get Gusty up just fine, but Hardy... The liveCD sticks around 5%, and when I install, I can get just a black screen after the progress bar sticks at the same place. 

Booting into recovery mode, I saw it locked on something called... padlock_aes? Some kernel module that failed to load or something...

---

