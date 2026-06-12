---
title: "Dual Boot Install of 10.04 LTS on RAID 0 Sony Laptop Win 7"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by GreginSJ on 2011-04-13
Trying to install 10.04 LTS as a Dual Boot (17.5 Gb partitioned) on a Sony Vaio S-Series Win 7 pro with 256gb SSD (two drive config), and 8 gig RAM.  Getting the "No Root File System is defined..." error at the point in the installation where you have to select the proper volumes on which to install Ubuntu.  I guess my question is, do I need to have two partitions to do a good Ubuntu install?  1 partition for as a mount drive, and 1 partition for a swap drive?  Should the mount drive be set to "/" or "/Home" and formatted as NTFS or Ext3, or Ext4?  Same for Swap on the extensions?  Also, is 17.5 gb enough for running a Magento database programing development and testing environment?

---

### Post by Hedgehog1 on 2011-04-14
I am a little confused by your title vs your post, so I want to be sure I understand:

Are you installing in a single 256 gig SSD device?  Or on a RAID 0 Array made of two 128 gig SSD devices?

If this is an array of Raid0 devices, we need to be sure the RAID is happening at the hardware level so Ubuntu can run on it.  To test that, boot off the LiveCD/LiveUSB, select 'try', and in the places menu open up one of your NTFS partitions and look at a few pictures.  If the LiveCD/LiveUSB can read the NTFS partitions OK, you can dual boot Ubuntu.

As to the partitioning, because the Windows MBR style of partition map only allows 4 primary partitions, we typically make an extended partition fir the Linus dual boot, and put 2 or 3 logical partitions in that.

Your current install for Windows 7 will have a least two partitions:

/dev/sda1 NTFS (100 meg windows boot partition)
/dev/sda2 NTFS (Windows 'C:' drive)

We would have you shrink your Windows partition using Windows Disk Manager to make room for Ubuntu.

Then we would have you create (using gparted from the LiveCD/LiveUSB) an extended partition (dev/sda3 or dev/sda4 if you have a 'D:' drive in Windows)

Then you would create either 2 partitions:
/dev/sda3
__/dev/sda5 EXT4 Ubuntu '/' (root) partition
__/dev/sda6 Swap

Or 3 partitons:

/dev/sda3
__/dev/sda5 EXT4 Ubuntu '/' (root) partition
__/dev/sda6 EXT4 '/home' partition
__/dev/sda7 Swap


First - make sure you can read the ntfs partitons from the LiveCD/LiveUSB so we know your raid is OK with a non-windows OS.


***The Hedge***

:KS

---

### Post by GreginSJ on 2011-04-14
Thanks for the guidance, and sorry about the confusion re the RAID 0 in the title (Sony does use two drives, I'll clear that up in the original post).  According to the tech folks over at Sony, installing Linux on my Laptop could basically trash the HD - i.e. voiding the warranty, and will most certainly have serious troubles with an unknown number of drivers.  I was completely bummed.  I'm going to give up on the Sony and use an old Thinkpad T61.  I've heard Ubuntu installs flawlessly on that.

---

### Post by Hedgehog1 on 2011-04-14
> **GreginSJ said:**
> Thanks for the guidance, and sorry about the confusion re the RAID 0 in the title (Sony does use two drives, I'll clear that up in the original post).  According to the tech folks over at Sony, installing Linux on my Laptop could basically trash the HD - i.e. voiding the warranty, and will most certainly have serious troubles with an unknown number of drivers.  I was completely bummed.  I'm going to give up on the Sony and use an old Thinkpad T61.  I've heard Ubuntu installs flawlessly on that.

Linux installs need less horsepower, so you will still enjoy Ubuntu on the Thinkpad.

Of course, Ubuntu on a killer system is - well - **killer**. :D


***The Hedge***

:KS

---

### Post by opodaniel on 2011-07-29
Check this tutorial on how to install Ubuntu on Sony Vaio with ssd raid 0. Hope will help
[http://ubuntuforums.org/showthread.php?t=1814341&highlight=sony+vaio+ssd](http://ubuntuforums.org/showthread.php?t=1814341&highlight=sony+vaio+ssd)

---

### Post by GreginSJ on 2011-07-29
I ended up purchasing a Dell E6420 laptop (also with 256gb SSD).  Ubuntu 10.10 installed on it flawlessly, and the Dell web site has all of the Ubuntu 10.10 specific drivers for that laptop on their web site.
  
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=04&l=en&s=bsd&catid=-1&dateid=-1&formatid=-1&hidlang=en&hidos=W764&impid=-1&os=WN104&osl=EN&scanConsent=False&scanSupported=False&servicetag=1G385Q1&SystemID=lat_e6420&TabIndex=&typeid=-1](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=04&l=en&s=bsd&catid=-1&dateid=-1&formatid=-1&hidlang=en&hidos=W764&impid=-1&os=WN104&osl=EN&scanConsent=False&scanSupported=False&servicetag=1G385Q1&SystemID=lat_e6420&TabIndex=&typeid=-1) 

I couldn't be more happy.

---

