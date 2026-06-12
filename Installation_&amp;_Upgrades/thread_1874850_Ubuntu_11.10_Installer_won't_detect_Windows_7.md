---
title: "Ubuntu 11.10 Installer won't detect Windows 7"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by nautica17 on 2011-11-03
I have a 1TB hard drive with Windows 7 installed on it. When I run the Ubuntu installer, it says it didn't detect Windows or any other OS. In Windows, I shrunk my C volume down and freed up about 200GB (which is unallocated at the moment). This usually works for me, and I've done this since 10.04 whenever I dual boot. 

fdisk displays the two partitions that Windows 7 runs on. It doesn't show my unallocated 200GB though. I looked at gparted out of curiousity (running live right now) and it shows that I have an empty 1TB hard drive. So something somewhere is not reading something properly. I simply just want Ubuntu to automatically install side-by-side with 7. 

fdisk printout: 
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6eb4065

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1534089215   766941184    7  HPFS/NTFS/exFAT

```

---

### Post by Mark Phelps on 2011-11-04
Messing around with partitioning runs the risk of corrupting the Win7 filesystem, so before you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

What do you see when you open the Disk Utility in Ubuntu?  Is the free space shown there?

---

### Post by Hakunka-Matata on 2011-11-04
please post output of ```
sudo sfdisk -luS && sudo fdisk -l
```

---

### Post by LinuxFan999 on 2011-11-04
What brand is your hard drive? How old is it?

---

### Post by nautica17 on 2011-11-04
Okay so to answer all the questions.. 

The hard drive is a Hitachi 1TB 7200RPM SATA, bought it new 2 years ago. Have never had a single problem with it, but I've never installed anything but Windows on it. 

Ubuntu disk utility shows my Windows partitions, and my 200GB of unallocated space that I set aside in Windows. (It actually shows 215GB which is sort of weird because I set exactly 200GB). 

The way I created space on my hard drive was using Windows very own utility for doing these things as that is the safest way to do so. This has always worked for me without a hitch, so it doesn't look like Windows was corrupted or anything (but then again you never know). And if anything goes wrong I have a back up disk, or I use EasyBCD to repair MBR. 


sudo sfdisk -luS && sudo fdisk -l 
```

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS/exFAT
/dev/sda2        206848 1534089215 1533882368   7  HPFS/NTFS/exFAT
        start: (c,h,s) expected (12,223,20) found (13,163,20)
        end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6eb4065

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1534089215   766941184    7  HPFS/NTFS/exFAT

```

---

### Post by nautica17 on 2011-11-04
Here's an update on my situation. I tried a few older versions of Ubuntu and I get the same issue. I'm guessing my problem is one of two things. Either a) the hard drive is the problem, or b) Windows or the MBR has an issue. 

Does anybody have any recommendations as to what I should do at this point?

Edit: I just reinstalled MBR, and that didn't help.

---

### Post by darkod on 2011-11-04
I think your issue is that the disk has a GPT partition table and not msdos (the old type).
On top of that, in the windows disk management check if it says the disk is Basic or Dynamic. It wouldn't install easy on dynamic (if it would install at all).

---

### Post by nautica17 on 2011-11-04
> **darkod said:**
> I think your issue is that the disk has a GPT partition table and not msdos (the old type).
On top of that, in the windows disk management check if it says the disk is Basic or Dynamic. It wouldn't install easy on dynamic (if it would install at all).

In Windows, it says I'm using basic. I've dual booted Ubuntu with 7 and Vista many times in the past though, and I think in every instance I was using a GPT partition table since that is I believe the default nowadays. 

I'm wondering if maybe there is a hardware issue. I built this computer 2 years ago, so none of the parts are legacy or anything like that. I'm gonna look in BIOS and see if there is something in there maybe.

Edit: After googling a bit, I think you're right, the GPT is the issue. And it doesn't look like I can convert it back to the old type without data loss.

---

### Post by Hakunka-Matata on 2011-11-04
install gdisk if you don't yet have it.  It will convert your guid partition table back to mbr.  gdisk is a command line tool, do a "man gdisk", to see how to use it.

---

### Post by nautica17 on 2011-11-04
> **Hakunka-Matata said:**
> install gdisk if you don't yet have it.  It will convert your guid partition table back to mbr.  gdisk is a command line tool, do a "man gdisk", to see how to use it.

Cool, I'll definitely look at that!

---

### Post by sjalv on 2011-11-06
> 
[QUOTE]Quote:
Originally Posted by Hakunka-Matata View Post
install gdisk if you don't yet have it. It will convert your guid partition table back to mbr. gdisk is a command line tool, do a "man gdisk", to see how to use it.
Cool, I'll definitely look at that!
 
[/QUOTE]
Did this work out for you? I ran into the same problem, but haven't yet had the nerve to mess around with gdisk.

In my case the output of sudo sfdisk -luS && sudo fdisk -l is

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS/exFAT
/dev/sda2        206848 1024002047 1023795200   7  HPFS/NTFS/exFAT
/dev/sda3     1024002048 3825106943 2801104896   7  HPFS/NTFS/exFAT
/dev/sda4     3825106944 3907026943   81920000   f  W95 Ext'd (LBA)
/dev/sda5     3825108992 3907026943   81917952   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ac35653

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1024002047   511897600    7  HPFS/NTFS/exFAT
/dev/sda3      1024002048  3825106943  1400552448    7  HPFS/NTFS/exFAT
/dev/sda4      3825106944  3907026943    40960000    f  W95 Ext'd (LBA)
/dev/sda5      3825108992  3907026943    40958976    7  HPFS/NTFS/exFAT

```

---

### Post by Hakunka-Matata on 2011-11-06
> **sjalv said:**
> Did this work out for you? I ran into the same problem, but haven't yet had the nerve to mess around with gdisk.

In my case the output of sudo sfdisk -luS && sudo fdisk -l is

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS/exFAT
/dev/sda2        206848 1024002047 1023795200   7  HPFS/NTFS/exFAT
/dev/sda3     1024002048 3825106943 2801104896   7  HPFS/NTFS/exFAT
/dev/sda4     3825106944 3907026943   81920000   f  W95 Ext'd (LBA)
/dev/sda5     3825108992 3907026943   81917952   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ac35653

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1024002047   511897600    7  HPFS/NTFS/exFAT
/dev/sda3      1024002048  3825106943  1400552448    7  HPFS/NTFS/exFAT
/dev/sda4      3825106944  3907026943    40960000    f  W95 Ext'd (LBA)
/dev/sda5      3825108992  3907026943    40958976    7  HPFS/NTFS/exFAT

```

Yeah, OK.  And what is your problem, are you trying to fix something?

---

### Post by sjalv on 2011-11-07
> **Hakunka-Matata said:**
> Yeah, OK.  And what is your problem, are you trying to fix something?

As this whole thread's title suggests, I'm trying to dual boot Win 7 and Ubuntu and the installer doesn't detect Win 7 installation. This is the first time I've run into this problem, before it has worked flawlessly (Win7 64 bit + Ubuntu 64 bit).

---

### Post by Hakunka-Matata on 2011-11-07
> **darkod said:**
> I think your issue is that the disk has a GPT partition table and not msdos (the old type).
On top of that, in the windows disk management check if it says the disk is Basic or Dynamic. It wouldn't install easy on dynamic (if it would install at all).

Your first problem with the HDD is that it already has more than four partitions.  Four primaries and one Extended, that setup is **undefined, illegal.  **Maybe Windows has converted your disc to **Dynamic, which Windows does if you try to force it to create more than four partitions.**

So show us or tell us what Windows Disk Manager says about the partitioning on your HDD.  If it has been converted to **dyamic,** you have some work ahead of you to get the HDD fixed up and ready for another OS to be installed.  

SO, is your disk now configured as **DYNAMIC, or BASIC?**

---

### Post by darkod on 2011-11-07
If he has GPT table the 4 partitions limit is not applicable any more. Just for MSDOS tables.

---

### Post by Hakunka-Matata on 2011-11-07
> **nautica17 said:**
> In Windows, it says I'm using basic. I've dual booted Ubuntu with 7 and Vista many times in the past though, and I think in every instance I was using a GPT partition table since that is I believe the default nowadays. 

I'm wondering if maybe there is a hardware issue. I built this computer 2 years ago, so none of the parts are legacy or anything like that. I'm gonna look in BIOS and see if there is something in there maybe.

Edit: After googling a bit, I think you're right, the GPT is the issue. **And it doesn't look like I can convert it back to the old type without data loss.**

**@nautica17: **
You should be able to convert back from Dynamic to Basic disk type w/o losing data or corrupting the partition, many people have done just that using information and in some cases programs that were built by FMers to deal with weird problems that usually are created by Windows esoteric ideas and implementations.

---

### Post by Hakunka-Matata on 2011-11-07
> **darkod said:**
> If he has GPT table the 4 partitions limit is not applicable any more. Just for MSDOS tables.

Yes, I realize that, but we are not sure of how the disk is partitioned, whether it in fact has a GPT Partition Table or (msdos) partition table.  If the disk was GPT at one time, and then reconfigured back to a msdos partition table then the backup GPT partition table that is written at the very end of the HDD may not have been deleted.  That will cause **fdisk** to report a GUID partitioning scheme, even though that is not the case.

GPT drives can handle a total of 128 primary partitions, it doesn't use Extended partitions and Logical partitions.

---

### Post by sjalv on 2011-11-07
> [QUOTE]Quote:
Originally Posted by darkod  
I think your issue is that the disk has a GPT partition table and not msdos (the old type).
On top of that, in the windows disk management check if it says the disk is Basic or Dynamic. It wouldn't install easy on dynamic (if it would install at all).

Your first problem with the HDD is that it already has more than four partitions. Four primaries and one Extended, that setup is undefined, illegal. Maybe Windows has converted your disc to Dynamic, which Windows does if you try to force it to create more than four partitions.

So show us or tell us what Windows Disk Manager says about the partitioning on your HDD. If it has been converted to dyamic, you have some work ahead of you to get the HDD fixed up and ready for another OS to be installed. 

SO, is your disk now configured as DYNAMIC, or BASIC?[/QUOTE]
In my case there were initially just three partitions, not five as I have now. That didn't work, nor did four as at first I played with the Windows disk manager. All partitions are basic and have been from the start (also the three initial partitions). It's also a "fresh" Win 7 installation on a brand new machine so at least in my case the partition table type shouldn't have been changed at any point yet.

---

### Post by Hakunka-Matata on 2011-11-07
Since this thread was started by FM **nautica17** I'll ask you politely to consider starting your own thread with an a very descriptive title.

Now, I'll ask you to run the script file I attach, all it does is download, install, run, **boot_info_script.sh** and open gedit on the file it generates, so you can paste it into a reply, and then enclose the entire text in [c0de] tags.  (don't copy that c0de), misspelled on purpose.  Somebody tell me how to post [B]bracket code slash bracket.

[/B]so run this 'makeresults.sh' script file suchly:```
sudo bash makeresults.sh
```either starting in the same directory that contains the script file itself, Downloads?, or adding that to the command.

---

