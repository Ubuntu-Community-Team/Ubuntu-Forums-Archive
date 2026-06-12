---
title: "Partitioning help"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by D-Train on 2012-04-15
Hi guys!

I just got a new Dell XPS13 laptop with a 256GB SSD. I was trying to install Ubuntu 11.10 this evening and when I got to the partitioning I hit a snag. Of course the drive is /sda and there are 4 partitions, sd1-sd4 with sd3 being the biggest partition (~227GB) and is ntfs

So I chose this partition and clicked on "Change" and entered a new size of 187GB. I did not format it, left the mount point blank and the format set to ntfs. Then clicked "Apply" This took me back to the previous list of partitions. My new 40GB partition was labeled "unusable" and I could not make any changes to it, or delete it. So I went to the now 187GB partition and clicked "Change" and resized it back to 227GB. Then I quit the installer. I am now typing this booted from the install CD. 

What did I do wrong? How do I create a 40GB partition and partition it ext4 so I can install Ubuntu to it? Then I need to edit that partition and make a 4GB swap space, leaving me 36GB for Ubuntu. 

Thanks!!

---

### Post by D-Train on 2012-04-15
Well after reading some of the other threads it seems my problem is that I already have 4 partitions. I guess the question is which of my existing partitions to delete? I need the recovery partition (no DVD Drive, so need that) but what the heck is the first partition for? It is Fat16 and is pretty small. 

OK I just looked at the partitions using Windows 7s Disk Manager. Here is what it says;
OEM Partition (39MB) 39MB free so it's empty. I think this one was FAT16
Hibernation Partition (8GB) 8GB Free. Also no format listed but probably NOT NTFS
OS (Main NTFS Partition) 213GB
Recovery Partition (NTFS 18.25 GB) 8GB Free

So what's my best options and why? Thanks!

---

### Post by zombifier25 on 2012-04-15
Actually, you can create an extended partition, which can contain other sub-partition underneath. With this extended partition you can add more than 4 partitions on your drive. Windows will refuse to sit in this extended partition but Ubuntu will do just fine, so use that ;)

---

### Post by D-Train on 2012-04-15
Hmmm, OK, sorry to be so obtuse (and believe me, I work for Apple tech support and HATE dealing with obtuse customers! some customers couldn't find their a$$ with both hands!) but I still have the same question. How do I create an extended partition without first deleting one or more of my existing partitions?  ](*,)
Thanks!

:redface:

---

### Post by Bucky Ball on 2012-04-15
> **D-Train said:**
> Well after reading some of the other threads it seems my problem is that I already have 4 partitions. 

Correct, and attempting to alter the Win partitions (NTFS, FAT) via Gparted (from the LiveCD) is that it will turn the partitions into dynamic partitions. I know nothing about the remedy but wiser heads might chime in and that is somewhere to research.

You need to resize the Win partitions with Win software, not Gparted.

> **D-Train said:**
> I guess the question is which of my existing partitions to delete? I  need the recovery partition (no DVD Drive, so need that) but what the  heck is the first partition for? It is Fat16 and is pretty small. 

OK I just looked at the partitions using Windows 7s Disk Manager. Here is what it says;
OEM Partition (39MB) 39MB free so it's empty. I think this one was FAT16
Hibernation Partition (8GB) 8GB Free. Also no format listed but probably NOT NTFS
OS (Main NTFS Partition) 213GB
Recovery Partition (NTFS 18.25 GB) 8GB Free

So what's my best options and why? Thanks!

These are all Win related. You could boot to Windows, make the recovery CDs and all that, resize the Win partitions whilst deleting the superfluous partitions (recovery etc) then install Ubuntu.

Yes, extended partition is a good idea (as you can theoretically have as many logical drives inside one as your hardware can handle) but you are right; you need to sort out the four partition max first. 

Primary partition = Windows; First drive, first partition (it likes it that way but take note some versions of Win use several partitions when instlling!).
Ubuntu = will exist on a logical drive inside an extended partition.

---

### Post by D-Train on 2012-04-15
This is a test to see if I can post an image.

[IMG]http://denniswelch.co.cc/images/partitions.jpg[/IMG]

---

### Post by oldfred on 2012-04-15
Best to shrink images to small sizes and use paperclip icon in edit panel above message to include screenshots. Ubuntu's screenshot app works well for directly making uploadable pictures.

Do not create new partitions with Windows as it will convert to dynamic partitions. 

If booting with UEFI the first partition is an efi partition where efi boot loaders go, but with Windows you have to have gpt partitioning not MBR(msdos) and then you do not have logical partitions as all are primary.

Is this really Windows 8 as it has the new quick reboot from hibernation for all shutdowns and creates some issues with dual booting. You have to turn off the quick reboot feature if you want to dual boot.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Normal Windows 7 in MBR has a hidden 100MB boot/repair partition, the main (c drive), and then the vendor's image of the hard drive or recovery and usually a vendor tools partition just to make sure they have used all 4 primary partitions.

Does not the vendor recovery allow you to make a multiple set of DVDs or a USB that is the recovery? You also should make a Windows repair CD/USB, so if you cannot get into your system for any reason you can repair it.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by D-Train on 2012-04-15
Hi Fred,
Thanks for the reply. This whole scenario seems rather complex and I'm pretty reluctant to start changing my partitions for fear of screwing something up. 

As I said in my first message, this is a Dell XPS13 (an ultrabook) with an SSD so I have no optical drive for making recovery DVD's. I guess I should go ahead and make a USB based recovery option on a thumb drive. I believe they have used some proprietary partitioning schemes for the "quick resume" feature and I really do not want to disable the quick reboot feature. 

I think I'll just take the safe path and leave this laptop as it is, with Windows 7 only. I already have Ubuntu running on my desktop PC and that should be sufficient for my needs (I'm really just playing around with Ubuntu and don't have a "need" for it)
I figure I could learn a bit of Unix/Linux commands playing with it and therefore learn more about the internal workings of the Mac OS. This can be helpful in my job if I need to use terminal to enter commands, but then again that's Tier 2 territory. Something I rarely need to have my customers do. 

Thanks anyway for the help guys but I think I'm just gonna leave well enough alone! ):P

---

### Post by Bucky Ball on 2012-04-15
Cool. Please mark thread as 'Solved' from 'Thread Tools'. ;)

---

### Post by mbogevik on 2012-04-15
If you have a good USB thumb drive (large and fast enough) that may be a good place to install Ubuntu as an alternative to the SSD disk ?

---

### Post by D-Train on 2012-04-15
Yeah I had already considered that option. Or I'm thinking of getting a USB 3 external drive, and I can just install it on that.  :cool:

---

### Post by D-Train on 2012-04-24
> **mbogevik said:**
> If you have a good USB thumb drive (large and fast enough) that may be a good place to install Ubuntu as an alternative to the SSD disk ?

Hmm, OK so I got a new 32GB Thumb Drive today and went to install Ubuntu 11.10 on it. I told the installer to create a new partition on the thumb drive and make a 28GB EXT4 partition and a 4GB swap space on it but when I try to install I get the message "No Root File System" I had also pointed to the thumb drive as the location for the boot manager. Was this the problem? If so please keep in mind my previously defined 4 partitions on the SSD, I'd rather not mess with them if I don't have to but I guess the boot loader may need to be on one of the SSD partitions, but which one? I managed to install Ubuntu on another computers external HD, but the boot loader doesn't even load if the drive is not plugged in, so is the boot loader on the external drive or is the boot loader on the internal drive and it just defaults to Windows if it can't find the external drive that has Ubuntu on it? :confused:

---

### Post by oldfred on 2012-04-24
You do want to install the grub2  boot loader on the MBR of the flash drive. Or any external install you want grub2's boot loader on the external so it does not modify the boot on any internal drives. Then you use BIOS to choose boot device or use BIOS's one time boot key.
 But grub2's bootloader defaults to sda unless you use something else or manual install. With manual install you have to specify a / (root) partition. You do not have to have any others including swap. 

I installed 12.04 on my 16GB flash drive in a 8GB partition with 8GB just for data. But I always partition in advance and since I was never using that install on anything else and wanted to learn about gpt partitioning and Arch recommends gpt for SSDs, I used gpt.

f```
red@fred-Precise:~$ sudo parted /dev/sdb unit s print[sudo] password for fred: 
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs

```

---

