---
title: "Grub 22 Error"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by yerokleoh on 2007-02-28
So, I've finally installed Ubuntu to the 5th partition of my external usb HD, sdc5.
I restart the computer and GRUB 1.5 comes up. I wait 2 seconds and I get an error 22. I don't have an XP restore disk, because my XP came on my system.
I'm currently typing from the live CD, as it is my only usable OS right now.
Help?

BTW: The biggest thing to glean from this is I am getting a GRUB "Error 22" on startup. :( 

Thanks in advance,
 Max

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> So, I've finally installed Ubuntu to the 5th partition of my external usb HD, sdc5.
I restart the computer and GRUB 1.5 comes up. I wait 2 seconds and I get an error 22. I don't have an XP restore disk, because my XP came on my system.
I'm currently typing from the live CD, as it is my only usable OS right now.
Help?

BTW: The biggest thing to glean from this is I am getting a GRUB "Error 22" on startup. :( 

Thanks in advance,
 Max
Here's a description of grub error 22, with possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

From the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

The Super Grub Disk can restore Windows mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 500 kb download & can boot Windows or Linux.

---

### Post by yerokleoh on 2007-02-28
This is my fdisk -l output 


Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       22752   182755408+   7  HPFS/NTFS
/dev/sdc2           22753       24792    16386300    f  W95 Ext'd (LBA)
/dev/sdc5           22753       24537    14337981   83  Linux
/dev/sdc6           24538       24792     2048256   82  Linux swap / Solaris

Disk /dev/sdd: 503 MB, 503709696 bytes
16 heads, 32 sectors/track, 1921 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1922      491888    6  FAT16
ubuntu@ubuntu:~$



EDIT: The Fat16 is a flash drive, Sdd1 is a flash drive

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> This is my fdisk -l output 


Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       22752   182755408+   7  HPFS/NTFS
/dev/sdc2           22753       24792    16386300    f  W95 Ext'd (LBA)
/dev/sdc5           22753       24537    14337981   83  Linux
/dev/sdc6           24538       24792     2048256   82  Linux swap / Solaris

Disk /dev/sdd: 503 MB, 503709696 bytes
16 heads, 32 sectors/track, 1921 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1922      491888    6  FAT16
ubuntu@ubuntu:~$

Are your internal hard drives SATA, Ubuntu doesn't seem to recognize any hard drives other than your external?
If you can set your external hard drive in bios as the first boot hard disk, then you may be able to at least get Ubuntu booted.  If you can get Ubuntu booted, then you should be able to make a Super Grub Disk to restore your Windows mbr.
See this guide for reinstalling grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

See reply #49 in this thread, explaining how this is done:
[http://www.ubuntuforums.org/showthread.php?t=363306&page=5](http://www.ubuntuforums.org/showthread.php?t=363306&page=5)
the difference would be that you would change root to **(hd0,4)**, when you edit the entry to boot Ubuntu.

---

### Post by yerokleoh on 2007-02-28
Setting my external drive first gives me NTLDR missing, oh, and I used supergrub to get windows back in the mbr. So now I'm on Windows, but how do I boot ubuntu? Oh, and how do I even get back into GRUB now? I've tried restoring it the the MBR but no dice. Also SUPERGRUB lists my Ubuntu partition as (hd1,4) while GRUB thought it was (hd2,4) on the LiveCD

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> Setting my external drive first gives me NTLDR missing, oh, and I used supergrub to get windows back in the mbr. So now I'm on Windows, but how do I boot ubuntu?

Easiest way may be to set your external drive as the first hard drive booted in bios, then reinstall Ubuntu to your external drive...make sure to install grub to the mbr of the external drive, you should be able to type in **/dev/sdc**, when prompted where to install grub.  Selecting (hd0) "should" be correct, since you have your external drive 1st in the boot sequence.

If the methods I described in the second link I gave in my other reply didn't work, then reinstalling would probably be the best way to go...glad you were able to get Windows restored.

Might be a good idea to unplug your flash drive before you boot up to install Ubuntu.

---

### Post by yerokleoh on 2007-02-28
I think Grub got installed to the flash drive actually. Considering I see some files with broken text and one named boot with another named bootex.log

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> I think Grub got installed to the flash drive actually. Considering I see some files with broken text and one named boot with another named bootex.log

That's a distinct possiblity...you should still be able to reinstall grub to the external hd, using the live cd, but reinstalling Ubuntu may be your best bet.

---

### Post by yerokleoh on 2007-02-28
I'm trying, but when I try to reinstall (I have to use the validation.py fix because it says no root file system even though I have it mounted BTW) the progress bar of "Creating ext2 file system for sdc partition #5" just disappears.

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> I'm trying, but when I try to reinstall (I have to use the validation.py fix because it says no root file system even though I have it mounted BTW) the progress bar of "Creating ext2 file system for sdc partition #5" just disappears.

I don't know what's going on, but you should format the partition as ext3, rather than ext2.

If this doesn't work, you might be able to pre-format the partition with the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

it's an excellent partitioning tool for Linux & might be worth trying.

---

### Post by yerokleoh on 2007-02-28
Ok. All set to go. Where should I install GRUB, HD0?

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> Ok. All set to go. Where should I install GRUB, HD0?

If you have your external hd selected as the first booted hard drive, yes, it should be (hd0)...if you want to be sure & you installed to /dev/sdc5, then you should be able to type in **/dev/sdc** in the "block" where hd0 is entered.

---

### Post by yerokleoh on 2007-02-28
Great. So I re-installed and the Windows HD gives me the GRUB 1.5 Error 21 I think now, while the Ubuntu drive gives me Missing NLTRD. :(

---

### Post by confused57 on 2007-02-28
> **yerokleoh said:**
> Great. So I re-installed and the Windows HD gives me the GRUB 1.5 Error 21 I think now, while the Ubuntu drive gives me Missing NLTRD. :(

Does your internal Windows drive boot OK, if it is the first booted hard drive in bios?  If not, then you should restore the Windows mbr again with the Super Grub Disk...sorry to run you in circles, but once you get Windows to boot OK(maybe with the external drive disconnected?), then we can "attempt"  to get your external hd to boot Ubuntu without having to reinstall again.

Added:  Have you tried booting Ubuntu with the Super Grub Disk?

---

### Post by yerokleoh on 2007-02-28
I can restore the MBR fine, and windows does work now. Yes I did try booting Ubuntu with the Super GRUB disc. I selected the Ubuntu Partition in one of the options and I got a disc read error. I can do direct boot somehow and I get a wall of text which gets to something about scsi drivers and then stops. I'll just try the alternate install disk. :(

EDIT: Oh, and if you have google talk or something that would be nice. You seem to know what you're talking about and even if you don't it would be nice to have someone to just talk to in realtime to figure this out.

INTERESTING INFORMATION:
Super GRUB lists the external drive as (hd1,4) which kinda makes sense, while Ubuntu names it (hd2,4) when I run sudo grub. My internal drives are a two disk RAID by the way. Oh, and the Unbuntu installer detects the RAID drive as the two individual drives. So maybe Unbuntu thinks:
RAID HD(1) = (hd0,0) ; RAID HD(2) = (hd1,0) ; Maxtor Onetouch(My USB Drive) = (hd2,#) Partition 5 is Unbuntu and #6 is swap

---

### Post by yerokleoh on 2007-03-01
Sorry for double post but I'll try using partition magic to format the Unbuntu partition and swap space as ext3 and swap then just use the alternate install disk tomorrow. I have to get up and it's 11 PM here. So I'm going to bed and I'll try again tomorrow.

---

### Post by confused57 on 2007-03-01
> **yerokleoh said:**
> Sorry for double post but I'll try using partition magic to format the Unbuntu partition and swap space as ext3 and swap then just use the alternate install disk tomorrow. I have to get up and it's 11 PM here. So I'm going to bed and I'll try again tomorrow.

I've had "some" success helping other people install Ubuntu to an external hd, probably by accident & hit-or-miss..LOL...the alternate install cd has the advantage of definitely being able to designate where grub is installed... on the last step, which is to install grub, you can select "no" when prompted to install grub to (hd0)...then you get a screen where you can type in where you want grub installed...for example, if during the install your root partition is /dev/sdc5, you can type in **/dev/sdc**, which is the mbr for your external drive.

If you want some excellent screenshots of the alternate installer:
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

I wouldn't use Partition Magic to pre-format your partitions for Ubuntu, instead use the gparted live cd that I mentioned in an earlier reply:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by yerokleoh on 2007-03-01
My external drive is NTFS. Can gparted partition/resize ntfs?
Also, what's wrong with Partition Magic 8 Pro?

---

### Post by confused57 on 2007-03-01
> **yerokleoh said:**
> My external drive is NTFS. Can gparted partition/resize ntfs?
Also, what's wrong with Partition Magic 8 Pro?
Good questions...the gparted live cd doesn't have a problem resizing NTFS, however, Partition Magic would probably do a better job of just resizing.  I've read of many people having problems when using Partition Magic to pre-format ext3 partitions to install Linux on...the partitioner on the alternate install cd does a great job and you may not need to pre-format...if you do, then I'd recommend using the gparted live cd...good luck with your install.

---

### Post by yerokleoh on 2007-03-01
I'm pretty sure I tried gparted. It ran great but wouldn't let me actually change anything. I'll just try the alternate installer's partitioner.

---

### Post by yerokleoh on 2007-03-01
OH JOY, OH HAPPY DAY! I am now the proud runner of Ubuntu 6.10 Edgy Eft on the 14 gig ext3 partition of my external drive. Thanks to the alternate install disk, which, by the way, is a GODSEND! :)

---

### Post by confused57 on 2007-03-01
> **yerokleoh said:**
> OH JOY, OH HAPPY DAY! I am now the proud runner of Ubuntu 6.10 Edgy Eft on the 14 gig ext3 partition of my external drive. Thanks to the alternate install disk, which, by the way, is a GODSEND! :)
That's what I like to hear, another success story...I've never used the live cd installer, since I've had so much success with the alternate cd...goes back to Breezy, which only had the alternate install cd(no live cd install)...glad it worked.

Sorry I couldn't help you any, but at least the alternate cd saved the day.

---

