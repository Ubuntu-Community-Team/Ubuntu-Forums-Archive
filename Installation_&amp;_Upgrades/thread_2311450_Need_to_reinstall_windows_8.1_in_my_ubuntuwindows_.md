---
title: "Need to reinstall windows 8.1 in my ubuntu/windows dual boot"
date: 2016-01-27
forum: Installation &amp; Upgrades
---

### Post by Decemius on 2016-01-27
Hello,

I need to reinstall windows 8.1 in my ubuntu/windows dual boot. Do  I need to remove Ubuntu first, then windows, clean install windows then ubuntu again? If so, how can I ensure that Ubuntu installs on my SSD? I had a lot of trouble getting it to work on this build. Sorry if this is a basic question, could only find guides on how to dual boot not how to reinstall a OS in a dual boot. Thanks!

---

### Post by mastablasta on 2016-01-27
reinstall Windows? strange solution, but ok i guess you messed up the OS completelly. i ahven't done that since i messed up win98 in the 90's by manually deleting some important system files. it seemed a good idea at the time... :)

reinstall Windows to it's disk partition. after you are done use Ubuntu live cd and the boot repair tool to reinstall grub (you can also do it in terminal If you know how) . that's it. ubuntu should stay as it is. 

if you are afraid of loosing any data then do a backup of the OS first (image backup using clonezilla or redo backup for example).

---

### Post by oldfred on 2016-01-27
Is system UEFI or BIOS? And how is drive partitioned?
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
How you boot install media is how it installs.

For Windows 8 or later, you do want to make sure the fast start up or always on hibernation is off whether UEFI or BIOS boot.

What system is it?
Motherboard, video card/chip?

---

### Post by grahammechanical on 2016-01-27
In the situation where you need to create a partition for Windows I suggest that you create space at the beginning of the drive. It may not be absolutely necessary to put Windows at the start of the drive but it is what I would do.

Use Gparted from a live Ubuntu session to resize/move any Linux partition. And the in the unallocated space use the Windows install disk to create the windows partition and format it. Then the Windows installer will see the partition and allow you to install Windows into it. I based this on my one experience of installing Windows 8 preview edition.

Oh, the installation process of installing Windows will most definitely over-write the Linux boot loader with the Windows boot loader and it will do that for every drive connected and not just the drive Windows is being installed. Again I am speaking from experience.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards

---

### Post by Decemius on 2016-01-28
Thanks for the responses. Windows 8.1 is UEFI. Fast boot was always turned off here because otherwise I couldn't access my hdd when on Linux. Windows currently has 177gb and Ubuntu Linux has 46gb. Windows has a ntfs partition while Linux has a ext4. If it matters, /boot/efi is a fat32. I made a screenshot: [http://i.imgur.com/7Bo5EaA.png](http://i.imgur.com/7Bo5EaA.png)


The system I use:
-ASUS Z97-PRO motherboard
-I5-4670K processor
-R9 290 graphics card
-Samsung 850EVO 250gb (SSD) 
-WD 1TB hdd

Grahammechanical, before I take your steps, do I need to remove windows first? What about using a USB stick instead of a disk? If I understand correctly:

1. Remove Windows
2. Create empty partition
Should it be unallocated or empty? Never quite understood the difference.
3. Restart Ubuntu, boot from USB
4. Install Windows

End result being that I am left with just a Windows install and having to do a new dual boot? Or could I repair Linux as Mastablasta states? I am sorry if I ask much, haven't had too much experience with installing operating systems. Much appreciated.

---

### Post by oldfred on 2016-01-28
Best to always have good backups.

Do not know about UEFI reinstall of Windows.
But be sure to boot installer in UEFI mode, or else it will convert entire drive to MBR(msdos) for BIOS boot.

And Windows has to have the 128MB system reserved just before main NTFS partition.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

I have seen this for Windows 10.
 Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

