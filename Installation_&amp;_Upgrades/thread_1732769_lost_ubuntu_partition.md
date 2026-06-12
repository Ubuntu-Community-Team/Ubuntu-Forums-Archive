---
title: "lost ubuntu partition"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by dfc5347 on 2011-04-18
p { margin-bottom: 0.08in; }  I have been using a dual boot with Vista and Ubuntu 10.10 successfully some time now.  Today my computer shut down unexpectedly when I in Vista.  When I rebooted my Ubuntu partition had totally disappeared.   I booted from a Ubuntu CD and the partition did not show under Places, and when I brought up the disk utility it didn't show there either.  The Windows partition did show in both places.  Below is the output from the boot_info_script.
 

 I would appreciate any help you can provide to restore my missing partition.   
 

  Boot Info Script 0.55    dated February 15th, 2010                     
  
 ============================= Boot Info Summary: ============================== 
  
  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  
     partition #5 for (,msdos5)/boot/grub. 
  
 sda1: _________________________________________________________________________ 
  
     File system:       ntfs 
     Boot sector type:  Windows Vista/7 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:  Windows Vista 
     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  
                        /ntldr /NTDETECT.COM 
  
 =========================== Drive/Partition Info: ============================= 
  
 Drive: sda ___________________ _____________________________________________________ 
  
 Disk /dev/sda: 750.2 GB, 750156374016 bytes 
 255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
  
 Partition  Boot         Start           End          Size  Id System 
  
 /dev/sda1    *             63 1,465,127,999 1,465,127,937   7 HPFS/NTFS 
  
  
 blkid -c /dev/null: ____________________________________________________________ 
  
 Device           UUID                                   TYPE       LABEL                          
  
 /dev/loop0                                              squashfs                                  
 /dev/sda1        DCD83195D8316F40                       ntfs       Windows Disk                   
 /dev/sda: PTTYPE="dos"  
  
 ============================ "mount | grep ^/dev  output: =========================== 
  
 Device           Mount_Point              Type       Options 
  
 aufs             /                        aufs       (rw) 
 /dev/sr0         /cdrom                   iso9660    (ro,noatime) 
 /dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by Rubi1200 on 2011-04-18
Hi and welcome to the forums :-)

Well, this does not look good :(

Apparently, Ubuntu was installed on partition # 5 of the drive, at least according to the script.

Currently, you only have Windows on sda1.

Could you provide some more information please as to what exactly may have caused this and post the specifications for the computer.

Thanks.

---

### Post by coffeecat on 2011-04-18
There is no evidence of any Ubuntu partitions in your boot script output. Indeed, it is showing that there is just one partition in your single 750GB drive, which would appear to be your Vista partition. Not only that, but it is 750.1 GB in size in a 750.2GB drive.

The only way that this could have happened on a single drive from what you've described is that Vista rewrote the partition table and co-opted the other partitions when it shut down unexpectedly. Which is extraordinary. I've seen both the XP and Vista installers do violent things to a partition table, but I've never come across anything like this.

So, a couple of questions. 

Was your Ubuntu installation a wubi install? Wubi is a way of installing Ubuntu to a virtual disc inside the Windows partition. There is no evidence of wubi in your boot script output, but a catastrophic event could conceivably have removed all evidence of it.

Also - do you have just one physical hard drive, or two with Ubuntu in its own partitions on the second drive?

**EDIT**: Oops missed this:

> **Rubi1200 said:**
> Apparently, Ubuntu was installed on partition #  5 of the drive, at least according to the script.

Thanks, Rubi1200. That'll teach me not to post when a bit under the weather. :oops:

---

### Post by dfc5347 on 2011-04-18
p { margin-bottom: 0.08in; }  I did not have a wubi installation.  It was installed side by side with Vista.  I have just one drive with the windows and Ubuntu partitions approximately equal in size.
 

 When  I try to boot, the following message comes up:
 

 Error: no such device: faef9916-1dd6-4fbe-9a36-2ad70739c474
 grub rescue>

---

### Post by coffeecat on 2011-04-18
> **dfc5347 said:**
> When  I try to boot, the following message comes up:
 
 Error: no such device: faef9916-1dd6-4fbe-9a36-2ad70739c474
 grub rescue>

That would be the UUID of the missing partition, which might be useful.

You might be able to recover the lost partitions (in the plural - my guess is that you had at least a swap partition as well) with testdisk from the live CD. Have a look here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

You need to enable the Universe repository before installing testdisk to the live session. But a couple of large caveats. According to the partition table, the Vista partition has spread itself over the whole drive, but we don't know whether the NTFS filesystem has been enlarged to match. If it has, recovering the Ubuntu partitions with testdisk may damage the Vista partition, possibly seriously. Also - don't use the Vista partition before you run testdisk. If the Vista filesystem has been enlarged, you run the risk of writing to areas of the disk where the Ubuntu partitions are.

---

