---
title: "Ubuntu installer: &quot;This computer has no detected operating systems.&quot;"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by riomhadoir on 2013-11-08
Hi there. Sorry for bothing everyone, I always feel a bit guilty signing up somewhere just to ask for help. Anyway I'm attempting to dual boot Windows 7 (64-bit) and Ubuntu.

I downloaded the 64-bit version of Ubuntu 13.10 from the official site and created a bootable flash drive using the Universal USB Installer from pendrivelinux.com

I attemtped to run the installer from the drive but the installer told me that "This computer currently has no detected operating systems" and the default option is "Erase disk and install Ubuntu". (screenshot should be attached)

Selecting "Something else" as my installtion option brings me to the partiion screen (other attachment) which appears to say the entire hard disk is free space.

I don't want to destroy my Windows installation so I quit the installer at that point.





I also tried my luck with using WUBI. I downloaded Ubuntu 12.04 and installed it through WUBI. It seemed to go fine with no complaints. When I tried actually booting Ubuntu then I got a black screen with only the output

```
Try (hd0,0) :  NTFS5 :  No wubildr
Try (hd0,1) :  NTFS5 :  Welcome to GRUB!
```

With "Welcome to GRUB!" highlighted. I thought it was a bit odd but left it alone. After a minute Ubuntu itself starting booting up. It brought me to an empty destop with no sidebar. A error appeared on the screen saying "No root file system is defined. Please correct this from the partitioning menu." When I dismissed the error it would just pop back up again.

I shut down the computer again, booted back to Windows and uninstalled Ubuntu through WUBI.





I then went back to my flash drive and this time decided to boot Ubuntu straight from it. It works fine and I am in fact currently typing in Ubuntu. I went to the installer again but it's still the exact same way; unable to detect my Windows installation.




So I've said quite a lot but it probably doesn't contain all that much useful information to diagnose the problem. Please inform me of any steps I can take to provide more information to figure out what's wrong and *please* tell me anything you think might allow Ubuntu to properly detect my Windows installtion and install successfully without destroying it.

Thanks at the very least for reading.




Edit: The issue has been resolved. The partition was MBR but there was leftover GPT data on the disc (probably from the time my brother installed Mac OSX on the machine) which caused the Ubuntu installer (and then GParter) to be confused. Using FixParts ([http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)) I was able to delete the GPT data and after that the installer was perfectly able to detect my Windows installation. Ubuntu in installing as I type.

Thanks for help.

---

### Post by westie457 on 2013-11-08
Hello riomhadoir, welcome to UF.

Can you boot your USB into 'Try' mode please. Once that is running start Gparted and post a screenshot, also do the same with Disks. For good measure open a terminal - Ctrl+Alt+T is the quick way - and post the output of this command ```
sudo fdisk -l
``` The l is a lower-case L.

More help will follow.

---

### Post by riomhadoir on 2013-11-09
Thanks. I tried to respond last night login.ubuntu.com was apparently down and I couldn't log in.


GParted gives a big error as soon as I run it:

[ATTACH=CONFIG]247702[/ATTACH]

I honestly didn't know what kind of partition table I have. Clicking either yes or no results in pretty much the exact same screen. The only difference is that if I click yes there's no red warning sign next to "unallocated"
[ATTACH=CONFIG]247703[/ATTACH]



Disks on the other hand says my partitioning is MBR. I guess that's the issue? The installer and GParted are trying to read it as GPT when it's actually MBR? It also actually shows up the different sections of the hard disk instead of just saying it's all unallocated space. Here's what it shows with all three partitions of the HD highlighted in turn:

[ATTACH=CONFIG]247704[/ATTACH]

[ATTACH=CONFIG]247705[/ATTACH]

[ATTACH=CONFIG]247706[/ATTACH]









And here's the terminal output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1732422f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07377a60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7822079     3911008+   b  W95 FAT32
ubuntu@ubuntu:~$ 
```

---

### Post by fantab on 2013-11-09
To Install ubuntu you need create/make some space for it, otherwise Ubuntu won't install.

Post the output of this command:
```
sudo parted -l
```

---

### Post by riomhadoir on 2013-11-09
> **fantab said:**
> To Install ubuntu you need create/make some space for it, otherwise Ubuntu won't install.

Post the output of this command:
```
sudo parted -l
```

Is this just the terminal version of the GParted I already did? Here's the output.

```
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? n                                                                 

Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 4006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4005MB  4005MB  primary  fat32        boot
```

---

### Post by grahammechanical on 2013-11-09
I cannot speak from experience on this subject. I pass on some information that I have learned from reading posts on this subject.

1) Use Windows tools to defrag the hard disk. do this at least twice.
2) Use Windows tools to create partitions for Ubuntu.
3) As you do steps 1 and 2 check to see if Windows is still loading.
4) Know how to restore Windows.

As far as I know the Ubuntu installer has been able to deal with GPT for a few years. So, GPT should not be such a problem. Have you looked at the disk partitioning using a Windows Utility? What would that show as to your partitions? Microsoft used to use something called Dynamic Disks as a way to get around the 4 primary partition limit. As Dynamic disks are a proprietary format Linux utilities cannot read them. Can you post a screen shot of your partitioning scheme as seen  by a Windows utility?

Regards.

Edit: This old thread might interest you

[http://ubuntuforums.org/archive/index.php/t-1947497.html](http://ubuntuforums.org/archive/index.php/t-1947497.html)

---

### Post by Bucky Ball on 2013-11-09
Welcome.

No, don't use Window to create partitions for Ubuntu. It can't create any partitions Ubuntu can use so you are creating partitions to be erased. Linux uses EXT* to install to. Windows doesn't know what they are and can't create them.

Do whatever you need to do to your Win partition while in Windows (shrink possibly) and make sure you have left free space, no partitions, just free space. Ubuntu will create its own partitions during install (automagically if you go that way or you can create and set them up how you like by choosing 'Something Else' at partitioning. If you do this you will see the Win partition in there (not that you have yet) and just don't touch that. It will be an NTFS partition.

Yes, defrag the Win partition with Win software before shrinking the Win partition. Three or four times is the rule of thumb. (PS: The Win software is not the most efficient at doing this which is why you should defrag a few times.)

Don't use Wubi. It is being phased out and you won't get much support here if anything goes wrong goes very few people know much about it. It is/was intended to try Ubuntu before installing, but you can do that from the install disk.

* Rule of thumb:
When resizing the Windows OS partitions - use Windows.
When resizing Linux partitions - use Linux.

> **riomhadoir said:**
> Hi there. Sorry for bothing everyone, I always feel a bit guilty signing up somewhere just to ask for help.

No bother, don't feel guilty, ask away and we'll help however we can. ;)

---

### Post by riomhadoir on 2013-11-09
The issue has been resolved. As the FixParts tutorial page put it

[COLOR=#000000][FONT=Times New Roman]"[GPT] data can remain behind on a disk if it was previously used on a Macintosh or in some other ways, then re-used as a conventional MBR disk. Although such leftover data should not technically be a problem because the GPT specification clearly states that such disks are [/FONT][/COLOR]*not*[COLOR=#000000][FONT=Times New Roman] GPT disks and should therefore be treated as MBR disks, some utilities can be confused by the presence of both MBR and GPT data."
[/FONT][/COLOR]
Using FixParts ([http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)) I was able to remove the GPT data and now everything is installing smoothly.

---

### Post by fantab on 2013-11-09
GPT stores a backup partition table at the end of the disk. When GPT disks are converted to 'msdos' this back GPT table is not removed and it confuses the Installer. FIXPARTS fixes it. I am glad you've found fixparts and fixed the issue.

---

### Post by Bucky Ball on 2013-11-09
Good news. Now you have something to pass on! ;)

---

