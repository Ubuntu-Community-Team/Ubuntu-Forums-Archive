---
title: "Multiple HDD &amp; GRUB Advice"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by wagb278 on 2015-10-08
I currently have two internal HDD with GRUB-2 configured for dual booting, all is well.  I have ordered two additional HDD to add to the computer and intend to install distributions on those new drives. Not sure of my terminology here, please forgive my ignorance on this topic. My initial intention (desire) is to install Ubuntu-based distributions on partitions of the new drives; so there will be four distributions available.  At some later time I will likely remove the old drives thus leaving only the two new ones, initially there will be four physical drives each with a distribution installed.  I just want a functioning system while I install & configure the new drives. 

So, first question is - can GRUB accommodate four boot targets?  I am assuming yes. 

My current installations were set to use /dev/sda for boot. My understanding is that means at Boot time the BIOS goes to drive zero to get instructions for available distributions and shows the GRUB menu.  If I remove the old drive zero (sda) how do I get the Boot instructions onto one of the new drives? 

Would I be better off just replacing the old drives with new ones and installing the distributions on the new drives so one of the new drives becomes drive zero (sda)? 

Related question - Is there a way to make two drives independent such that if drive 0 fails the second drive can still boot? I assume this is not possible, the BIOS needs a single drive to access, but maybe I am wrong. 

Any advice is welcome, thanks.

---

### Post by Dennis N on 2015-10-08
Assuming you are not using UEFI.

I use two drives with each containing operating systems. I install the grub bootloader for each OS to the drive it is on. Each drive is then bootable. The drive that's booted by default is set in the BIOS boot order, so if you later make changes, you can adjust that order if necessary. You should also be able to boot any drive from the one-time boot option most computers have.
 
The controlling Ubuntu on each drive will detect the other installations and include them in its grub menu using the os prober during installation.

Should be easy.

---

### Post by wagb278 on 2015-10-08
Thanks for the reply Dennis.

If I understand what you do, instead of specifying just sda for Boot information I should specify a partition such as dev/sdc1 or sdd1 (what the new drives will be) and if a drive fails I can change a setting in BIOS to allow booting from a working drive.  Right?  Seems like what I should do.

---

### Post by yancek on 2015-10-08
> My initial intention (desire) is to install Ubuntu-based distributions  on partitions of the new drives; so there will be four distributions  available.

Not sure if you mean to put one distribution on each drive but if that is the case it would be a simple matter of installing Grub to the MBR of that specific drive, /dev/sda, /dev/sdb, etc.

The number of 'target' systems Grub can boot is limited by the size of your hard drive(s).  There is a post at the Just Linux forums from years ago by a member named Saikee who had 140+ operating systems installed on one computer using Grub Legacy to boot or chainload all.

> My current installations were set to use /dev/sda for boot. My  understanding is that means at Boot time the BIOS goes to drive zero to  get instructions for available distributions and shows the GRUB menu

Correct.  You can change which drive is set to first boot priority in the BIOS setup.  If all four drives are recognized in the BIOS and you have installed Grub to the MBR, you can simply change the boot order to boot whichever drive you want.

> 
Related question - Is there a way to make two drives independent such that if drive 0 fails the second drive can still boot? I

Yes, explained in paragraph above.

NOTE.  All of this will be different if you are not using MBR but are using UEFI to boot.

---

### Post by wagb278 on 2015-10-08
Thanks Yancek. 

I don't think I have EUFI.  The computer is over 10 years old and I don't do Microsoft, which I think EUFI is related to.  I do put one distribution on a physical drive.  My current configuration has two partitions on each drive but the other partitions are for data files that get mounted at boot time (via fstab).  I plan to dedicate each of the new drives to one partition (distribution) and keep data files in the expected locations, instead of shared folders, mount points. 

I will probably remove the old drives after I have the new drives working.

Thanks again for the insight.

---

### Post by yancek on 2015-10-08
> 
I don't think I have EUFI.  The computer is over 10 years old and I don't do Microsoft, which I think EUFI is related to.

Yes, if your computer is that old there will be no UEFI but it's not related to microsoft it's a modification of the basic manner of booting and is used with Apple (Macs), windows and Linux.

---

### Post by wagb278 on 2015-10-08
Thanks again.  I completely miss understood what EUFI is and your response caused me to look on the Web to find descriptions.  I thought it was some Microsoft invented secure boot modification to BIOS.  Boy was I wrong.  I now have a better understanding of that.  Within a year I hope to be getting a new laptop and will be very interested to see what the Firmware looks like. That laptop will be partitioned and dual booted with Linux distributions.

---

### Post by oldfred on 2015-10-08
If system is over 10 years old, are drives SATA or PATA?
If SATA, BIOS totally controls booting.

But older PATA drives may have BIOS control if configured for cable select using newer 80 conductor cables. 
If not cable select or 40 conductor cables you only control boot by the really tiny jumpers on the hard drive. I really hate those jumpers and changed to SATA as soon as SATA drives were only a few dollars more than PATA and new motherboard that supported SATA drives, and that was my new build at then end of 2006.

---

### Post by wagb278 on 2015-10-09
Thanks oldfred,

The computer is definitely SATA, not PATA configured. I checked my records and the computer was bought in early 2008, so it is not ten years old, so I was wrong on the age. The current drives are SATA, as are the new drives I have ordered.  The Antec Sonata case supports four internal drives and the Intel DP35DP MOBO provides five SATA connectors. I have not checked, but will, what Firmware is on the MOBO (BIOS/EUFI), but I am pretty sure the Firmware is functioning as BIOS.  It might be EUFI in BIOS compatible mode. 

I dual boot only to permit loading a new Linux distro for experimentation and when time to update a distro allowing me to go back to the old one if I have problems.  The original drives are small - a cost decision when I bought this computer - now with the cost of internal hard drives lower it is time to get larger drives.  

The root cause of this whole exercise is that I run a LAMP server for my LAN on this computer and store the MySQL databases and Web files on a separate partition. Each new distribution I install and configure I change MySQL and Apache II configuration to point at that shared partition so both distributions access the same data files.  But a problem is that each distribution uses different UID:GID values meaning data file ownership is usually wrong and I have to manually go into the new system and change UID:GID values to match values used by the other system; which is turning out to be a real pain.  With larger drives I will leave the database and web files in the expected location (not a separate partition).  Then installing and configuring a new distribution will include copying the database and web files from the old system.  I will probably setup an rsync script to automate that copy operation. 

If the distribution makers would agree on standard UID:GID values that would be a big improvement to the user community.  UID:GID values below value 100 seem to be pretty standard, Ubuntu based distro assign human user accounts starting at UID:GID 1000; but the other values depend on the order software is installed - UID:GID values get assigned to next available values.  My two cents worth!

---

### Post by oldfred on 2015-10-09
System from 2008 would still be BIOS only.

I use shared data partition but almost always Ubuntu or one of the flavors. I do like shared data partitions, but only user files. Before users noted that some other distributions used 500 for UID where Ubuntu used 1000. I think Fedora changed to 1000, now. 
But your system applications that have UID:GIDs then are a complication.

---

