---
title: "Dual boot, Windows 7"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by Danny_Dib on 2014-06-22
please help me...
i have a dual core 64 bit setup with 4gb ram and 2 300gb HDD one is a backup drive for windows 7...
i currently have windows 7 installed and would wish to dual boot ubuntu with windows 7 and set bootloader to windows 7 which i know how to do using the dvds..
ubuntu does not recognise my hard drives i think its a raid fault upon investigation please someone help me... :(

oh and i forgot to mention that i can view the partitions only by using the gparted application on the live user session but not with the installation!!!

---

### Post by fantab on 2014-06-22
Is that a laptop? If yes which one?
First of all lets confirm that it is a RAID issue...
In your BIOS setup look for SATA Mode and tell us what is it set to: AHCI, IDE or RAID.
If you have a Intel Mobo then also look for 'fastboot', if present and enabled then disable it.

If you can boot with Ubuntu DVD/USB and 'try Ubuntu (without installing) then open Terminal and post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Danny_Dib on 2014-06-22
For a PC not laptop..
set in IDE and fast book enabled...
tried sudo apt-get remove dmraid 
returned good as I could see 1 disk 0,0,0 told it to install alongside windows 7
but halted with some error and would not continue...
im so confused I just want to install on the first hard drive without deleting data on the second hard drive
as my windows backups are on that....

please help :(

---

### Post by Mark Phelps on 2014-06-22
To prevent any changes to the Backup drive, you should have only the Target drive connected when you try to do the installation.

To see what's on your target drive, boot into Ubuntu, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).

---

### Post by Danny_Dib on 2014-06-22
You mean open the PC case and disconnect the back up drive?

---

### Post by oldfred on 2014-06-22
If you really had RAID running you were not backing up to another physical drive, but what Windows may call a d: drive which probably was just another partition.
With RAID your two physical drives are seen as one physical drive with data mirrored to second. Or if a new UEFI system with Intel SRT the RAID sets up a fast boot partition that is really just hibernation.

Would have been a lot better to post the commands fantab requested before removing RAID a now we are not sure where you are at??

Is this a newer UEFI based system?

---

### Post by Danny_Dib on 2014-06-22
Forgive my stupid confusion... I have taken snapshots I'll upload them shortly.. As I mention I have 2 300gb sata hard drives one has windows 7 installed and the other us merely a place to set up back up images... Ubuntu doesn't show the partitions but the hard disks only... If I use sudo apt-get remove dmraid then go to gparted I see everything as I should... But in the installation area I just see the 2 volumes only... I've gone ahead and formatted the partition with windows on it so it's clean!!!

---

### Post by Danny_Dib on 2014-06-22
[IMG][IMG]http://i60.tinypic.com/2e6elnd.jpg[/IMG][/IMG]

---

### Post by dylan0005 on 2014-06-22
Is beacause you have to configurate RAID in ubuntu(also) so the OS can recognise the parition system. 
Whatever, installing another OS with windows 7 is like having a headache!

---

### Post by oldfred on 2014-06-22
With RAID you only have one logical drive. The second drive is imaged depending on type of RAID to other drive.
Understand with Linux a drive is a physical device.
In Windows a drive may be a physical hard disk, but often is just a partition where it still calls it drive d:. So I think you have Windows in a partition, your backup in another partition and that is mirrored to your second drive.

The desktop installer is not configured for RAID installs. That was available last with the alternative installer in 12.04 and is available with the server installer. You can add the RAID drivers to correctly see the partitions with the desktop version.

Some users with systems with RAID, break RAID, keep Windows on one drive and install Ubuntu on the other drive. Then you can backup Windows data to a NTFS partition on the Ubuntu drive and backup Ubuntu data to a Linux formatted partition on the Windows drive. That is not automatic backup, but RAID is not backup anyway.

       [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup

[/URL]
 EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

### Post by Danny_Dib on 2014-06-23
Is it not just possible to install ubuntu with windows 7 as a dual boot? How do I fix this?

---

### Post by oldfred on 2014-06-23
I do not know RAID, but BIOS RAID is called fakeRAID also:

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

