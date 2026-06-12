---
title: "Would you mind helping with yet another native Mac installation?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by sloverlord on 2011-02-27
Hi everyone, first-time poster here.

I've been running Ubuntu on a VM for a while, and am now trying to do a native installation. I'm trying to install 10.04 onto a MacBook Pro (5,1) which already has OS X and Windows installed. Following the instructions provided on several websites, I installed rEFI, and used OS X's Disk Utility to create another partition for Ubuntu (it's currently FAT). As of right now, my system is set up in that hybrid configuration where OS X is using the GPT, Windows is using an MBR, and gptsync is keeping the two together. 

The problem is that when I boot from the LiveCD, the installer is not seeing my partitions: it sees the disk as one single unit (/dev/sda), and asks if I want to install there, wiping out all other disk data.

Google directed me to several other people on this forum with a similar issue, and most of them seemed to be able to get it resolved, but their circumstances were all slightly different from mine and I wanted to get some expert advice before I went messing with my partitions. 

On each of the previous posts about this issue, people asked for information from fdisk and parted, so here goes:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2          409640   300795847   150193104   af  HFS / HFS+
/dev/sda3       303986688   367413247    31713280    c  W95 FAT32 (LBA)
/dev/sda4   *   367413248   625141759   128864256    7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo sfdisk -d

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        1, size=   409639, Id=ee
/dev/sda2 : start=   409640, size=300386208, Id=af
/dev/sda3 : start=303986688, size= 63426560, Id= c
/dev/sda4 : start=367413248, size=257728512, Id= 7, bootable

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: end of file while reading No such file or directory                
Retry/Ignore/Cancel? Cancel                                               
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh
table, and using Parted's rescue feature to recover partitions.

ubuntu@ubuntu:~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 210MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

ubuntu@ubuntu:~$ sudo parted /dev/sda2 print
Model: Unknown (unknown)
Disk /dev/sda2: 154GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  154GB  154GB  hfs+

ubuntu@ubuntu:~$ sudo parted /dev/sda3 print
Model: Unknown (unknown)
Disk /dev/sda3: 32.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

ubuntu@ubuntu:~$ sudo parted /dev/sda4 print
Model: Unknown (unknown)
Disk /dev/sda4: 132GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  132GB  132GB  ntfs

```(/dev/sda3 is where I'd like to install Ubuntu)

I just don't understand why the installer can't see my partitions when OS X, Windows, and parted all seem to think everything's fine. 

One last thing: elsewhere on the Internet someone recommended I try and use gdisk to rewrite my GPT as what it "should" be (i.e., what OS X and the MBR think it is now), to hopefully get the installer to see the tables. Is that my only option? And what do I need to add to my repo list to get gdisk? When I tried getting it with apt-get it couldn't find the package.

Thanks in advance, and let me know if there's more information I should provide.

---

### Post by srs5694 on 2011-02-28
You can download GPT fdisk (gdisk) from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) Get the .deb file for your architecture (i386 or amd64) and double-click it to install it. Alternatively, you can download the OS X version and install it in OS X. In fact, I recommend you download both. Of course, you'll need to download the Linux version to the Ubuntu installation CD in "live CD" mode, or use something like [Parted Magic](http://partedmagic.com/doku.php) or [System Rescue CD,](http://partedmagic.com/doku.php) which include gdisk as "standard equipment."

Be very cautious, though. GNU Parted seems to think that your GPT data are damaged, but it hasn't provided any specifics about what's wrong. Blundering about with this could make matters worse. The good news is that your MBR partitions fill most of the drive, so if you need to recover using them, it should be possible (assuming they accurately reflect the true filesystem locations); you'll only need to guess at the EFI System Partition, and on Macs, that almost always starts at sector 40, so it should be easy to recover.

One critical bit of information: The whole reason for the ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) (which is what gptsync creates) is to keep Windows happy. When shown a hybrid MBR disk, Windows uses the MBR partitions, while most other modern OSes (such as Linux and OS X) use the GPT partitions. Thus, the fact that Windows is happy with the disk means nothing at all; it's showing you the MBR side and is ignoring the GPT side. The parted output you've posted indicates that the GPT side may be damaged; however, OS X uses the GPT side on hybrid disks, and you say OS X boots fine. This makes it a bit puzzling what's going on.

I recommend you post the following items:


[list]
[*]A screen shot of OS X's Disk Utility, with your hard disk highlighted so that we can see how your partitions are laid out according to it.
[*]The output of "sudo diskutil list" from an OS X Terminal program. This provides another view of the disk from OS X's perspective.
[*]The output of "sudo gdisk -l /dev/disk0" from an OS X Terminal program (after installing gdisk in OS X, of course).
[*]The output of "sudo gdisk -l /dev/sda" from a Linux Terminal program (using Parted Magic, System Rescue CD, or gdisk installed in an Ubuntu live CD).
[/list]


This information will help in diagnosing the problem and suggesting subsequent actions. Note that I'm asking for gdisk output from both OS X and Linux. In theory, they should be identical except for the disk device references (/dev/disk0 vs. /dev/sda); however, if they differ it could indicate a strange low-level problem of some sort. Also, if the parted message is any indication, gdisk might throw up a warning about damaged GPT data and ask whether to use MBR or GPT data. If so, tell it to try to use the GPT data, at least for this first test.

Whatever you do, *do not* try to make any changes to your partition table, using any utility, until you understand what's going on. Making blind changes in your situation can be quite risky. When the time comes, gdisk offers recovery options; you can read about them [here.](http://www.rodsbooks.com/gdisk/repairing.html) I recommend you read that page, perhaps some other pages from the same [GPT fdisk documentation,](http://www.rodsbooks.com/gdisk/) and maybe the [Wikipedia page on GPT.](http://en.wikipedia.org/wiki/GUID_Partition_Table) The technical details can get a bit hairy, but even if you don't understand everything, grasping some of the main concepts will help you recover your disk safely.

---

### Post by sloverlord on 2011-02-28
Thanks for your help. Here's the information you asked for:

[IMG]https://lh6.googleusercontent.com/__nJHgYAROSo/TWvMC4Y7_QI/AAAAAAAAAos/rcJkUYzlW8M/s512/disk_util_screenshot.png[/IMG]

Output from OS X:

```

[alex@alexs-macbook-pro:~]$ sudo diskutil list                                       (02-28 08:57)
Password:
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *320.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            153.8 GB   disk0s2
   3:       Microsoft Basic Data UBUNTU                  32.5 GB    disk0s3
   4:       Microsoft Basic Data BOOTCAMP                132.0 GB   disk0s4

[alex@alexs-macbook-pro:~]$ sudo gdisk -l /dev/disk0                                 (02-28 09:03)
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00000EA5-0556-0000-D120-0000725A0000
Partition table holds up to 64 entries
First usable sector is 18, last usable sector is 625142430
Partitions will be aligned on 8-sector boundaries
Total free space is 3191533 sectors (1.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       300795847   143.2 GiB   AF00  Customer
   3       303986688       367413247   30.2 GiB    0700  Untitled
   4       367413248       625141759   122.9 GiB   0700  BOOTCAMP

```Output from Ubuntu:

```

ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00000EA5-0556-0000-D120-0000725A0000
Partition table holds up to 64 entries
First usable sector is 18, last usable sector is 625142430
Partitions will be aligned on 8-sector boundaries
Total free space is 3191533 sectors (1.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       300795847   143.2 GiB   AF00  Customer
   3       303986688       367413247   30.2 GiB    0700  Untitled
   4       367413248       625141759   122.9 GiB   0700  BOOTCAMP

```GPT fdisk did not ask for which data to use in either case, and skipped straight to GPT.

(The "missing" 1.5 GB between the OS X and Ubuntu partitions is from when I tried to make a swap partition, but realized that would put too many records in the MBR and kick out windows. I thought (and Disk Utility thinks) I gave it back to OS X, but evidently not. That doesn't bother me though.)

So gdisk seems to have the same view of the disk on both systems, and like I said, OS X seems to think everything is fine. 

Hope this helps, and thanks again for your assistance. Like you said, I know nothing more than the absolute basics of disk partitioning, and don't want to take any action until I'm sure I understand the problem.

---

### Post by srs5694 on 2011-02-28
> **sloverlord said:**
> ```
[alex@alexs-macbook-pro:~]$ sudo gdisk -l /dev/disk0                                 (02-28 09:03)
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00000EA5-0556-0000-D120-0000725A0000
Partition table holds up to 64 entries
First usable sector is 18, last usable sector is 625142430
Partitions will be aligned on 8-sector boundaries
Total free space is 3191533 sectors (1.5 GiB)
```

Congratulations! You win the "most obscure GPT problem award" of the month! ;) In fact, I very nearly missed it in this output: Your GPT is half the usual size. Ordinarily, GPT disks can hold up to 128 partitions, but yours handles only 64. This is technically a violation of the GPT specification, but every OS I've tried this with handles it fine. The only utility I know of that *doesn't* handle it is libparted, which is used by the Ubuntu installer, GParted, GNU Parted, and several others. (FWIW, libparted also doesn't handle larger-than-usual GPT structures, which *are* legal, so I class this as a libparted bug.)

Out of curiosity, what tools did you use to create and modify this partition table? Not many can do this.

The solution, fortunately, is simple: You can use gdisk, as follows:


[list=1]
[*]Launch gdisk on your disk ("sudo gdisk /dev/disk0" in OS X or "sudo gdisk /dev/sda" in Linux; either will work).
[*]Just to be sure there's no other subtle problem, type "v". This performs a series of checks on the GPT and hybrid MBR data structures. If it reports any problems, type "q" to exit and post the output here.
[*]Type "x" to enter the experts' menu.
[*]Type "s" to change the partition table size.
[*]In response to the prompt, type "128" as the partition table size.
[*]Type "p" to review your partition table and be sure everything's OK. Also check that it's reporting a table size of 128 rather than 64.
[*]Type "w" to save your changes.
[/list]


There are a couple other things you might want to do before the last step, as described below; or you could re-launch gdisk to handle them, or not do them at all....

> (The "missing" 1.5 GB between the OS X and Ubuntu partitions is from when I tried to make a swap partition, but realized that would put too many records in the MBR and kick out windows. I thought (and Disk Utility thinks) I gave it back to OS X, but evidently not. That doesn't bother me though.)

Disk Utility tends to ignore smallish gaps between partitions, so it probably is doing that in this case.

In fact, you can create swap space and not have MBR problems. All that needs to be in the MBR is the Windows partition, and there's no need to have the MBR partitions be in the same order as the GPT partitions. The standard gptsync utility, though, is pretty limited in this respect. GPT fdisk is much more flexible, as described on my [hybrid MBR Web page.](http://www.rodsbooks.com/gdisk/hybrid.html) In fact, if you use GPT fdisk to create new GPT partitions on your disk as it is now, your hybrid MBR shouldn't be touched; but you might need to use GPT fdisk to create a new hybrid MBR in the future, should you make other changes or should you re-run gptsync or some other tool that modifies the hybrid MBR.

One other issue while considering partition changes: You might want to create a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) This partition is used by GRUB 2 on BIOS-based systems with GPT disks, which is what your Mac seems to be as far as GRUB 2 is concerned, given your current configuration. GRUB 2 can theoretically work without this partition, but it's more reliable with a BIOS Boot Partition.

If you choose to do all of these things, the procedure would be:


[list=1]
[*]Launch gdisk on your disk. If you integrate these instructions into the preceding ones, type "m" to return to the main menu after you fix the partition table size.
[*]In the main menu, type "n" to create a new partition. Enter a start point of "+128M", an end point of "+1M", and give it a type code of EF02. This action creates a BIOS Boot Partition that's 1 MiB in size. There'll be a 128 MiB gap between it and the preceding OS X partition. (OS X likes to see such gaps for certain operations, like OS upgrades.)
[*]In the main menu, type "n" to create a new partition. Use the default start and end points and give it a type code of 8200. This creates the swap partition. (It will need to be initialized, but the Ubuntu installer should do this.) If you skip creating the BIOS Boot Partition, though, enter "+128M" as the start point to keep that gap after the OS X partition that OS X likes to see.
[*]Optionally, type "s" in the main menu to sort the partitions. This isn't necessary, but it makes the table a bit less confusing.
[*]Type "p" to view the partition table and verify that it makes sense.
[*]Type "r" to enter the recovery & transformation menu.
[*]Type "o" to view the MBR data. Compare that to the "p" output from earlier to verify that the hybrid MBR partitions are as they are now. If not, you can create a new hybrid MBR by typing "h". You'll be prompted for information, as described on [my hybrid MBR page.](http://www.rodsbooks.com/gdisk/hybrid.html)
[*]Type "w" to save your changes.
[/list]


Good luck!

---

### Post by sloverlord on 2011-02-28
Everything worked wonderfully; I'm writing this post on a native Ubuntu installation that has not destroyed any of my other operating systems. Thank you so much!

> **srs5694 said:**
> Congratulations! You win the "most obscure GPT problem award" of the month! ;)

Hee hee, where do I claim my trophy>

---

