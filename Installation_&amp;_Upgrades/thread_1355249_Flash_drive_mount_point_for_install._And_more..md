---
title: "Flash drive mount point for install. And more."
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by garvinrick4 on 2009-12-14
Installing 9.10 on 16 gig flash say it is "sga"  what do I mount the file system as
/ or what. It comes up /media (group of #,s) when I mount as /.  And the grub
in sga or sga1. ?    gparted has no problem making a swap partition and then in
?8 of installation in advanced asks where I want boot to reside.
 I have only had dual and triple boot so there could not be a seperate boot partition
as I am used to.  Could be in sga1 on Flash drive. There is also the question of ext3 or 
ext4 I have been using ext4.  Am I right there?
 Googling does not come up with anyone I have seen that has a complete working system
on a 16 gig Flash that retains upgrades and capable of using computers Wired or wireless
network. Going on Vacation would like to carry as my computer as no WIFI in house I am
staying at. My Daughter has a nice machine to work with though. Sounded easy but lots of questions came up as putting theory into action. Has to be Linux users who have done this before.
                           Thanks for any and all help.

---

### Post by garvinrick4 on 2009-12-15
Grub turns out should be installed in sga1 not sga. Mount point is / but linux sees all removable devices as /media which I have not figured out. gparted is a good piece of software with a lot of little hidden settings you must use properly. Settings can always be learned. So you can get the needed partitions and the Grub installed with OS. Be careful to answer setting 
8 with advanced and in sga1. The g to be whatever your device is when you "fdisk l" before you start just in case you have more than one device you get the right one. 
Leave enough for Swap partition when you set sga1 partition size. 16 gig Thumb drive used
14 gig extended and left about 2 gig for swap. Might need good size swap for different
machines you use. Now if anyone can help me with mount point in Thumb drive. Again I was using / and it did not work defaults to /media.  
 Again do not put Grub in sga for it will install in your HD usually sda and you do not want that, goofs up your existing Grub. Takes some editing to straighten out.
 As stated before not trying to make a Live USB but  a working system on a Flash drive.
  Not getting much action here. Any help would be appreciated.

---

### Post by audiomick on 2009-12-15
Hallo.
I have never done this, but your problem interests me.
Here are a few thoughts that occur to me.

(by the way, your posts are difficult to read. Give a thought to breaking them up a bit with a

return so that the different points are

seperated. ;))

> **garvinrick4 said:**
> Grub turns out should be installed in sga1 not sga.

A word to the naming procedure for drives:
sga would be the name for the drive itself. Normally it would be sda, the second sdb. That yours is sga is probably due to it being a flash drive and not a sata or ide. Anyway, that is the designation for the drive itself.

The designation sga1 refers to the partition on the drive sga. If you had more than one, they would be sga1, sga 2 up to the maximum of 4 primary partitions. If you have an extended partition, the logicals partitions inside start at sga5, even if there are less than 4 outside the extended.


 > Mount point is / but linux sees all removable devices as /media which I have not figured out.

I couldn't find anything on this, but I ***_think_*** it might be something like this:
I you are working on the drive from a running Ubuntu, you will see the drive at /media/something as long as it is mounted. If you boot from it, the file system that you have built on it will start from / because you are now booted from at, and not looking at it from outside.

As I said, that is just a thoery based on your description of what you are trying to do. It could also be utter rubbish...;)

 > gparted is a good piece of software with a lot of little hidden settings you must use properly. Settings can always be learned. 
Yes indeed. :P

> Leave enough for Swap partition when you set sga1 partition size. 16 gig Thumb drive used
14 gig extended and left about 2 gig for swap. Might need good size swap for different
machines you use. 

Rule of thumb for swap these days is swap = RAM, or suspend wont work. For your purposes, suspend is probably not that important, so 2GB is probably a good ballpark figure. On older machines, when RAM was typically 256MB or so, the rule was swap = 2x RAM.
The system will theoretically run without a swap, but this is not recommended, and is likely to be tediously slow.


>  As stated before not trying to make a Live USB but  a working system on a Flash drive.

Actually, I think you are try to make a live USB system.
What you want, if I have understood you right, is a bootable system on a flash drive that you can plug into your daughter's computer when you are in your holiday residence and have it present you with "your" system.
That is a Live CD / USB / whatever.
Don't confuse the "live" with the installer. "Live" refers to a system that is capable of booting itself into the RAM of the computer that the storage device is connected to and running from there without changing the computer that it is running on.

You might be interested in this for your purposes:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

I haven't tried it. I found it whilst searching for stuff relevant to your questions.

As far as the updates go, I don't think you will have much luck there. My impression is, when you build a portable bootable system like you seem to be trying to, it is not updateable. This, however, doesn't seem to be a major problem to me. If the thing works, it works. I would even be reluctant to let it try and update stuff, in case the update breaks something. You  know the adage "never  change a running system";)

I would be more interested in being able to save stuff to take it with me, which is what the persistence thing seems to be about, as well as remembering your settings.

As far as the file system goes, in the course of searching for relevant information to your questions I came across a suggeston to use ext2 for such purposes, as it has a smaller overhead on the storage medium, i.e. uses less space to store the same amount of data. A current Ubuntu will run on ext2. The reason for using ext3, and now ext4, is that the newer version offer journalling and are apparently faster. Your priority, however, would seem to be space.

Hope some of that is some help to you.

---

### Post by Zebedee050 on 2009-12-15
Hello, I have installed Ubuntu from a live CD onto a Kingston 8GB Data DataTraveler.
I think this is what you want to do.     And it works correctly.
 
In reply to Audiomick, to the question of updates, my USB was at first unable to see my WiFi and refused to connect. 
I connected with ethernet cable and each time I connected, Update Manager started automatically and updated my Ubuntu.
About the 6th time I connected, Update Manager installed and activated my WiFi, a Broadcom B43, which I noticed a lot of people were having trouble with. So I can now connect with WiFi.
 
eg. like some others on here, my system said the driver was installed and active but I was not connected.
 
The problem I have is that I need to have the CD installed and the USB stick attached
before I am able to boot into Vista, I am working on this.

---

### Post by audiomick on 2009-12-15
@ Zebedee: ok, I stand corrected!:D

---

### Post by garvinrick4 on 2009-12-18
I have finally got a 16 gig Flash drive to work as independent system. A lot of trial and error.
Used Live CD. 9.10 64 bit and the 16 gig flash drive.
Booted Live CD and selected install.
When it got to partitioning selected USB device of course.
1st partition was 500 meg ext3  /boot as mounting point
2nd partition was 13.5 gig ext3 / as mounting point
3rd partition was 2 gig Swap

IN THE 8TH PAGE YOU HAVE TO CLICK ADVANCED TAB AND SELECT BOOT AS THE SAME
AS YOUR 1ST PARTITION  THAT YOU SELECTED AS /BOOT AS MOUNTING POINT.

 Then add your repositories such as partners, medibuntu, backports, all the same ones as your normal install. You have over 12 gig left to work with so use what you want. Compiz works fine, the only thing in Karmic I have not gotten to work is sound and every install of 9.10 on my HP G71-34OUS has
had sound issues, I will get it. WIFI came right in. Has been a normal install.

Grub menu.  When you upgrade it installs itself onto your systems grub with no partition
number such as sba1 or any device. This works well it just installs a grub selection while
plugged in to USB port with recovery selection.

---

### Post by darkod on 2009-12-18
You should have grub on the MBR of the stick, otherwise I don't see how are you booting it. Yes, you can chainload it to another bootloader otherwise it needs to be on the MBR, for example, /dev/sdb, not /dev/sdb1 (your /boot partition).
/boot partition just means that few second stage grub files will go there instead of a boot folder on /. You still need your bootloader on the MBR as far as I know (although I never tried installing on a stick).

---

### Post by garvinrick4 on 2009-12-18
here is fdisk.   I am running flash drive now.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris

---

