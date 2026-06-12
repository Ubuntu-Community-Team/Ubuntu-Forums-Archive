---
title: "UEFI 12.04_AMD64 - Win7 dual boot problems"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by martinr on 2012-06-14
I'm trying to create a dual boot system. I bought new hardware with Win7 64bit (a UEFI capable BIOS but with a System Reserved boot partition) pre-installed. I repartitioned my drive (with gparted) and did a fresh install of Ubuntu desktop 12.04 amd64 LTS with the live CD.

During installation I selected to install Grub into the MBR of sda (the alternative options sda1-sda9 made no sense to me). Now my computer still boots straigt into Windows. I've been reading up on UEFI-GTP for a day, but things are getting more fuzzy than clear. I'm new to UEFI and GPT, is there a simple and safe solution to make this dual boot work?

I attached bootinfo-script results (ignore thumbdrive sdd) and grub entries from the install syslog file to this question. Any help would be much appreciated.

Here's a quick overview of sda:
```

(parted) print 
Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  16.1GB  16.1GB  primary   ntfs            diag
 2      16.1GB  16.2GB  105MB   primary   ntfs            boot
 3      16.2GB  177GB   161GB   primary   ntfs
 4      177GB   1000GB  823GB   extended
 5      177GB   182GB   5046MB  logical   ntfs
 6      182GB   189GB   6443MB  logical   linux-swap(v1)
 7      189GB   242GB   53.7GB  logical   ext4
 8      242GB   247GB   5046MB  logical   ext4
 9      248GB   1000GB  753GB   logical   ntfs


Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)  [OEM recovery partition]
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS                 [Appearantly the Win7x64 boot loader partition]
/dev/sda3          31,664,128   346,236,927   314,572,800   7 NTFS / exFAT / HPFS                 [Win7x64 installation/system partition]
/dev/sda4         346,236,928 1,953,523,711 1,607,286,784   5 Extended                            [Container for logical partitions]
/dev/sda5         346,238,976   356,093,951     9,854,976   7 NTFS / exFAT / HPFS                 [Data partition]
/dev/sda6         356,096,000   368,680,959    12,584,960  82 Linux swap / Solaris                [Linux swap partition]
/dev/sda7         368,683,008   473,540,607   104,857,600  83 Linux                               [Ubuntu 12.04 root partition]
/dev/sda8         473,542,656   483,397,631     9,854,976  83 Linux                               [Linux /home partition]
/dev/sda9         483,399,680 1,953,523,711 1,470,124,032   7 NTFS / exFAT / HPFS                 [Data partition]


```

I did some further digging and what happened here?
```

# gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

```
Could this be the result of grub from the live CD trying to install itself in the MBR of sda?
Should / can I fix this?

Here's the [solution]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957").

---

### Post by darkomano on 2012-06-14
ATA WDC WD10EADX-22T (scsi) - 1TB - is a MBR disk. (Not a GPT disk).
 
Your computer should have the option to switch between BIOS or UEFI firmware. 
------------------------------------------------------- 
If BIOS is selected then **first disk** listed in BIOS must be a _MBR disk_.
Whatever code is placed in MBR it is loaded and executed after BIOS POST. 
a) if Windows based this code loads code from active partition boot record and executes it.
b) If GRUB based this code looks for next stage of GRUB code located on disk based on partition offset, loads it and executes it.
 
----------------------------------------------------------------------------
If UEFI is selected then a disk in the system must be a _GPT disk_ holdind a GPT "System Partition" which contains OS specific EFI boot manager(Windows bootmgr.efi or efi boot manager from another OS)
 
The firmware executes UEFI boot manager(contained in UEFI) which in turn loads either Windows boot manager or another boot manager (for example GRUB) if installed. 
UEFI does not use boot records (MasterBR, PartitionBR, VolumeBR).
 
UEFI boot manager can also load and execute another OS specific efi boot manager from removable (CD, DVD, USB) EFI (installation) media (so you can install a specific OS on hard disk).
--------------------------------------------------------------------------------
Hope this small explanation on boot sequences for BIOS and EFI can help you further. 
 
I think your firmware must be switched to BIOS at the moment as you have a MBR disk with Windows 7 installed which is also booting OK.
 
You have two options:
1. Add Ubuntu installation to Windows boot menu.
2. Run Ubuntu installation media and reinstall / repair grub to MBR. Reinstalling would also create a dual-boot menu (grub based) for Ubuntu and Windows 7.
 
Adding Ubuntu to Windows 7 boot menu goes like this:
1. copy file /boot/grub/boot.img (from Ubuntu) to a Windows folder say "c:\".
2. create a boot sector loader (in BCD) with drive and path pointing to c: and "\boot.img". You could use [Visual BCD Editor]("http://www.boyans.net") for creating boot sector loader and amending drive and path.

---

### Post by darkomano on 2012-06-14
Can you post a screenshot of Windows 7 Disk Management to see how Windows 7 sees disk an partitions at the moment ?

---

### Post by martinr on 2012-06-14
Thanks Darko,

Your overview helps a lot.
It seems I have a bit of both?!

The contents of sda2 are:```
/dev/sda2       100M   25M   76M  25% /media/SYSTEM RESERVED

root@ubuntu:/media/SYSTEM RESERVED# ls
Boot  bootmgr  BOOTSECT.BAK  System Volume Information

```

Upon power up, I can select a boot device by pressing F12 and see an UEFI CDROM option or my HD (no Ubuntu of Grub). In the BIOS I haven't seen an MBR/EFI switch at all (I'll take a picture the next time I'm in there).

On the MS forums I read that Win7x64 uses EFI + GPT to boot.

Could it be that the 12.04 Live CD install have bluntly overwritten the MBR area? How could I check this?

Before repartitioning I found this:
```

Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size        Type     File system  Flags
 1      2048s       31459327s    31457280s   primary  ntfs         diag
 2      31459328s   31664127s    204800s     primary  ntfs         boot
 3      31664128s   992057343s   960393216s  primary  ntfs
 4      992057344s  1953521663s  961464320s  primary  ntfs

```

After repartitioning and pre 12.04 install, I had this:
```

Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size         Type      File system     Flags
 1      2048s       31459327s    31457280s    primary   ntfs            diag
 2      31459328s   31664127s    204800s      primary   ntfs            boot
 3      31664128s   346236927s   314572800s   primary   ntfs
 4      346236928s  1953523711s  1607286784s  extended
 5      346238976s  356093951s   9854976s     logical   ntfs
 6      356096000s  368680959s   12584960s    logical   linux-swap(v1)
 7      368683008s  473540607s   104857600s   logical   ext4
 8      473542656s  483397631s   9854976s     logical   ext4
 9      483399680s  1953523711s  1470124032s  logical   ntfs


```
There is a firmware way of starting the recovery partition by pressing <ALT>+F10 during boot. This doesn't start grub either.

---

### Post by martinr on 2012-06-14
> **darkomano said:**
> Can you post a screenshot of Windows 7 Disk Management to see how Windows 7 sees disk an partitions at the moment ?

I will. (from memory I can remenber that it is not a dynamic disk and that I wasn't able to convert it to GPT). 

I'm currently working of this rig with a live CD, heavily apt-getted with diag tools, that's why I can't get into the BIOS or Win7x64 right now.

I've done many dual boot installs in the past and blindly trusted on my good experience with Ubuntu, but now I've gotten a little worried of losing the #$%^ factory pre-installed stuff without recovery CDs nor documentation.

Never a dull moment whilst boldly installing a new OS. :mrgreen:

---

### Post by darkomano on 2012-06-14
There is a "System Reserved" partition which Microsoft/Windows 7/Vista creates on MBR disks - this partition is usually hidden and 100-200MB in size. It contains usually  bootmgr and \boot folder with BCD store inside.
 
This MBR "System Reserved" must not be confused with GPT System Partition !
They have similar roles but a MBR partition is not a GPT partition !
 
A MBR disk can have only MBR partitions.
A GPT disk can have only GPT partitions.

---

### Post by martinr on 2012-06-14
According to Oldfred:
> **oldfred said:**
> If you have the new UEFI type BIOS then you should with both Windows or Ubuntu get two choices from the install CD/DVD. One would be legacy/BIOS/MBR and the other UEFI/efi. 

You have to choose the same for both Windows &  Ubuntu. Windows will only boot from gpt partitioned drives with UEFI, but Windows normally still is installed in old BIOS/MBR mode. So then you need to install Ubuntu in BIOS/MBR mode.

Two things tell if UEFI. One is drive will be partitioned with gpt(GUID) not MBR(msdos). The other is the first partition should be the efi partition.

Only if drive does not have Windows (Linux only) can you create a gpt partition scheme and boot with BIOS but then you also need an extra 1MB bios_grub partition.
[origin]("http://ubuntuforums.org/showthread.php?p=12026008")

That would indicate that I have the BIOS/MBR boot sequence, but why didn't grub appear then, when it installed itself to the MBR of sda? I only had the choices: sda, sda1-sda9 (except sda4).

Furthermore at boot time I can select the boot device with F12 and the only things I can see are:
[LIST=1]
[*]UEFI CD/DVD
[*]HD0
[*]CD/DVD
[/LIST]

Furthermore why is there a separate and active boot partition in sda2? Where windows seems to bootstrap from?

The world used to be so simple.

---

### Post by martinr on 2012-06-14
> **darkomano said:**
> There is a "System Reserved" partition which Microsoft/Windows 7/Vista creates on MBR disks - this partition is usually hidden and 100-200MB in size. It contains usually  bootmgr and \boot folder with BCD store inside.
 
This MBR "System Reserved" must not be confused with GPT System Partition !
They have similar roles but a MBR partition is not a GPT partition !
 
A MBR disk can have only MBR partitions.
A GPT disk can have only GPT partitions.

Okay, that should settle the matter that it is an MBR partition and hence the BIOS/MBR bootstrap method should be in effect.

Then I still don't understand why I won't see grub appear? I configured it to install itself into the MBR of sda (note that sda2 is active).

(Why did Win7x64 need a separate boot partition (sda2)??)

---

### Post by darkomano on 2012-06-14
UEFI/GPT I think is still in development and not used very much. New computers come with UEFI but with possibilty to switch to BIOS.
 
On forums you can get more help if you stick with BIOS/MBR. There are also much more guides addressing old BIOS/MBR dual boots.
 
I am not sure there are many people understanding EFI/GPT and EFI dual booting really - I have not done EFI dual booting either.
 
----------------------------------------------------------------------
Windows 7 creates the "System Reserved" partition to separate boot related files from the rest of OS for one main reason:
Boot files cannot be encrypted !
(and because the partition is hidden the boot files are better protected)
 
You could encrypt the OS partition but the "boot" partition must stay unencrypted.
Windows boot files _must_ be on an "active" partition or you cannot boot.
 
--------------------------------------
One possible explanation for grub not being written to MBR is:
Maybe there is an option in BIOS to protect MBR - a user should have the possibility to unprotect.

---

### Post by martinr on 2012-06-14
> **darkomano said:**
> UEFI/GPT I think is still in development and not used very much. New computers come with UEFI but with possibilty to switch to BIOS.
 
On forums you can get more help if you stick with BIOS/MBR. There are also much more guides addressing old BIOS/MBR dual boots.
 
I am not sure there are many people understanding EFI/GPT and EFI dual booting really - I have not done EFI dual booting either.
 
----------------------------------------------------------------------
Windows 7 creates the "System Reserved" partition to separate boot related files from the rest of OS for one main reason:
Boot files cannot be encrypted !
(and because the partition is hidden the boot files are better protected)
 
You could encrypt the OS partition but the "boot" partition must stay unencrypted.
Windows boot files _must_ be on an "active" partition or you cannot boot.
 
--------------------------------------
One possible explanation for grub not being written to MBR is:
Maybe there is an option in BIOS to protect MBR - a user should have the possibility to unprotect.

Of course, thanks!

I've looked for that already, but I'll look again. For my understanding, there is only one MBR on a disk, isn't there?
Does it matter for Grub that sda2 is active?

How can I re-install GRUB in the MBR (resuming my broken dual boot installation)?
Is there another way to start Grub? from Win7 for example? (It used to work with boot.ini files.)

---

### Post by darkomano on 2012-06-14
> **martinr said:**
>  For my understanding, there is only one MBR on a disk, isn't there?
Does it matter for Grub that sda2 is active?
 
How can I re-install GRUB in the MBR (resuming my broken dual boot installation)?
Is there another way to start Grub? from Win7 for example? (It used to work with boot.ini files.)
 
Yes there is only one MBR - first sector on disk. 
Grub does not use active partition - it uses partition address.
 
Grub install/reinstall - [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
 
 
To dual boot from Windows 7:
 
1. copy file /boot/grub/boot.img from Ubuntu to say Windows "c:\"
(from Windows - install "ext2fsd" - allows access to ext2/3/4 from Windows 7)
2. using [Visual BCD Editor]("http://www.boyans.net") - create "boot sector loader" -> drive = c: and path=\boot.img

---

### Post by martinr on 2012-06-15
Hi Darko,

Thanks for you help.

Here's the information you asked for.

How Win7x64's disk manager sees the drive (in order to determine GPT):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219742&stc=1&d=1339778311[/IMG]

Some BIOS shots to determine which boot sequence is followed and why Grub wasn't installed in the MBR of sda?

No MBR protection option can be found:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219743&stc=1&d=1339778311[/IMG]
EFI is first in the boot sequence:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219744&stc=1&d=1339778311[/IMG]
This is the details page of the EFI DEVICE PRIORITY option:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219745&stc=1&d=1339778311[/IMG]

My new rig also has an Intel Management Engine BIOS on board (which does nothing at the moment).

The question remains, why Grub wasn't installed in the MBR and why can't I find that in the install log files?

---

### Post by darkomano on 2012-06-16
Thank you for the screen shots.
 
In BIOS Setup - Boot Options screen the first boot device is [EFI Device].
 
I think it must taken out of order.
 
So your boot options would be:
 
1st boot device [CD/DVD]
2nd boot device [HDD]
.....
 
If you insert a CD/DVD then it is booted, else
HDD is booted (HDD should be in MBR format).
 
Maybe this [EFI Device] in 1st position of BIOS boot options is confusing Linux installer and GRUB is not written to HDD first sector (MBR position) ? 
 
All new installation media (I think) is prepared for BIOS and for EFI boot.
 
It is the computer setup which boots either BIOS way or EFI way.
In your case 1st device is EFI so the installation CD/DVD is booted EFI way (I think).
Is Linux setup/installation expecting also a GPT disk as installation target when booted the EFI way ? 
I don't know.
If this is true then writing a MBR is meaningless and setup does not write a MBR.
Maybe it is just an error in the setup/installation script ?
 
Installation is much more complex now with having two kind of disk formats (MBR and GPT) and also two kind of firmware (BIOS an EFI).

---

### Post by martinr on 2012-06-16
My brain reached critical mass this morning, after reading up on EFI boot sequences, WIN7x64 + GPT, Darko's help and reading a lot of other threads.  
Here's a recap for other people experiencing similar problems.

**Goal**:
Create a dual boot system with a pre installed Win7x64 and Ubuntu Desktop 12.04 LTS amd64 with Grub installed as the boot-loader in the MBR of sda.

**Problem symptoms**:
After Ubuntu installation from the Live CD along side Win7x64, Grub wont start at boot-up of the system. It boots straight into Win7.

**Hypothesis:**
The Ubuntu Desktop 12.04 amd64 Live CD, was booted with an UEFI boot sequence although the hard disk structure is MSDOS with MBR.
This fools Grub into switching to EFI mode and failing to install itself into the MBR.
To test this hypothesis I will reinstall from the Live CD, but start it with an BIOS/MBR boot sequence.

**Needed Materials**:
[LIST]
[*]An external HD and/or a 10 pack of empty DVDs (for backup).
[*]Ubuntu Desktop 12.04 LTS amd64 Live CD
[/LIST]

**Method**:
[LIST=1]
[*] Backup first.
[*] Determine if the HD structure is mdos/MBR or GUID Partition Table (GPT).
[*] Determine the utilized boot sequence of the Live CD (U)EFI/GPT or BIOS/MBR.
[*] Determine if you can somehow switch between (U)EFI or BIOS/MBR boot sequence.
[*] Boot the Live CD in non (U)EFI mode.
[*] Install Ubuntu on its partition and install Grub in the MBR of sda (the boot HD).
[*] Reboot and test if Grub appears and Win7 and Ubuntu 12.04 work.
[/LIST]

**Results**:
[LIST=1]
[*] As a precaution backup (in order of prevalence): your MBR, your data, burn the (cheap-***) OEM (bastards) factory restore DVDs, burn the Win7 recovery DVDs.
[*] Run parted on sda to find out your HD partition structure.
```

(parted) print 
Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: **msdos**

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  16.1GB  16.1GB  primary   ntfs            diag
 2      16.1GB  16.2GB  105MB   primary   ntfs            boot
 3      16.2GB  177GB   161GB   primary   ntfs
 4      177GB   1000GB  823GB   extended
 5      177GB   182GB   5046MB  logical   ntfs
 6      182GB   189GB   6443MB  logical   linux-swap(v1)
 7      189GB   242GB   53.7GB  logical   ext4
 8      242GB   247GB   5046MB  logical   ext4
 9      248GB   1000GB  753GB   logical   ntfs

```
[*] I verified in the intial install logs (/var/install/syslog) that erroneously grub-efi was installed instead of grub-pc:
```

Jun 13 13:45:35 ubuntu grub-installer: info: architecture: amd64/**efi**
...
Jun 13 13:45:38 ubuntu grub-installer: **Removing grub-pc** ...
Jun 13 13:45:39 ubuntu grub-installer: Purging configuration files for grub-pc ...
Jun 13 13:45:40 ubuntu grub-installer: Removing grub-gfxpayload-lists ...
Jun 13 13:45:40 ubuntu grub-installer: Removing grub-pc-bin ...
...
Jun 13 13:45:44 ubuntu ubiquity: The following extra packages will be installed:
Jun 13 13:45:44 ubuntu ubiquity:   efibootmgr grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common
...
Jun 13 13:45:57 ubuntu ubiquity: **Setting up grub-efi** (1.99-21ubuntu3.1) ...
...
Jun 13 13:45:58 ubuntu grub-installer: info: **Installing grub on 'dummy'**
Jun 13 13:45:58 ubuntu grub-installer: info: grub-install supports --no-floppy
Jun 13 13:45:58 ubuntu grub-installer: info: Running chroot /target grub-install  --no-floppy --force
Jun 13 13:45:59 ubuntu grub-installer: Installation finished. No error reported.
Jun 13 13:45:59 ubuntu grub-installer: info: grub-install ran successfully

```

[*] Check for (U)EFI options in your BIOS and or firmware boot menu. Switch off (U)EFI or select the non (U)EFI DVD boot method in your firmware boot menu. My computer offers a firmware boot menu by pressing F12 at start-up. Switch off the (U)EFI boot sequence in the bios or select the non (U)EFI boot device/method in the firmware boot menu. I will choose the non UEFI CD boot in the firmware boot menu (no BIOS changes required).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219744&stc=1&d=1339778311[/IMG]
[/LIST]

See my next posting for further results, my conclusion and recommendations. 

[Whilst I was writing this, I saw that Darko simultaneously had replied, thanks it supports my hunch and gives me confidence I'm on the right track.]

---

### Post by martinr on 2012-06-16
(Results continued)

[LIST]
[*]4. (continued) Here's a picture of the F12 boot device selector option during startup of my computer:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219782&stc=1&d=1339838037[/IMG]
[*]5. I entered the Live CD into the CD/DVD drive, rebooted and hit F12 during startup. The boot device selector appeared and instead of the default UEFI selection, I selected the P2 options (see picture above). To boot the Live CD in non (U)EFI mode.
[*]6. I installed Ubuntu on its partition again and noted a difference. I was not served the question "on which partition I wanted to install Grub", any more whereas in the previous attempt I could choose between sda, sda1, ..., sda9.
[*]7. After installation I rebooted and Grub appeared as expected! Ubuntu boots correctly and Win7 also. Success!
[/LIST]

**Conclusion**
When the Live CD is booted with an UEFI boot sequence, Grub erroneously expects a GPT structured HD, even if the boot HD is msdos/MBR structured. Grub doesn't installs itself to the MBR. When the same Live CD is booted with a non UEFI boot sequence Grub is automatically installed correctly in the MBR and Win7 is added too. So start the Live CD with a non UEFI boot sequence if you have an msdos/MBR (non GPT) structured HD.

**Discussion**
A BIOS option to write protect the MBR could also prevent Grub from installing itself in the MBR.

Because by (factory) default my computer tries to boot a CD in UEFI mode it triggers the flow of events that leads to the failing grub-efi installation. The simplest way to correct this, is to re-install the live CD in non UEFI boot sequence mode.

Because more and more computers support UEFI nowadays, the out of the box installation of Grub and hence Ubuntu from the Live CD is expected to fail more often. I would suggest that the installation process should be updated to alert the user of a UEFI boot sequence conflicting with a non GPT structured installation HD or better yet, if possible automatically make the correct Grub installation selection accordingly to the HD's structure.

**Recognitions**
Along with the authors of helpful threads on this forum, I would like to explicitly thank darkomano for his help and advise in this matter. Thanks!

---

### Post by martinr on 2012-06-16
Please feel free to drop a line if you found this thread helpful or have additional insights.

---

### Post by YannBuntu on 2012-06-18
Hello

**@martinr:** Thank you for describing your experience. It shows a good example of system where it is possible to deactivate EFI in the BIOS and use standard grub-pc instead of grub-efi. 
If I understood well, it also shows a bug of Ubiquity (=the Ubuntu installer). Please could you create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)
Entitle it "Ubiquity installed grub-efi when it should have installed grub-pc", attach your /var/log/installer/syslog and 
/var/log/installer/partman files, and **please indicate the URL of this report** here so that we can follow-up it.


**@all:** I would like to add that **some EFI systems need a procedure different to the one you used in this thread.**
Here is why:
- some EFI-BIOS have an option to deactivate EFI boot, some don't. Some BIOS don't have EFI mode at all.
- The procedure for activating/deactivating EFI in the BIOS can be different for each BIOS
- on some systems, it is possible to use grub-pc even if the BIOS is in EFI mode
- on some systems, it is possible to use grub-efi (if BIOS setup in EFI mode), or grub-pc. On some other systems, it is possible to use only grub-pc , or only grub-efi.
- **If you want to try grub-efi**, it is first necessary to have a GPT disk with an ESP (EFI partition= FAT32, >200Mo, start_of_the_disk, boot flag), and to setup the BIOS in EFI mode. Then you need to install grub-efi (an easy way for this is to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") with the "Separate /efi" option). To finish, some old EFI-BIOS need to create an entry that boots the grub*.efi file in the EFI partition.
- **If you want to try grub-pc**, it is necessary to have either a non-GPT disk, or a GPT disk with a BIOS-boot partition (>1Mo, no filesystem, bios_grub flag). On some systems it is also necessary to deactivate EFI in BIOS. Then you need to install grub-pc (an easy way for this is to use Boot-Repair without the "Separate /efi" option).
- **If you don't know which method you need (grub-pc or grub-efi).** I don't know any general rule to know if a system can/must use grub-pc or/and grub-efi. But there are clues that may orientate to one or the other method (eg if Windows is installed in the MBR, try grub-pc first). What I recommend here is to run Boot-Repair's "Recommended repair" which will install either grub-pc or grub-efi according to these small clues, it will also give advice on how to setup BIOS and boot partitions. Note the URL that will appear on a paper, and reboot the PC. If you still can't access Ubuntu, you can then try the other method this way: run Boot-Repair again, click "Advanced options",go to the "GRUB location" tab, toggle the "Separate /efi" option, apply. Note the 2nd URL that will appear, then reboot. If both methods don't work, you may have not setup your BIOS and/or boot partitions correctly, so indicate your 2 URLs to ask help [here]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917").

Hope this helps.

---

### Post by martinr on 2012-06-19
> **YannBuntu said:**
> **@martinr:**
If I understood well, it also shows a bug of Ubiquity (=the Ubuntu installer). Please could you create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)
Entitle it "Ubiquity installed grub-efi when it should have installed grub-pc", attach your /var/log/installer/syslog and 
/var/log/installer/partman files, and **please indicate the URL of this report** here so that we can follow-up it.

Thanks for the link YannBuntu. I submitted the report.
The bug report can be found [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015211").

---

### Post by YannBuntu on 2012-06-19
thanks

---

### Post by martinr on 2012-06-26
You can vote for this bug to be permanently fixed [over here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015211/+affectsmetoo").
See how many people it affects [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015211").

---

### Post by promet on 2012-07-06
I am in the process of building a new box, and you guys are exquisitely heightening my anxiety about the whole process, lol!

I had no idea this whole UEFI "innovation" was going to be such a can of worms. Well, yes I did, deep, deep in my subconscious, but I didn't want to admit it to myself in my waking life. I can at least thank you for ripping off the Band-Aid quickly. #-o

---

### Post by martinr on 2012-07-13
> **promet said:**
> I am in the process of building a new box, and you guys are exquisitely heightening my anxiety about the whole process, lol!

I had no idea this whole UEFI "innovation" was going to be such a can of worms. Well, yes I did, deep, deep in my subconscious, but I didn't want to admit it to myself in my waking life. I can at least thank you for ripping off the Band-Aid quickly. #-o

With the new 2TB HDs and beyond they grew out of their jacked and we needed something new (which made things more complex).

Now that you are aware of the problem its not half as bad. I knew no fear and obliviously installed on a system with all of my data on it. I was tricked into a false sense of security because the previous zillion times it worked like a charm. That's the time you get nipped in the butt.

---

### Post by nehaljwani on 2012-10-08
You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

---

### Post by martinr on 2012-12-09
> **nehaljwani said:**
> You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

Me no understand. :confused: Do need dual boot. HD was already MBR-BIOS, but only the boot sequence was UEFI.

---

