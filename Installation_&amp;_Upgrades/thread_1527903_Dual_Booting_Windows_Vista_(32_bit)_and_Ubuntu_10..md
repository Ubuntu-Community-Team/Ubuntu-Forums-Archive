---
title: "Dual Booting Windows Vista (32 bit) and Ubuntu 10.04 (64 bit)"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by SamQ on 2010-07-09
I'm a newbie concerning dual boot OS's and usage in general.
 
Having looked at a few tutorials on how to create a Dual boot system, I'm left with the following questions:
1- If my Vista OS is 32 bit (on a 32 bit laptop), will the 64 bit Ubuntu 10.04 work properly in a dual boot setup? If not what should be done? 
2- If (when creating a dual boot system on 1 hard disk already partitioned as C: (OS) and D: (data files) ) I allocate 30 GB on D: for Ubuntu, ....will applications in the Ubuntu OS partition only access data files in the 30 GB allocated to it, or can it also access data files on D: or C: that are not residing within the 30 GB Ubuntu allocated space?
3- Can the Vista OS "see" any data files located in the Ubuntu 30 GB partition and access them?
4- If the Ubuntu partition is blind to all other partitions, can it access and store data files on an external USB hard drive? If so, is there a significant speed reduction in external hard drive file storage and access when using Ubuntu? I'm concerned about application data storage space.
5- Will doing a complete System Image backup of the Vista OS drive prior to implementing the dual boot system enable me to restore the Vista boot loader? in case something goes wrong with dual-boot?
6- Are there any up-to-date (Ubuntu 10.04) instructions on how to set up a dual boot system using EasyBSD? The current instructions appear dated.
7- I am considering creating a dual boot system on my laptop that has an external "extended monitor" monitor for more desktop space connected to it. Will Ubuntu recognize the extended monitor?
 
Thanks for your help,
SamQ

---

### Post by garvinrick4 on 2010-07-09
64 bit Ok.

If data file is formatted fat32 Windows will give it a Letter and Linux will give it a
partition number. Can swap files easily.

Yes you can mount your Windows OS in Ubuntu.

Always wise to have backup of Home files, docs, downloads, music and such.
Will be able to put Windows boot back if needed. With windows installation or recovery
disk or Ubuntu live cd.

No difference in Linux with USB device.

I use Ubuntu installation disk as install and it is also a live CD. 

[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Mark Phelps on 2010-07-10
> **SamQ said:**
> I'm a newbie concerning dual boot OS's and usage in general.
 
Having looked at a few tutorials on how to create a Dual boot system, I'm left with the following questions:
1- If my Vista OS is 32 bit (on a 32 bit laptop), will the 64 bit Ubuntu 10.04 work properly in a dual boot setup? If not what should be done? 
It it's really a 32-bit laptop, NO.  64-bit OSs require 64-bit processors.
> 2- If (when creating a dual boot system on 1 hard disk already partitioned as C: (OS) and D: (data files) ) I allocate 30 GB on D: for Ubuntu, ....
That's not really dual-boot (in which each OS has its own separate partitions).  For real dual-boot, use the Vista Disk Management utility to shrink the "D" partition to leave free space to install Ubuntu.  Then, boot from the Ubuntu CD and select that free space.

> will applications in the Ubuntu OS partition only access data files in the 30 GB allocated to it, or can it also access data files on D: or C: that are not residing within the 30 GB Ubuntu allocated space?
They CAN access files in "C" or "D", but I would advise strongly AGAINST mounting the "C" partition read-write.  Doing this can clobber the partition and leave it unbootable.  If you MUST access "C", do so only in read-only mode.
> 3- Can the Vista OS "see" any data files located in the Ubuntu 30 GB partition and access them?
Basically -- NO.  The existing utilities that CAN see Linux filesystems from inside MS Windows can NOT work with Ext4 filesystems -- the default filesystem for Ubuntu since 9.10.
> 4- If the Ubuntu partition is blind to all other partitions, can it access and store data files on an external USB hard drive? If so, is there a significant speed reduction in external hard drive file storage and access when using Ubuntu? I'm concerned about application data storage space.
A partition doesn't "see" anything -- it's just a container for files.  When you plugin an external USB drive or stick, Ubuntu will auto-mount it, you will get an icon on the desktop, and you will see a file manager window open for each of the partitions on that device.
> 5- Will doing a complete System Image backup of the Vista OS drive prior to implementing the dual boot system enable me to restore the Vista boot loader? in case something goes wrong with dual-boot?
Yes -- but if you back it up BEFORE shrinking the "D" drive, make sure that when your restore it, you do NOT restore the "D" drive as well.  If you have a Vista DVD, you can also restore the boot loader by booting from it.  IF you don't have a Vista DVD, you can download and burn a Vista Repair CD image from the link below:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

> 6- Are there any up-to-date (Ubuntu 10.04) instructions on how to set up a dual boot system using EasyBSD? The current instructions appear dated.
If you ask HERE, most folks will tell you NOT to use EasyBCD and to use GRUB2, instead.

If you insist on using EasyBCD, you would do bet to check with the NeoSmart Technology easyBCD support forums for details.
> 7- I am considering creating a dual boot system on my laptop that has an external "extended monitor" monitor for more desktop space connected to it. Will Ubuntu recognize the extended monitor?
Don't know -- depends on the video chipset installed and the default driver for it.  Would be best to indicate what video chipset that is.  That would help us answer the question.

---

### Post by efflandt on 2010-07-11
There is no problem having 32-bit Windows and 64-bit Ubuntu on the same drive (assuming that your cpu can run 64-bit).  That really has no effect on how data is stored on the drive.  I have 32-bit WinXP and 64-bit Ubuntu on laptop and desktop.

I would suggest installing Ubuntu on a separate partition instead of using Wubi to install it within a Windows partition.  For Vista or Win7 shrinking a partition is best done with their own admin tools (computer management).  Although, I have had no trouble resizing WinXP NTFS partitions from Linux (years ago using ntfsresize, or more recently using gparted).

Linux can access Windows partitions, although, it does not auto mount partitions on internal drives unless you make entries in /etc/fstab.  It will mount them if you open them from Places in the upper panel.  External (USB) drives or flash are auto mounted when you connect them.

If you want to be able to access Linux partitions from Windows, there are Win utilities that can access ext3 partitions, but probably not ext4 yet.  So if you want to be able to do that, you may want to format the Linux partitions as ext3 instead of the default ext4.  Some people get snooty about that, but even though ext3 may not be the latest, it is very mature and stable because it has been around for years.  I use it.

Otherwise if you do need to access files from Windows or Linux you could simply put them on flash memory or USB hard drive.

---

