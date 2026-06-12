---
title: "Western Digital MyBook Essential 2TB does not mount"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Kiddosr on 2010-06-10
Ubuntu 10.04 LTS on VirtualBoxVM  
Western Digital MyBook Essential 2TB USB   

Want to format and partition the external hard drive for USB storage for DD WRT (i.e. into ext3)    

The drive is MS-DOS (FAT32) - Using Disk Utility (MAC) i erased what was on the drive.  

It mounts properly and can be accessed on the Mac OS.  

 Upon plugging the USB into the Mac, the drive does not show on the Ubuntu desktop.  Under the USB icon (bottom right) it indicates no USB devices attached however the "Western Digital My Book [0175]" is greyed out.   

 Going "Places" > "Computer"   Only "File System" visible.

GParted - Drive not visible (only /dev/sda)    

Using the sudo fdisk -l:   
Disk /dev/sda: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Any recommendations? Or if further information would help please tell me.

---

### Post by wkulecz on 2010-06-10
The WD MyBook drives I have use some bogus partitioning scheme that makes Windows install the drive as two devices, a CDROM with some lame windows only software, and then the hard drive.  I suspect this is what is messing you up.

You can download utilities from WD to delete the CDROM crap and repartition the device as a normal hard drive, but you need to do this on a windows machine :(

I won't be buying any more of these, but the two I have worked well on a Linux based video player box once I removed the bogus CDROM crap.

---

