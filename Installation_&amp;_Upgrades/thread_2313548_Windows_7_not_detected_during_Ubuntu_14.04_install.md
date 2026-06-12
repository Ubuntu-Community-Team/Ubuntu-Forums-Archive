---
title: "Windows 7 not detected during Ubuntu 14.04 installation"
date: 2016-02-13
forum: Installation &amp; Upgrades
---

### Post by cirrusminorae on 2016-02-13
[FONT=Verdana]Hello all,[/FONT]

[FONT=Verdana]I'm  attempting to create a dual boot on my Windows 7 computer by adding  Ubuntu 14.04. I attempted to free up 100GB for Ubuntu on my hard drive  using the Shrink Volume option in Windows, but could only free up 4GB,  so I followed the suggestion I found in another forum to use the AOMEI  Partition Assistant program. This seemed to successfully free up the  100GB I wanted. I created a live USB stick using the pendrivelinux  program, use the "try Ubuntu" feature when it boots, and select the install Ubuntu  14.04 program. When I get to the install options, there is not an option  for "install alongside windows." It recognizes /dev/sda as  entirely unformatted space. While on the Live USB, it recognizes the Windows partition (?) and I can access the C:\ drive and its contents, but the installer doesn't recognize it.
[/FONT]
[FONT=Verdana]I've been searching this problem for several hours now. I found a thread with a similar issue ([/FONT][FONT=Verdana][http://ubuntuforums.org/showthread.php?t=1793978](http://ubuntuforums.org/showthread.php?t=1793978)) but, as [/FONT][FONT=Verdana]srs5964 states in that thread:[/FONT]
[COLOR=#000000][FONT=Verdana]If I've suggested a solution to a problem and you're not the original poster, [/FONT][/COLOR][I]do not try  my solution! Problems can seem similar but be different, and a good  solution to one problem can make another worse. Post a new thread with  your problem details.
[/I]
[FONT=Verdana]So here's a new thread :). From what I've read, this is probably a partitioning issue that is over my head -- I'm not too computer savvy. From my reading, I don't think its a UEFI issue (I don't think my computer is UEFI but not entirely sure...).

 I'll attach what I see in Windows disk management, since I'm in Windows right now. Let me know what other information is required and I'll be glad to supply it![/FONT]

---

### Post by grahammechanical on 2016-02-13
> [FONT=Verdana]I don't think its a UEFI issue (I don't think my computer is UEFI but not entirely sure...).
[/FONT]

I agree. In that picture I see mention of primary & extended partitions and what Windows calls logical drives. All of which points to MBR partitioning. That forum thread that you linked to is a long and complicated thread and it got side tracked. Forum member srs5964 is correct to warn about the use of certain commands which due to the power of the command can be dangerous. Also, unless we have exactly the same problem blindly following suggestions can make things worse.

In that user's case the problem was due the the machine having a BIOS boot system but with a GPT partitioned disk drive. We do not know if that is your situation. The thread did give us a command that is safe to use and informational. I have just used it on my system.

```
sudo sfdisk -l -uS
```

I will show you some relevant output

> Disk /dev/sda: 232.9 GiB, 250000000000 bytes, 488281250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 711AFC71-CB9D-498E-AE26-87126F2AF9D5

Device        Start       End   Sectors   Size Type
/dev/sda1      8192     16383      8192     4M BIOS boot
/dev/sda2     16384    147455    131072    64M EFI System
/dev/sda3    147456   8536063   8388608     4G Linux filesystem
/dev/sda4   8536064  16924671   8388608     4G Linux filesystem
/dev/sda5  16924672 488280063 471355392 224.8G Linux filesystem


> Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0008e2df

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         4096  78386908  78382813  37.4G 83 Linux
/dev/sdb2        78389246 976773119 898383874 428.4G  5 Extended
/dev/sdb5       972503040 976773119   4270080     2G 82 Linux swap / Solaris
/dev/sdb6        78389248 856629247 778240000 371.1G 83 Linux
/dev/sdb7       856631296 972500436 115869141  55.3G 83 Linux

I have a BIOS boot system with 2 hard drives. sdb has MBR partitioning and sda has GPT partitioning. As you can see from the disk label type. In your case there is 101 GB free space inside an Extended partition. And that may be the reason why the Installer is not offering the option to install alongside.

You could try shrinking the Extended partition using a Windows utility so that the free space becomes unallocated space outside the extended partition. With MBR partitioning we are allowed a maximum of 4 primary partitions and you have 2 primary partitions. System (500MB) & the extended partition (790GB) which seems to be Windows C: but that is actually referring to the whole extended partition with 2 logical partitions which are D: & C:

All this means is that with the 101GB free space as 101GB unallocated space outside the extended partition the Ubuntu installer might offer to install along side as It will have 101GB of space and 2 primary partition slots available to use for Ubuntu.

An alternative is to use the Something Else option which is another subject which we can advise on if you want to go that route.

Regards.

---

### Post by cirrusminorae on 2016-02-13
I attempted to create a partition in Windows for the Ubuntu OS, but I'm having the same problem with the Ubuntu installer not seeing any of the Windows stuff. Here's the output of the command you suggested, which suggests there is something going on between the way Windows and Ubuntu are interpreting the hard drive -- though, as a novice, I'm not sure what it means. sda is my hard drive where I want to install Ubuntu, and it looks like the partition I created shows up as sda6. sdc is the USB drive which is running the Live session.

```
ubuntu@ubuntu:~$ sudo sfdisk -l -uS

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048   1026047    1024000   7  HPFS/NTFS/exFAT
/dev/sda2      84912128 1530915325 1446003198   7  HPFS/NTFS/exFAT
/dev/sda3       1028033 1845515069 1844487037   f  W95 Ext'd (LBA)
/dev/sda4             0         -          0   0  Empty
/dev/sda5       1028096  84912127   83884032   7  HPFS/NTFS/exFAT
/dev/sda6     1530931200 1845515069  314583870  83  Linux

Disk /dev/sdc: 30672 cylinders, 64 heads, 32 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/55/55 (instead of 30672/64/32).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *     51304  62816255   62764952   c  W95 FAT32 (LBA)
        start: (c,h,s) expected (16,52,45) found (6,46,23)
        end: (c,h,s) expected (1023,54,55) found (243,54,55)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty
```

Where do I need to go from here?

---

### Post by yancek on 2016-02-13
You would be better off using the Something Else options during the install.  The Alongside method usually works but when something does go wrong, you will have absolutely no idea what it was because everything was happening in the background.  The link below explains dual booting in detail.  If you don't understand the tutorial, you would be better off stopping before you overwrite everything.  It's not really that complicated.  It just requires the ability to read and follow instructions along with some patience.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by cirrusminorae on 2016-02-13
I'm not opposed to taking the Something Else route while installing. The problem I'm having is that this option doesn't seem to detect any partitioning. In the guide you linked, the installer detects the partitions sda and sdb, and the various Linux installations, etc. When I get to this point, the installer only detects my disk as sda, without any information on it. I'm trying to follow the gparted tutorial, as well, to learn more about partitioning, and I find that no partitioning scheme is visible in gparted, it only shows I have 931 GB of unallocated space. 

So, I'm stuck. There seems to be some problem with the way Ubuntu is interpreting the partitions on the disk, but I don't know what the problem is or how to begin solving it.

---

