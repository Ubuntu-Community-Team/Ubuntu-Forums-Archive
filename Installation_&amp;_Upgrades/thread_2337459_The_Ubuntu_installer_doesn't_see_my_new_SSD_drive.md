---
title: "The Ubuntu installer doesn't see my new SSD drive"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-09-18
My specs:
Acer Predator G3-710 Desktop, 
HD ATA Disk 1TB, sda, GUID PT, this came with this pc.
SSD 120 GiB, sdb, GUID PT, just installed it yesterday.

The **HD** has Ubuntu Studio 16.04 only. It has 5 partitions (not in the following order): 
sda1, EFI System. Mounted at Boot EFI
sda2, Ext4. Mounted at Filesystem root.
sda3, Linux Swap, Active. 
sda4, EFI4, Fat32, not mounted
sda5, Fat32, not mounted

The **SSD** has 3 partitions. The 3rd one was made while I attempted to install Ubuntu.
sdb1, EFI, Ext4, not mounted, 57 Gib, Flags: Boot, ESP at the time of the attempt last night (no flags now).
sdb2, NTFS, not mounted, 42 GiB, Flags: msftdata at the time of the attempt last night (Boot, ESP now).
sdb, Unallocated, 21 GiB
-----------------------------------------------------------------------------

So, the problem is, at the time of installation, it would not allow me to install Ubuntu in the SSD drive. It was allowing me to choose the SSD drive to install the boot file though (in the choice at the bottom of the same page). 
Could it have to do with the Flags I had before for the SSD drive partitions? (See sdb specs above pls).

Thanks in advance for your info :)

JDL

---

### Post by sudodus on 2016-09-18
The information you show indicates that there are only two partitions on your SSD. Furthermore, the EFI partition should be small and have a FAT32 file system. But that information might not be quite correct.

Please post the output of the following commands (copy and paste to get it exactly correct),

```
df -h
sudo lsblk -fm
sudo parted -l
```

It will help understand the current partition table of the SSD.

-o-

Do you want the system in the SSD to be portable, or do you intend to have it in this Acer all the time?

---

### Post by javierdl on 2016-09-18
Thanks sudodus, here it goes:


```
df -h
Filesystem Size Used Avail Use% Mounted on
udev 7.8G 0 7.8G 0% /dev
tmpfs 1.6G 9.6M 1.6G 1% /run
/dev/sda2 275G 38G 224G 15% /
tmpfs 7.9G 439M 7.4G 6% /dev/shm
tmpfs 5.0M 4.0K 5.0M 1% /run/lock
tmpfs 7.9G 0 7.9G 0% /sys/fs/cgroup
/dev/sda1 511M 3.6M 508M 1% /boot/efi
tmpfs 1.6G 52K 1.6G 1% /run/user/1000

-------------------------------------------------------------------------

NAME   FSTYPE LABEL   UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                   sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat           D45B-1044                            /boot/efi  &#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4           5353966b-6a49-4801-b3db-06d3a464dc1f /          &#9500;&#9472;sda2 279.4G root  disk  brw-rw----
&#9500;&#9472;sda3 swap           e863d0f6-0ab2-4f1f-9fa3-55a652b02283 [SWAP]     &#9500;&#9472;sda3     8G root  disk  brw-rw----
&#9500;&#9472;sda4 vfat           5968-2E1F                                       &#9500;&#9472;sda4   293G root  disk  brw-rw----
&#9492;&#9472;sda5 vfat           5999-D4D5                                       &#9492;&#9472;sda5 350.7G root  disk  brw-rw----
sdb                                                                   sdb    111.8G root  disk  brw-rw----
&#9500;&#9472;sdb1 ext4   patr_ubu
&#9474;                     42fcf870-f522-4ec5-8a2a-56d95865d7c6            &#9500;&#9472;sdb1  53.2G root  disk  brw-rw----
&#9492;&#9472;sdb2 ntfs   patr_W10
                      0C50BB4D0D5E2EAD                                &#9492;&#9472;sdb2  39.3G root  disk  brw-rw----
sr0                                                                   sr0     1024M root  cdrom brw-rw----

-------------------------------------------------------------------------

sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   301GB   300GB   ext4
 4      301GB   615GB   315GB   fat32                                 msftdata
 5      615GB   992GB   377GB   fat32                                 msftdata
 3      992GB   1000GB  8523MB  linux-swap(v1)




Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name    Flags
 1      1049kB  57.1GB  57.1GB  ext4         Ubuntu
 2      57.1GB  99.2GB  42.1GB  ntfs         Win10   boot, esp 
```

---

### Post by Bucky Ball on 2016-09-18
Please use code tags. See the green link on the first line of my signature at the bottom of this post. Thanks.

---

### Post by sudodus on 2016-09-18
When you ran the commands, your computer was booted from **/dev/sda2**

Let us look at **/dev/sdb**

```
NAME   FSTYPE LABEL     UUID                                NAME SIZE   OWNER GROUP MODE
sdb                                                          sdb  111.8G root  disk  brw-rw----
&#9500;&#9472;sdb1 ext4   patr_ubu  42fcf870-f522-4ec5-8a2a-56d95865d7c6 &#9500;&#9472;sdb1 53.2G root disk brw-rw----
&#9492;&#9472;sdb2 ntfs   patr_W10  0C50BB4D0D5E2EAD                     &#9492;&#9472;sdb2 39.3G root disk brw-rw----


Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number Start  End    Size   File-system Name   Flags
1      1049kB 57.1GB 57.1GB ext4        Ubuntu
2      57.1GB 99.2GB 42.1GB ntfs        Win10  boot, esp 
```

Please use code tags next time, it makes it easier to read program code and input/output to/from a terminal window.

-o-

Do you intend to have both Ubuntu and Window 10 in the SSD (and to dual boot from it)?

Do you want to boot in UEFI mode or BIOS mode?

How did you install Windows?
- A fresh install and some kind of copy or clone?
- Which tool did you use?
- Does it work?

You mentioned that 'it would not allow' you to install Ubuntu. How did you try to install Ubuntu?
- A fresh install and some kind of copy or clone?
- Which tool did you use?
- Do you want to install into the 21 GB unallocated drive space or into partition #1?

---

### Post by Bucky Ball on 2016-09-18
Ah, ha! That old chestnut. Tip: swap the drives around and you should have it fixed in no time! (With any luck.) Windows in UEFI, or period, just hates to boot from sdb without some good degree of coaxing ...

Give it a try. Just change the SATA connections over, boot and see what happens, then report back. You might need to play about with it a bit to get it to work, but less than getting Win to boot from sdb.

Some laptops (I know you're on a desktop) flat refuse to boot anything from anything but sda without just about getting a crowbar to them, and some not even then ... :|

---

### Post by javierdl on 2016-09-18
sudodus,

1. Yes. I was going to install Windows 10 last (as advised [here]("http://www.tek-tips.com/viewthread.cfm?qid=1769606")). Reason why I was trying to install Ubuntu. That's when I encountered that problem. 
However, after all the advice I see around to install Ubuntu last, I'm feeling like going with what most say. But before I do I thought it would be good to solve that mystery about Ubuntu not letting me install in the SSD drive.

2. I suppose I should boot with UEFI, being a more recent technology. Shouldn't I?

3. Windows 10 came installed already with this desktop, I just got it about a month ago.

4. Same as above...

5. Same as above...

6. Windows 10 is no longer in the HD. I erased it. 
Btw, I do own a copy. That's what I'll use.

7. To install Ubuntu I used a LiveUSB drive. And chose "Install Ubuntu".

8. Downloaded it from Ubuntu.com, and used Startup Disk Creator.

9. Which tool?
 
10. No. The idea is to install into the Ext4 partition (unless someone here tells me otherwise). That 21 GiB Unallocated was created in the process as a result of attempting installation of Ubuntu. The NTFS partition was larger.



Bucky Ball,
Thanks, I hope that's easy enough. I'll give it a try.

---

### Post by javierdl on 2016-09-18
Ok, I did swap the partitions, see the new drives info here:

```
sudo lsblk -fm
[sudo] password for javier: 
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                 sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat         D45B-1044                            /boot/efi  &#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4         5353966b-6a49-4801-b3db-06d3a464dc1f /          &#9500;&#9472;sda2 279.4G root  disk  brw-rw----
&#9500;&#9472;sda3 swap         e863d0f6-0ab2-4f1f-9fa3-55a652b02283 [SWAP]     &#9500;&#9472;sda3     8G root  disk  brw-rw----
&#9500;&#9472;sda4 vfat         5968-2E1F                                       &#9500;&#9472;sda4   293G root  disk  brw-rw----
&#9492;&#9472;sda5 vfat         5999-D4D5                                       &#9492;&#9472;sda5 350.7G root  disk  brw-rw----
sdb                                                                 sdb    111.8G root  disk  brw-rw----
&#9500;&#9472;sdb1 ntfs         7FB2905E6E2475AD                                &#9500;&#9472;sdb1  48.8G root  disk  brw-rw----
&#9492;&#9472;sdb2 ext4         cc38bad8-967d-4d7b-a87e-3192db02081d            &#9492;&#9472;sdb2    63G root  disk  brw-rw----
sr0                                                                 sr0     1024M root  cdrom brw-rw----

--------------------------------------------------------------------------------------------

 sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   301GB   300GB   ext4
 4      301GB   615GB   315GB   fat32                                 msftdata
 5      615GB   992GB   377GB   fat32                                 msftdata
 3      992GB   1000GB  8523MB  linux-swap(v1)




Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name    Flags
 1      1049kB  52.4GB  52.4GB  ntfs Win10, esp
 2      52.4GB  120GB   67.6GB  ext4 Ubuntu boot,
```

---

### Post by sudodus on 2016-09-18
The SSD (patriot) is still /dev/sdb, so no difference after swapping the drives. And use CODE tags, please!

-o-

What can make a real difference is to disconnect the HDD. That will force the computer to recognize the SSD as /dev/sda. Then you can install Windows and Ubuntu into it. It is easier in that order, because Windows destroys boot things for Ubuntu (overwrites grub). It might happen also with major updates of Windows, so I think you need to learn how to repair grub.

But you own a copy of Windows. That means that you need not install in UEFI mode. It should be possible to install Windows in BIOS mode, if the computer can be booted in BIOS mode alias CSM alias legacy boot. And then it would be easier to get a stable dual boot system.

***Edit 1:*** I think Windows wants an MSDOS partition table in BIOS mode, and GPT in UEFI mode.

***Edit 2:*** It is also an option to have Windows in one drive and Ubuntu in the other drive, for example, keep Windows, where it is in the HDD, and install Ubuntu into the SSD. After that, it should be possible to fix dual boot either via a hotkey to get a boot menu (from which drive to boot), or via grub. In the latter case the EFI partition in the HDD will be used.

---

### Post by javierdl on 2016-09-18
When disconnecting HDD, do I boot up without it before I connect it back? 
Or just connect it back right away? 
Or it makes no difference?

---

### Post by sudodus on 2016-09-18
If you are careful, and avoid mechanical as well as electrical shocks, it works well. ***The power should be turned off*** when you connect and disconnect the drive.

A general rule is to turn off the power (and disconnect from the power grid) before opening the computer. And avoid static electricity.

---

### Post by Bucky Ball on 2016-09-18
> **sudodus said:**
>  ***The power should be turned off*** when you connect and disconnect the drive.

A general rule is to turn off the power (and disconnect from the power grid) before opening the computer. And avoid static electricity.

+1. Double check. Can't be careful enough (or maybe I'm paranoid). ;)

Incidentally, Windows should be installed first. I think you mentioned something about it second. Do you need to do that? Maybe I missed something. Head cold. SDD = install Win then Ubuntu

---

### Post by sudodus on 2016-09-18
Thanks for the [noparse]```
tags
```[/noparse] :-)

---

### Post by javierdl on 2016-09-19
Only now I'm finding that there can only be one Partition Table per disk, isn't it? 
This means that I'll have to install Ubuntu with Bios too &#128549;
So I booted from Gparted and created a new partition table for Bios, along with 2 partitions, one NTFS, the other one EXT4.
I already set the Bios to start up from the USB drive with Win10.
But when I booted It says: BOOTMGR is missing, that's as far it goes &#128549;
I guess it's not succeeding booting from the USB Drive, has it?

---

### Post by oldfred on 2016-09-19
Its not one partition table per drive.
But one type of partitioning, generally MBR or gpt.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

If newer UEFI system, then how you boot install media for both Windows & Ubuntu UEFI or BIOS is how it installs. Windows only installs to gpt when booted in UEFI mode and only installs to BIOS/MBR when installer booted in BIOS mode.

With UEFI/gpt boot flag must be on the ESP - efi system partition.
With BIOS the boot flag must be on the Windows partition with more boot code in the partition boot sector. And part of that info is bootmgr.

So if bootmgr missing, either boot flag is not on correct partition for either UEFI or BIOS boot or installer not correctly created.

---

### Post by javierdl on 2016-09-19
I would prefer to go with GPT/UEFI for both, Win10 and Ubuntu. After all, this is a newer system, just got it a couple months ago. But I thought someone had said that it would be safer and simpler if I were to install Win10 in BIOS. 
But given the present problem at hand (missing BOOTMGR), maybe I should go back to GPT/UEFI. 
What do you think?

---

### Post by oldfred on 2016-09-19
For most systems UEFI may have advantages. But the 35 year old BIOS/MBR configuration is well known.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by javierdl on 2016-09-19
Like I said, given that Bios won't go anywhere without a BOOTMGR, and given your positive response, I will move forward with GPT/UEFI :)

Cross your fingers for me ;)

Thanks a lot for all the info.
I'll be back to confirm outcome either way

---

### Post by javierdl on 2016-09-20
So I decided to try. I switched the USB driver to Legacy.
 But it didn't take me far.
 It loaded this: 
> GRUB4DOS - then many numbers here
 Windows NT6 Setup
 1 Second part/continue NT6 Setup (boot first internal disk)

 Then, it switched to a black screen with a blinking underscore.

 So much for that!
 What now? 
 Help!!!!! Lol :(

---

### Post by sudodus on 2016-09-20
Let us get everything clear!

- What is working now?

- Can you boot Windows from the HDD?

- Can you boot Windows from the SSD?

- Can you boot Ubuntu from USB?

- Did you try to install Ubuntu, when the disk with Windows was disconnected?

---

### Post by oldfred on 2016-09-20
There is no grub4dos in Windows nor Ubuntu. That has to be some third party boot loader that added it? And grub4dos will not work with UEFI.

Black screen is often a video driver issue. In addition to sudodus' questions what video card?

---

### Post by javierdl on 2016-09-20
What is working now?
**The only OS that is still working is Ubuntu Studio, in the HDD (unplugged now).**

 - Can you boot Windows from the HDD?
**No. Because 1. HDD is now unplugged, 2. There's no Windows installed anywhere in that computer at the moment.**

 - Can you boot Windows from the SSD?
**No. I am trying though. Refer to the previous post please.**

 - Can you boot Ubuntu from USB?
**Yes.**

 - Did you try to install Ubuntu, when the disk with Windows was disconnected?
[B]I did try before as you may have seen in a previous post above. But for clarity sake, I'm trying to install both OSs in the same SSD drive. 

Should I infer from your question that it could be easier to install them separated, one per drive? I hope not, because then that means that (at least for now) I'd have to put one of them in a regular HDD.[/B]

I will get another report of the present drives status once I get home in about 6 hours

---

### Post by javierdl on 2016-09-20
> **oldfred said:**
> ...Black screen is often a video driver issue. In addition to sudodus' questions what video card?

Oh, that reminds me, someone recommended me to use the motherboard graphics while installing the OS, just to keep things simple. Was it you?
I'll do that. Not sure where I'll plug the monitor cable to though. I'll have to wait until I'm at home to see it.

---

### Post by javierdl on 2016-09-20
Ok, so here is the latest report:

```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sdb        1.5G  1.5G     0 100% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow            7.9G   59M  7.8G   1% /
tmpfs           7.9G  220K  7.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs           7.9G  4.0K  7.9G   1% /tmp
tmpfs           1.6G   84K  1.6G   1% /run/user/999
ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE  LABEL   UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                    sda    111.8G root  disk  brw-rw----
&#9500;&#9472;sda1                                                                 &#9500;&#9472;sda1  48.3G root  disk  brw-rw----
&#9492;&#9472;sda2 ext4    Linux   5f927a85-2db9-4fd3-bdfb-22ac7ea5af50            &#9492;&#9472;sda2  63.5G root  disk  brw-rw----
sdb    iso9660 Ubuntu 16.04.1 LTS amd64
&#9474;                      2016-07-19-21-27-51-00               /cdrom     sdb      3.8G root  disk  brw-rw----
&#9500;&#9472;sdb1 iso9660 Ubuntu 16.04.1 LTS amd64
&#9474;                      2016-07-19-21-27-51-00                          &#9500;&#9472;sdb1   1.4G root  disk  brw-rw----
&#9492;&#9472;sdb2 vfat    Ubuntu 16.04.1 LTS amd64
                       0F7B-9366                                       &#9492;&#9472;sdb2   2.3M root  disk  brw-rw----
sr0                                                                    sr0     1024M root  cdrom brw-rw----
loop0  squashf                                              /rofs      loop0    1.4G root  disk  brw-rw----
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Patriot Torch LE (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      1049kB  51.9GB  51.9GB               Win10  boot, esp
 2      51.9GB  120GB   68.2GB  ext4         Linux


```

---

### Post by oldfred on 2016-09-20
Your sda partitioning does not make sense. It says gpt, but only have two partitions. That might work with BIOS/MBR.
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 


Windows only boots with gpt partitioning in UEFI boot mode and needs multiple extra partitions.
Ubuntu also needs the same ESP - efi system partition as Windows uses for UEFI boot. 
Or if on gpt and booting in BIOS boot mode you must have a bios_grub partition for grub to correctly install.

For both Windows & Ubuntu how you boot install media is then how it installs. So if you want UEFI/gpt be sure to boot installer in UEFI mode.
Or if you want BIOS, boot installers in BIOS boot mode.

 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by sudodus on 2016-09-21
> **javierdl said:**
> ...
 - Did you try to install Ubuntu, when the disk with Windows was disconnected?
**I did try before as you may have seen in a previous post above. But for clarity sake, I'm trying to install both OSs in the same SSD drive. .**

Thanks for making this chear :-)
> 
Should I infer from your question that it could be easier to install them separated, one per drive? I hope not, because then that means that (at least for now) I'd have to put one of them in a regular HDD.
...

Yes, I think it is easier to install Ubuntu and Windows separately. But it should also be possible to install them together. It it more complicated in new computers than in old computers. I think Microsoft and the manufacturers make it complicated because they want to keep people from doing what you intend to do.

You have a GUID partition table, GPT, in the SSD now. That works, if you boot in UEFI mode and install Windows. But I think Windows wants an MSDOS partition table, when installed in BIOS mode.

There is no separate EFI partition, which you should have, if you intend to boot in UEFI mode. That partition should have a FAT32 file system and a boot flag. Windows itself wants an NTFS file system.

Windows is able to create partitions and file systems, but it will grab the whole drive, and you have to shrink the Windows partition afterwards to create unallocated drive space, where you can create partitions for Ubuntu. Use Windows tools to shrink the Windows partition.

This is probably the easiest way:

1. Install Windows

2. Create space for Ubuntu (with Windows tools). Leave the unallocated drive space as it is.

3. Reboot Windows and let it notice the change of its partition.

- Check that Windows works correctly
- Turn off secure boot (in the UEFI-BIOS menu) and fast boot (a kind of hibernation in Windows).
- Check that Windows works correctly

4. Backup Windows as it is at this stage (makes it faster to get back, if things get damaged later on).

5. Boot from Ubuntu live system from the USB drive.

6. Use gparted (in Ubuntu live) to create partitions for Ubuntu.

- at least a root partition with the ext4 file system and a small swap partiiton
- maybe also a data partition, if you want to share data with Windows. In that case, the data partition should have the NTFS file system.

7. Start the installer (in Ubuntu live) and at the partitioning page: select ***Something else***, and select the partitions you created with gparted for root '/' and swap. Do not worry about the data partition.

8. Reboot.

9. Fix things if necessary.

10. Decide how you want to backup your new dual boot system and start doing it at once.

---

### Post by javierdl on 2016-09-21
[SIZE=2]**Finally got Win10 installed!**[/SIZE]
I didn't say it, but I did try installing Win10 a couple days ago, unsuccessfully. I got an error message saying:
"Windows 10 cannot be installed on this partition. The partition is an EFI system partition."
At that time there were only 2 partitions: 
1. NTFS with a boot/ESP flag (for Win10), and 
2. Ext4 (for Ubuntu).

Now that I had:
a small 200 Mb partition with Fat32/Primary and a boot/ESP flag, 
200 Mb of unallocated space, 
and the rest for NTFS/Primary.
It worked! No complaints this time!
I have updated Windows Defender and it's doing a quick scan. 
Next I'll create a Restore point right away.
I'll use it for a couple days to ensure everything is running ok.
Then next time I have a chance I'll install Ubuntu too, in about a week. Should this linger, I'll just wait for 16.10 to be released next month.
Also, I still have to re-plug the HDD with Ubuntu Studio. I imagine I'll have to do some GRUB fixing, I hope not.

Thank you all for your amazing help, as usual!
oldfred, sudodus, and Bucky Ball :)

---

### Post by sudodus on 2016-09-21
Congratulations to this first step, and welcome back next week, when it is time for you to install Ubuntu alongside Windows :-)

---

### Post by oldfred on 2016-09-21
I might stay with 16.04 LTS, unless you want to reinstall regularly.
 
I use the current newest LTS as my main working install, but usually install each new release just to see what changes and that it works on my configuration. I just use another 25GB partition for / (root).

---

### Post by javierdl on 2016-09-21
sudodus, 
Thank you so much for extending that welcome for the near future, I certainly appreciate that, God knows I'll need it ;)

oldfred,
Thanks for the suggestion :)
I understand LTS stands for Long Term Support. But to be sure I understand how it works about the LTS and the rest: 
1. Is it that the LTS has the same newest added features/fixes as one that's a non-LTS that was just released? Except that all you do to get those features/fixes is receive the updates, as opposed installing from fresh?
Or 
2. Does the LTS gets mostly fixes and minor features added? And if you want the actual best features too, then you have to go with a non-LTS?

J

---

### Post by oldfred on 2016-09-21
It used to be that nothing was updated with the LTS versions other than security fixes.
Now versions include HWE - hardware Entablement stack. Which is newer kernel & support software as new hardware needs newer kernel. But most software applications are not updated. Firefox now is updated as that seemed easier. But with so many applications they cannot test all with each kernel.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

 Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I was updating every 6 months & my spouse complained about too many changes. So now I update every 2 years. But I do have the newer version to see if anything really has changed that much.

---

### Post by Bucky Ball on 2016-09-22
> **javierdl said:**
> And if you want the actual best features too, then you have to go with a non-LTS?

Wouldn't have put it like this. If you want the 'newest' features then go with the newest release. That is not to say it is the 'best' release or the updated apps in it are 'the best'. They're just the newest. In some cases, they could be buggier than the older version which may have been working perfectly on an older release.

Once you've been here awhile you'll soon realise 'newest' does not always equal 'best'. 'Newest' can sometimes mean endless hours of troubleshooting and hair pulling.

LTS releases are intended for work and production machines where stability is the aim and downtime undesirable. Machines like this don't need to be on the bleeding, or even cutting edge, so 'newest' is not exactly a priority. The support life is five years so that says something. Good luck. :)

---

### Post by sudodus on 2016-09-22
> **Bucky Ball said:**
> Wouldn't have put it like this. If you want the 'newest' features then go with the newest release. That is not to say it is the 'best' release or the updated apps in it are 'the best'. They're just the newest. In some cases, they could be buggier than the older version which may have been working perfectly on an older release.

Once you've been here awhile you'll soon realise 'newest' does not always equal 'best'. 'Newest' can sometimes mean endless hours of troubleshooting and hair pulling.

LTS releases are intended for work and production machines where stability is the aim and downtime undesirable. Machines like this don't need to be on the bleeding, or even cutting edge, so 'newest' is not exactly a priority. The support life is five years so that says something. Good luck. :)

+1

---

### Post by javierdl on 2016-09-22
I'm so glad I asked.
Thank you so much for that info guys :)
I'll stick with the LTS then!

J

---

