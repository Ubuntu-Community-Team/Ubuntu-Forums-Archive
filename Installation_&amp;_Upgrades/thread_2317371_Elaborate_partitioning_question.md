---
title: "Elaborate partitioning question"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by david503 on 2016-03-15
Alright, long time linux admin here, new to ubuntu (desktop) 

Here's the situation:


I'm running windows 8.1 pro on one drive.


I also have an external 500gb drive.


I want to partition the external drive to be able to run ubuntu but *also* be used as a windows time machine backup drive. (Oh wait, what's the ms equivalent of time machine? whatever.)


So, one partition of drive has to be able to be seen by windows.  


I want the other partition to be bootable into ubuntu.


I don't want to use a boot loader. My bootloader will simply be choosing one or the other drives in bios to boot from.  No bootloader.


So question is: 


Can I put the 50 gig ubuntu partition at the end of the disk?  Or does it have to be at the beginning in order to be bootable.  Windows apparently has a problem even assinging a drive letter to a disk if it has the bootable flag at the beginning partion.  I just learned that.


So can I put ubuntu at the end?  Will it be able to boot if I select it in bios?  Or will bios try to boot but it won't see that the drive is bootable.


(And no, putting a little /boot partition at the beginning would be just as bad, since the first parition would be bootable and windows doesn't like that, right. And, again, I don't want a boodloader.)


thanks,


d

---

### Post by kc1di on 2016-03-16
Hi david503 and Welcome to Ubuntu, 

What you propose is do able, Ubuntu won't care where it's drive is at.  you will how ever have to install grub boot loader on the drive in question because it's needed to boot Ubuntu.  The default is to place it in the MBR but it can boot Ubuntu from any partition.  so you'll have to be careful not to allow it to install in the MBR. 

note the information on [this page]("https://help.ubuntu.com/community/Grub2/Installing") concerning bios/uefi and grub 2 
[this page]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition") may also be of help to you.
and this older [thread]("http://ubuntuforums.org/showthread.php?t=1417268") may be of help also. good luck.

---

### Post by Bucky Ball on 2016-03-16
Make the Time Machine backup partition NTFS and put it where you like. Doesn't have much to do with Ubuntu. Different partition.

---

### Post by oldfred on 2016-03-16
Is Windows UEFI or BIOS?
You really want Ubuntu installed in same boot mode, UEFI or BIOS.

If UEFI, with Ubuntu, grub will automatically be installed to ESP - efi system partition on sda. But you can just copy files to sdb drive after install.

With flash drives Windows only sees first partition. Not sure how it knows but it seems to work ok with hard drives.
Only some very old BIOS with IDE would only boot from first 137GB of a drive (even older less). Issue also applies to some USB boot. You may just have to try. If UEFI have not seen an issue.

UEFI suggests first partition be ESP, although Windows often have it second or even third partition but still near beginning of drive. I would not have an ESP at end of new multi-TB drive, but in your case should be ok wherever.

If UEFI, you also need gpt partitioning. Even if BIOS you can use gpt as only Windows XP would not read gpt. Only 64 bit Windows 7 or later can boot from gpt in UEFI mode, but you cannot boot external drive with Windows.

---

