---
title: "Lost Grub totally installing 10.04 beta...please help"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gordong11 on 2010-03-26
Hi,

I just installed 10.04, and when i was done installed, i re-booted and got grub rescue error. I loaded the 9.04 liveCD and ran 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006752f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87040138+   7  HPFS/NTFS
/dev/sda2           18139       18241      827347+   5  Extended
/dev/sda3   *       13387       18138    38170440   83  Linux
/dev/sda4           10837       13386    20482875    7  HPFS/NTFS
/dev/sda5           18140       18241      819315   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Disk identifier: 0x6f20736b

Disk /dev/sdb doesn't contain a valid partition table
________________________________________________________________________

Can someone please help me re-store Grub? Version 1 or 2 it doesnt matter to me, if 10.04 doesnt matter which.Thanks

Gord

---

### Post by gordong11 on 2010-03-26
I am currently downloading 10.04 Live CD, since i am pretty sure i'll need grub2 files.

---

### Post by overdrank on 2010-03-26
Moved to Lucid Lynx Testing and Discussion

---

### Post by gordong11 on 2010-03-26
Solved it by doing the following....(taken from this link: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708))



1. Burn 10.04 beta 1 live cd
2. opened terminal

note next steps: (X= the Device number of your Ubuntu Drive )

sudo mkdir /media/sdaX 
sudo mount /dev/sdaX /media/sdaX

then 

sudo grub-install --root-directory=/media/sdaX /dev/sda

---

### Post by wkulecz on 2010-03-26
> note next steps: (X= the Device number of your Ubuntu Drive )

This is where the 9.10 and 10.04Beta installers are falling down.  They seem to ignore the BIOS boot order setting and called my SATA /dev/sda and my IDE drives sdb & sdc.

IF you recognize the issue, (I only did from my experience with 9.10 on the same machine) the "advanced" button on step 8 of 8 page lets you change where the boot loader will be installed to match you BIOS.  But be aware the drop down selection doesn't work, you have to change it manually by typing into the control.

---

### Post by dino99 on 2010-03-26
nothing new since Karmic, go to system -- admin -- bootupmanager and make your choice.

---

