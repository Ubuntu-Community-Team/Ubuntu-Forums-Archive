---
title: "LVM ate my drive!"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by john409 on 2015-07-10
I set up a new computer the other day, and have 3 hard drives in it. 
SSD 256GB
SSD 120GB
HDD 1T

I installed a dual boot for Windows and Ubuntu on the 256GB SSD and was planning to use the 120GB for data storage and the 1TB for backup. But after I was all done ... the 120GB drive is not showing and it seems to be partitioned strangely. There is a 

Partition 1 is 255MB Linux partition (Ext2) 
Partition 2 is 120GB Extended
Partition 5 parallels partition 2 and is a 120GB LVM2 and shows that it is FULL!

Partition 2 and 5 are locked against tampering with GParted...though I am pretty sure it will format if I attempt it.

Can I reformat it without tanking my system? I am not sure exactly what LVM is, and did not intend to set it up on this disk.

---

### Post by yancek on 2015-07-10
>  I am not sure exactly what LVM is, and did not intend to set it up on this disk. 		

LVM is definitely NOT the default install.  On a system with a current operating system, it would probably be the 4th option, just above Something Else which means that you did select it.  Probably be easier to reinstall and select the manual (Something Else) option.

> 
Partition 2 and 5 are locked against tampering with GParted...though I am pretty sure it will format if I attempt it

That would happen if you are trying to use GParted from an installed system on the partition to which it is installed.  Use GParted from the installation medium and righ-click any partition and select the option to unmount it before making any changes to it.

---

### Post by oldfred on 2015-07-10
Probably better to keep Windows on one SSD and Ubuntu on the other SSD.

LVM is a logical partition layer over the physical partitions. So the physical partition will show as full, but logical partition will have correct size. LVM also requires LVM tools and you cannot use gparted or standard partition tools on LVM.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

If this is an Asrock motherboard, did you install Windows in UEFI or CSM/BIOS boot mode, you need to install Ubuntu in the same boot mode:

 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/

[/URL]Some have issues with Asrock and its asmedia ports, do not use them for anything.
      
 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

Also you may need nomodeset until you install nVidia proprietary driver from Ubuntu repository or ppa.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    

    


[URL="https://neosmart.net/wiki/disabling-secure-boot/"]
[/URL]

---

### Post by john409 on 2015-07-12
Ok...I figured it out. The LVM partition was set up while I was initially trying to set my drives. It was not actually in use.

The Ubuntu installer kept installing itself on my 1Tb HDD when I was trying to get set up, and I eventually had to simply unplug it to control where it installed. I ended up with both Windows and Ubuntu on the same SSD.

Is there a way to safely migrate Ubuntu over to my smaller SSD? Without a full reinstall?

---

### Post by oldfred on 2015-07-12
Full install can be quicker. If you installed lots of apps you can export list and reinstall. And you can copy /home over.

On my SSD with partitions already created, it took about 10 min for a full install. My ISO was booted from my other hard drive to speed things up a bit using grub's loopmount.

If you copy, you still have to create new partitions, reinstall grub2, and edit fstab with new UUIDs. There are a few other hidden things that also should be updated. If you use clone tools you may  have bigger issues if tools does not change UUID as you cannot have duplicate UUIDs. Clone tools are more for restoring to same partitions with same UUID.

---

### Post by john409 on 2015-07-12
Sigh...I was afraid you might say that oldfred. I don't think it is worth the effort at this point. I will just live with it.

---

### Post by oldfred on 2015-07-12
After reading this post, I install Ubuntu in a 25GB partition on every larger drive.

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

