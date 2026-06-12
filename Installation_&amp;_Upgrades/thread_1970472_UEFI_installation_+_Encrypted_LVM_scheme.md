---
title: "UEFI installation + Encrypted LVM scheme"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by LazyYeti on 2012-05-01
Hello, 

I'm trying to install Ubuntu 12.04 LTS Precise Pangolin in U(EFI) mode.
Started with the Beta2 (AMD64 alternate CD), I'm now using the official release (AMD64 Alternate CD). I started a discussion [here]("http://ubuntuforums.org/showthread.php?p=11828138#post11828138"), topic has been closed since 12.04 official release.

**What I want to achieve:**
 
[LIST=1]
[*]UEFI installation (only)
[*]LVM
[*]Disk encryption using LUKS
[/LIST]
 The hardware is a brand  new Lenovo X220 laptop (Intel Core i7, Intel-VT &  VT-D enabled, UEFI only BIOS setting + USB UEFI BIOS setting enabled, Intel- SSD Intel 160 Go).

**What I've done so far:**

1 ) I used Parted Magic (Linux 3.2.1-pmagic) live CD to setup the partitions

[LIST]
[*] EFI System Partition, 256MB (FAT32) with boot flag : ef00
[*] BIOS Boot Partition 1MB (no filesystem)
[*]/BigPartition xxx GB (to hold the encypted LVM volumes)
[/LIST]
2 ) I use the [Ubuntu 12.04 LTS AMD64 Alternate CD]("http://releases.ubuntu.com/precise/") to proceed to installation

I booted on the installation media, setup the newtork, etc. When it comes to partitioning, the Ubuntu installer recognised the following partition scheme:
```
SCSI1 (0,0,0) (sda) - 160.0 GB ATA INTEL SSDXXXXXX
                 1.0 MB          Free space
n°1            268.4 MB     B    fat16                             ESP
n°2            159.8 GB                                            VGP

```I choosed "manual partitioning" for the partitionning step, I set my "VGP" named partition (159.8 GB) as a "Physical volume for LVM".

*NOTE: "**ESP" & "VGP" are just partition names set using the gdisk utility in Parted Magic (Linux 3.2.1-pmagic) live CD.*

Then I created my encrypted container, using the "create encrypted volume" feature & choose my "VGP" partition (159.8 GB):
```

[ ] /dev/sda free #1    (1MB; Free space)
[ ] /dev/sda1              (256MB; fat16)
[*] /dev/sda2             (159772MB; LVM)

```I ended with the following:
```
SCSI1 (0,0,0) (sda) - 160.0 GB ATA INTEL SSDA2CW16
                 1.0 MB          Free space
n°1            268.4 MB     B    fat16                             ESP
n°2            159.8 GB     K    encrypted  (sda2_crypt)           VGP

```Then I created all the logical volumes inside the encrypted volume group & set their mount points & options:

[LIST]
[*]root:            /                             (ext4)
[*]var:             /var          (ext4)
[*]usr:                           /usr                     (ext4)
[*]usr-local:           /usr/local        (ext4)
[*]swap
[*]home:                  /home                  (ext4)
[/LIST]
*NOTE: I choose to skip the /tmp to be able to create it in RAM using TMPFS (another challenge for the near future here...)*.

After validating of the partition scheme, I was asked where to install Grub: I tried to set "/dev/sda" & then "/dev/sda1" and got a fatal error for each attempt:
> 
unable to install grub in /dev/sda
Executing 'grub-install /dev/sda5' failed
This is a fatal error.


I then skip the step the bootloader and finalisez the installation, of course the Laptop won't boot...

Help would be appreciated

Thanks in advance

---

### Post by oldfred on 2012-05-01
It looks like it still is trying to do FAT16, that bug supposely is fixed.

EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)

I do not know for sure but the grub boot file has to be in the efi partition, so with efi do you specify the efi partition as the location to install?

OR:
PC's boot menu, the DVD drive showed up twice: once prefixed with UEFI, once with BIOS.
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

You should end up with this so you can boot from it in your efi partition:

/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi

---

### Post by LazyYeti on 2012-05-05
@oldfred: thanks for your feedback. As I mentionned, at the bootloader step, I tried to specify my /dev/sda1 partition (EFI partition) as destination & got the error:
> 
unable to install grub in /dev/sda1
Executing 'grub-install /dev/sda1' failed
This is a fatal error.                      
Since this first post, I modified the filesystem on the efi partition (switch from fat16 to fat32). I'll give another try.

---

### Post by oldfred on 2012-05-05
Not sure what your issue is.

Some installs that worked. But they did not have LVM.

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

---

### Post by LazyYeti on 2012-05-19
Issue isn't solved at this time, but I made a few steps forward.

I discovered (in the BIOS options) that the boot priority was set to  "legacy first", so I turned it to "UEFI first", perhaps this  modification has an effect, I can't be sure for now.

Than I booted on the [Ubuntu 12.04 Alternate AMD64 CD]("http://releases.ubuntu.com/12.04/") once again  (didn't touch the partition) & set the 268.4MB fat32 "ESP" partition  to be used as "EFI System Partition" (or the equivalent in the list,  can't recall the exact term).

The partitionning scheme before the grub step was:
> 
Encrypted volume (sda2_crypt) - 159.8 GB Linux Device-mapper (crypt)
n°1 159.8 GB f ext4

SCSI1 (0,0,0) (sda) - 160.0 GB ATA Intel XXXXXXXXXX
           1.0 MB                     Free space
n°1  268.4 GB      B      F     fat32 EFIboot EFI System P
n°2 159.8 GB       K             encrypted VGP (sda2_crypt)
859.6 kb                             Free space
After the partitionning, I was asked for the bootloader location, I did either try two options:

[LIST]
[*]install the bootloader on the MBR
[*]install the bootloader on /dev/sda
[/LIST]
 In both cases, I encountered ann error message:
> unable to install grub in /dev/sda
 Executing 'grub-install /dev/sda' failed
 This is a fatal error.
I'll give a last try with UEFI only installation of Ubuntu 12.04, double checking if:

[LIST=1]
[*]EFI system partition (268.4 MB fat32) has the right "ef00" boot flag
[*]Set the bootlader installation destination to /dev/sda1
[/LIST]
 I don't know what's wrong with the procedures I've gone through...

Perhaps my last hope would be to install Ubuntu in "Legacy mode" instead  of UEFI & see if I can use the workarounds to move to UEFI (I want  to avoid the dirty tricks & prefer a clean install, but at the end, I  need a FUNCTIONNAL installation ASAP).

---

### Post by oldfred on 2012-05-19
With UEFI, grub installs to the efi partition.

PC's boot menu, the DVD drive showed up twice: once prefixed with UEFI, once with BIOS.
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)

Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

But each vendor's UEFI is somewhat different.

If you try legacy mode (BIOS) you will also need a 1MB bios_grub flagged partition for grub to install correctly to the MBR.

---

### Post by LazyYeti on 2012-06-25
UEFI installation is not achieved yet, even after further reading on the web. I tried to perform (once again) a "fresh install".

The disk on which I'm trying to install Ubuntu 12.04 is not the original device which came with my Lenovo Thinkpad X220 laptop: I switched the original 2.5" HDD (with pre-installed Windows) with a brand new 160 GB Intel SSD.

The Laptop BIOS is a Phoenix SecureCore Tiano UEFI BIOS (version 1.26 - Date 2011-12-01). The BIOS settings used to boot & install Ubuntu using the Ubuntu 12.04 AMD64 alternate CD downloaded from [here]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-alternate-amd64+mac.iso"). CD integrity has been checked after burning.

**Partition preparation with GParted live CD**

I used GParted live CD (version 0.12-1-1). GParted live CD was enable to boot in UEFI only mode, so I modified the BIOS settings to enable legacy AND UEFI BIOS modes. 

Using GParted, I created 3 partitions using the followinf scheme in GParted:

[IMG]http://img36.imageshack.us/img36/9718/gpartedscreen01.jpg[/IMG]

*Note that the first 256 MB FAT32 partition is flagged as "boot" & the following partition with no filesystem (1MiB) is flagged as "bios_grub".*

Next step was to reboot, modify the BIOS settings to UEFI only. 
Than, I booted on a Ubuntu 12.04 Desktop live CD to run the fdisk & [Gdisk]("http://www.rodsbooks.com/gdisk/") utilities.

**Boot on the Ubuntu 12.04 Desktop live CD in UEFI only mode**

During the boot process, I noticed a quick message:
> Error: "prefix" is not set Than the live system started normally. I grabbed the following infos from fdisk:
```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   312581807   156290903+  ee  GPT

```
I grabbed the following infos from gdisk:
```

ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

```
So far, so good. Time to print the current partition table:
```

ubuntu@ubuntu:~$ sudo gdisk /dev/sda
Command (? for help): p
Disk /dev/sda: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 267AC1F8-E7A3-4AA3-83EA-9E560641FBBA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 2048-sector boundaries
Total free space is 3693 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          526335   256.0 MiB   EF00  
   2          526336          528383   1024.0 KiB  EF02  
   3          528384       312580095   148.8 GiB   0700  

```
Now, still using Gdisk utility, I printed out one by one all the partition detailled informations:
_Partition 1_
```

...
Command (? for help): i
Partition number (1-3): 1
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: 3662285A-1A04-4C49-869B-F99C4E06467F
First sector: 2048 (at 1024.0 KiB)
Last sector: 526335 (at 257.0 MiB)
Partition size: 524288 sectors (256.0 MiB)
Attribute flags: 0000000000000000
Partition name: ''

```
_Partition 2_
```

...
Command (? for help): i
Partition number (1-3): 2
Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)
Partition unique GUID: 3DE01AB7-B1FF-4545-998E-2CF8FB9346D9
First sector: 526336 (at 257.0 MiB)
Last sector: 528383 (at 258.0 MiB)
Partition size: 2048 sectors (1024.0 KiB)
Attribute flags: 0000000000000000
Partition name: ''

```
_Partition 3_
```

...
Partition number (1-3): 3
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: D8F79148-97F9-4101-98E7-16A783EDE612
First sector: 528384 (at 258.0 MiB)
Last sector: 312580095 (at 149.0 GiB)
Partition size: 312051712 sectors (148.8 GiB)
Attribute flags: 0000000000000000
Partition name: ''

```
Everything seems to be ok, so I rebooted the laptop (with BIOS settings "UEFI only" mode) on the Ubuntu 12.04 AMD64 alternate CD. 

**Boot on Ubuntu 12.04 AMD64 alternate CD (UEFI only mode)**

During the boot process, I noticed the following message again:
> Error: "prefix" is not set
Than the Ubuntu CD installer showed up as usual. I followed the normal installation process, using manual partitionning options, set my encrypted container, my Logical volume Group. Than I created all my logical volumes, apply the modifications to the partition table. I set all the mount points for the logical volumes and their filesystems...

During the Bootloader step, I'm asked to setup a destination for the bootloader:
I tried /dev/sda1 (which is supposed to be my UEFI System Partition), than the same old error message showed up (I even tried /dev/sda without more success...).
> 
unable to install grub in /dev/sda
Executing 'grub-install /dev/sda' failed
This is a fatal error.

This is really disapointing. What's wrong with this procedure? It's really surprising that a simple Ubuntu installation in UEFI mode is so painfull.

I have no clue for the moment. Before stepping down to a regular legacy BIOS only Ubuntu installation I REALLY appreciate suggestions here.

Thanks in advance.

---

### Post by geoff13 on 2012-06-29
@LazYeti
 
This is where you are going wrong (assuming). If you are using Firmware RAID from you Motherboard, Ubuntu will not recognize /dev/sdaX. You motherboard is telling it something else. In my case it was /dev/mapper/isw_alkjfnRaid1 and then the corresponding partition numbers. Once I learned this I was able to install Grub; I just have not installed it in the right paritition yet. :X
 
@OldFred
 
Thanks for all of the information on Paritioning, but alot of these issues are related to misnomers with firmware RAID. You have bee a godsend in setting up partitions thus far. Thanks!

---

### Post by LazyYeti on 2012-07-02
@geoff13: Thanks for your input, but I don't have a RAID setup.

---

