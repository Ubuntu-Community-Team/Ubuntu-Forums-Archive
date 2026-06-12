---
title: "Installation on a 2nd drive alongside XP"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by Gazzamo on 2014-03-06
Hi,
On the face of it, quite simple, but I haven't yet managed it.

I've a fairly old setup with XP running, which I don't want to touch. It runs amongst other ancient stuff, an old Canon slide scanner that I'm still using. XP sits on the Primary Master drive. I've a second drive, the Primary Slave which I've partitioned, intending to use the first partition for Windows data, and install Linux on the second.

When I first tried to install, I was given the option of installing on the drive with Windows on it, or on an external USB drive which I had neglected to disconnect before I started the installation. No mention of the drive which I had intended to use. I disconnected the USB drive and tried again. This time the only offer from the installation was to partition the drive with Windows on it. I then did a bit of googling and came upon an article that said there should not be a partition created for Linux, but the space should be unallocated. I deleted the second partition on the second drive and tried the installation again, with exactly the same result.

I then tried other distributions, openSUSE and Mint Linux, with exactly the same results. I even tried disconnecting the Windows drive to try and force the installation on to the second drive. No luck!

During one of the later attempts I ran bootinfoscript and mailed myself the results, which I'm inserting here:-

```

                  Boot Info Script 0.61      [1 April 2012]

============================= Boot Info Summary: ===============================
 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS
sdb1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sdb2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *             63   234,420,479   234,420,417   7 NTFS / exFAT / HPFS

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1                  63   143,492,579   143,492,517   7 NTFS / exFAT / HPFS
/dev/sdb2         143,492,580   321,669,494   178,176,915   7 NTFS / exFAT / HPFS

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        8AE42EB7E42EA583                       ntfs       
/dev/sdb1        369832339831F1CB                       ntfs       DeskstarD
/dev/sdb2        B418CE4F18CE1072                       ntfs       DeskstarE
/dev/sr0                                                iso9660    Linux Mint 16 Cinnamon 32-bit
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
=============================== StdErr Messages: ===============================
  No volume groups found


```

If anyone can throw some light on to this matter, I would be extremely grateful.

Many thanks

---

### Post by ajgreeny on 2014-03-06
You don't appear to have any unallocated space on either disk, and the second partition on sdb is still ntfs.

How did you delete, or think you had deleted, the partition before your last attempt to install?

---

### Post by Gazzamo on 2014-03-06
> **ajgreeny said:**
> You don't appear to have any unallocated space on either disk, and the second partition on sdb is still ntfs.

How did you delete, or think you had deleted, the partition before your last attempt to install?

Hi,

After the attempt to install with an unallocated area on sdb failed with the same symptons as before, I reasoned that the unallocated space thing was a red herring and reinstated the partition I had deleted.

---

### Post by Mark Phelps on 2014-03-06
> intending to use the first partition for Windows data, and install Linux on the second.

Sounds like you're trying to install Ubuntu to a Windows filesystem partition -- which you can't do.

You need to have unallocated space, so that the installer can create the Linux filesystem partitions needed.

---

### Post by Gazzamo on 2014-03-06
> **Mark Phelps said:**
> Sounds like you're trying to install Ubuntu to a Windows filesystem partition -- which you can't do.

You need to have unallocated space, so that the installer can create the Linux filesystem partitions needed.

Hi,

As I said in the starter, at one point I deleted the second partition on the second drive leaving an unallocated space of about 90 Gb. The installer still didn't offer to install on the second drive. What I don't understand about this unallocated/partition thing is that at each attempt to install (apart from my last try, where I disconnected the first drive), the installer has offered to shrink the only partition on the first drive and install in a newly created partition in the space created by shrinking the existing NTFS partition. Where does that leave the proposition that it is not possible to install into a Windows filesystem partition? Or am I missing something?

---

### Post by oldfred on 2014-03-06
Linux uses Linux formatted partitions like ext4, not Windows formats like NTFS. Windows does not support ownership & permissions which are part of why Linux has better security.

You mention slave drive. Is system so old that you still jumper IDE hard drives as master/slave and can only boot from sda? 
Or a somewhat newer PATA drive with cable select that lets you select boot drive. But then you also have to have to correct 80 conductor cable & jumpers on drives.

 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Gazzamo on 2014-03-06
> **oldfred said:**
> Linux uses Linux formatted partitions like ext4, not Windows formats like NTFS. Windows does not support ownership & permissions which are part of why Linux has better security.

You mention slave drive. Is system so old that you still jumper IDE hard drives as master/slave and can only boot from sda? 
Or a somewhat newer PATA drive with cable select that lets you select boot drive. But then you also have to have to correct 80 conductor cable & jumpers on drives.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Hi,

This could be it!. The system is old, the disks are ATA/IDE, it has ribbon cable which runs from the IDE1 on the motherboard to the 2 disks, and the 2 disks have jumpers which are set such that the windows disk (C/sda) is the master, and the 2nd (D/E/sdb)which I am trying to install to is set to slave. Does this mean that the system will only boot from the master? I thought that somewhere on the first disk there could be an option which would cause the system to boot from disk 2 partition 2, but I have to confess that was based on supposition. What threw me was the fact that I could mount and write to both 2nd drive partitions from Linux running off the DVD drive.

Just to be clear on this; are you saying that on my system, I can only install Linux on the master disk, or could I have some sort of boot stub on the first disk which would start Linux on the 2nd slave disk?

Thanks for the info

---

### Post by oldfred on 2014-03-06
Not sure but it has been a long time since I had IDE drives.  I really really hated those tiny jumpers. Not sure if your BIOS would let you boot from slave or not. I did once try to use a 40 conductor (new from CD) connector with my cable select and that caused issues. In effect I was back to only master/slave even though system was new enough for cable select. As soon as SATA drives were only $10 more than PATA I built my new system (2006) with only SATA devices.

You can always install grub2's boot loader to sda and boot sdb. You may need boot partition on sda? I would make sure I had working Windows XP CD as repair, just in case I needed to convert MBR back to Windows.
Boot-Repair can also add a Windows type boot loader, but can only make minor Windows fixes.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by mastablasta on 2014-03-07
in theory (but make sure you have winXP repair cd to repair boot loader if needed) you could do like mentioned above. select manual install (something else option). create linux parittion on /sdb named / (with ext4 format) and /swap (with swap format). make sure you put the grub on /sda 

then boot should go like so:

BIOS->GRUB on sda (first disk)->linux on sdb (second disk)
BIOS->GRUB on sda -> windows on sda

why i think it should work - because by installing grub you can use it to boot from USB even if BIOS doens't support it. it's a more advanced boot manager.&#382;

another option but i am not sure if this would work or if it realyl matters is maybe to create /boot partition on sda. but i would first try the grub option.

---

### Post by Gazzamo on 2014-03-07
> **mastablasta said:**
> in theory (but make sure you have winXP repair cd to repair boot loader if needed) you could do like mentioned above. select manual install (something else option). create linux parittion on /sdb named / (with ext4 format) and /swap (with swap format). make sure you put the grub on /sda 

then boot should go like so:

BIOS->GRUB on sda (first disk)->linux on sdb (second disk)
BIOS->GRUB on sda -> windows on sda

why i think it should work - because by installing grub you can use it to boot from USB even if BIOS doens't support it. it's a more advanced boot manager.ž

another option but i am not sure if this would work or if it realyl matters is maybe to create /boot partition on sda. but i would first try the grub option.

Hi

This is how I imagined the new setup was going to work, although I was extremely sketchy on detail. But the problem is that I am only being offered sda when it comes to the point in the installation where I choose the device. As iI said in the first post, the first time I tried to install, I had an external USB drive hooked up; this was offered by the installation as a possible repository for the install, but at no time has the second internal drive appeared. Perhaps it's just not possible, unless there is a method of manually installing Linux on a given drive.

Thanks

---

### Post by oldfred on 2014-03-07
Does BIOS show drive correctly?
And are jumpers and cable correct for slave drive? If not correct, it will not be seen correctly.

---

### Post by Gazzamo on 2014-03-07
> **oldfred said:**
> Does BIOS show drive correctly?
And are jumpers and cable correct for slave drive? If not correct, it will not be seen correctly.


Hi

Since the last post, I've changed the Master/Slave setup to Cable Select. The disks had been connected with a Cable Select cable. After a couple of false starts where I had to clear CMOS and then reconfigure one of the jumpers (I had assumed 16 heads on the drive, and it should have been 15), XP rebooted and was running as well as before the change. Bios can see both drives, and I have actually written to both partitions on what would be drive sdb on Linux from Linux running off the installation DVD. I'm beginning to think that there is no solution, but on the face of it, it seems a reasonable thing to attempt to do.

BTW Once I had reconfigured the drives I tried the installation again with the same result; no trace of sdb when the option was presented.

Thanks

---

### Post by Gazzamo on 2014-03-10
Hi,
In the end it turned out to be something connected to raid. I got the Mint Linux installation to offer sdb by entering the following in a terminal window:-
```

sudo apt-get -y remove dmraid

```
I managed to find this after hours of trawling through threads in various forums. I suspect that the drive in question when mistakenly plugged into a raid IDE connector on the motherboard was somehow flagged up as  a raid drive, and so was not offered as an installation point.

The installation fell over, but at least it had started, and now I have openSUSE installed and the machine happily dual boots XP and Linux.

Hurrah!!

---

