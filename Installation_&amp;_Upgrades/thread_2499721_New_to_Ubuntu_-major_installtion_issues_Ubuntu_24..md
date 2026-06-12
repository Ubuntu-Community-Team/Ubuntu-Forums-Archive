---
title: "New to Ubuntu -major installtion issues Ubuntu 24.10"
date: 2024-08-07
forum: Installation &amp; Upgrades
---

### Post by cloudrunner77 on 2024-08-07
I am new to Linux.  I am a long time Windows user and a former desktop support engineer for the better part of 2 decades.  I have an issue that I have searched high and low for an answer and I can't find one.

I have limited space on my Windows boot drive.  I am not made of money.  I am disabled and I am on a fixed income.  Buying anything but necessities is out of the question.  So I want to boot from another drive on my system.  I want to try my best to transition to Ubuntu because I am sick of windows.  I chose Ubuntu because I use Studio One 6.6 and it is now available for Ubuntu 24.X with Wayland.  And this is critical for me because I do not want to switch back and forth between Linux and windows.  I am telling you all of this to head off some suggested solutions to my issue.  As I said I want to transition to Ubuntu as quickly as possible.

That said My largest free space is one a Raid array that I use for my fast storage.  It consists of 4 smaller SSDs connected to a hardware RAID controller.  Win 11 device manager says it is a Marvell 92xx 6gb controller.  It is made by Vantec.  I tried installing Ubuntu and when it got to creating the boot partition the Raid controller and those partitions do not show up.  I am 1) Looking for a driver to support this device and 2) figuring out a way to install it pre install so that the device is available.  I have read in various places that you can't boot from a Raid array but I have seen it done in server environments, so I think that is bogus info.

I have regular HDDs for other storage in my system but they are slow.  I want and need the SSD performance.  I do graphic work and create music in Studio One.  The performance hit is not acceptable for either.  I do not play games anymore so that isn't an issue.

SO... can someone please tell me how I can use a partition on that Raid array to boot from.  It has to be possible.  I am willing to be patient in setting it up.  I am tech saavy and can follow instructions.  I am just a complete noob with Linux.  My sole experience is with some utilities I have used in pre boot environments.

---

### Post by TheFu on 2024-08-08
Not all RAID devices are supported.  In Linux, LSI RAID cards (and rebranded versions used by HP/Dell/IBM) are the normal HW-RAID HBA in servers.

You need to learn that vendors don't make drivers for Linux for all their devices.  In general, the cheaper the device, the less well it is supported by Linux.  Blame the vendors.  Sometimes **really**, **really** popular devices will eventually get Linux support because someone in the community has the skill and time to port code or find code for a similar chip. It is often a personal itch for that person.  Then they post their driver and how-to compile it on gitlab for the world to use - at their own risk.

For home Linux users, SW-RAID has been the rule for almost 20 yrs.  It is more flexible, just as fast, thanks to our CPUs, and allows easy migration to different systems since it isn't tied to hardware.

Lastly, there's something called "Fake-RAID", which is provided by motherboards.  This has  all the limitations of HW-RAID, but still uses the CPU to do most of the work.  I've always avoided Fake-RAID, since if a motherboard fails, the data is generally gone. Inaccessible. Unless an exact same model and version of the motherboard are found.  The same applies to HW-RAID.  Enterprises can have a spare on-sites for when the RAID card fails. Most home users do not.

If you are going to dual boot, maybe the best option is to have a small OS boot device (non-RAID) and hopefully find a driver that will support the RAID post-boot.  Google found this [https://unix.stackexchange.com/questions/218650/drivers-for-marvell-88se9230-sata-controller-on-linux](https://unix.stackexchange.com/questions/218650/drivers-for-marvell-88se9230-sata-controller-on-linux) which says the chips in the marvell-88se9230 are in the kernels already. 

Beware that "support" and "boot support" are very different in Linux.  In general, if you see the RAID controller BIOS BEFORE grub, then you can treat it like any HDD.  If special drivers need to be used at OS boot time to see the hardware, then you probably cannot boot from it.

If you want RAID1 for the OS (not the boot, EFI, FAT32 partition) then you can install using LVM to a single device, then add RAID1 using LVM lvconvert later to make it RAID1.  That's for everything except the EFI  and /boot/ partitions.  I have a 22.04 server setup this way. It isn't using EFI to boot, however.  Don't know if this will help, but here's the storage layout using LVM with RAID1 for /.
```
$ lsblk 
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
```
and the fdisk version (simplified to remove all the LVM objects, better seen above):

```
$ sudo fdisk -l
Disk /dev/vda: 15 GiB, 16106127360 bytes, 31457280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: CCD1DD1C-1587-4B4E-AAB3-8FC49103FC2B

Device       Start      End  Sectors  Size Type
/dev/vda1     2048     4095     2048    1M BIOS boot
/dev/vda2     4096  1576959  1572864  768M Linux filesystem
/dev/vda3  1576960 29358079 27781120 13.2G Linux filesystem


Disk /dev/vdb: 15 GiB, 16106127360 bytes, 31457280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6AD324FD-9704-4973-AD17-DF8258AA0888

Device       Start      End  Sectors  Size Type
/dev/vdb1     2048     4095     2048    1M BIOS boot
/dev/vdb2     4096  1576959  1572864  768M Linux filesystem
/dev/vdb3  1576960 29358079 27781120 13.2G Linux filesystem
....

```
The df -Th .... 
```
$ dft
Filesystem               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0 ext4  9.8G  4.6G  4.7G  50% /
/dev/vda2                ext4  739M  290M  395M  43% /boot

```

The full LVM layout using LVM tools:
```
$ sudo pvs
  PV         VG    Fmt  Attr PSize   PFree
  /dev/vda3  vg-00 lvm2 a--  <13.25g 2.24g
  /dev/vdb3  vg-00 lvm2 a--  <13.25g 3.24g

$ sudo vgs
  VG    #PV #LV #SN Attr   VSize  VFree
  vg-00   2   2   0 wz--n- 26.49g 5.48g

$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-ao**r**--- 10.00g                                    100.00          
  lv-swap vg-00 -wi-ao----  1.00g
```
Note that lv-0 is RAID.  lv-swap isn't on RAID. I don't see the point in RAID for swap.  As a server, used to play with different minimal stuff, I didn't give it much storage. It doesn't have any GUI.  No GUI means less than 5GB of storage is needed. That's actually very bloated compared to some other distro server installs.

Installing with LVM isn't trivial. Canonical's installers make doing it a pain, so I setup the LVM storage how I want it before doing the install to disk using a custom script that's only for my systems and needs.  Everyone has different needs for their different system.  The u22.04 server shown above is very simple and not what I use in production for LVM layouts.

Anyway, hopefully, I've provided some other ideas for consideration.  You might want to consider using ZFS if you are just starting out in Linux. There are many great things about it, including RAIDz and RAIDz2.  Alas, Windows doesn't know anything about ZFS.

---

### Post by oldfred on 2024-08-08
You should not be installing 24.10 as that is in development and may break. It will go many updates. And is not a long term support version (LTS) and will need update/reinstall in 9 months.
Better to install 24.04LTS and get longer support.

If you have Windows 11, I assume it is a newer UEFI based system with gpt partitioning.
With UEFI, you have to have an ESP - efi system partition for booting. That is FAT32 and must not be inside LVM nor RAID, so UEFI can read it directly UEFI only has driver for FAT32.

Most with server or server type installs, have a separate /boot partition that must be Linux formatted, often ext4, even if other partitions are in one of the more advanced Linux formats.
If dual booting, often have a shared NTFS partition. But Windows has to have bitlocker off, fast start up off and not need chkdsk to work with the Linux NTFS driver.

You do not need a lot of room for the / (root) partition & /boot, if using it. Ubuntu does now use snaps for many things and then you do need more space. I currently use Kubuntu, with no snaps and use 10GB on my external SSD used with laptop and 16GB on main working desktop system. I typically allocated 35 to 40GB  for / including /home, but all data is in separate data partition. But have seen some users with default snaps & snap backups using as much as 20GB just for snaps. So even then only 60GB may be needed for /. 

You can shrink your Windows NTFS partition by 60GB or so, with Windows tools and install / on that drive. It will use same ESP as Windows. Then you can mount your RAID, if you can get drivers to work.

Note that RAID is not backup, but was used for uptime with servers. 
Often now SSDs & newer NVMe SSDs are faster, than RAID with HDD.

---

### Post by TheFu on 2024-08-08
I completely missed the 24.10 mention.  

If you aren't a Linux expert, you shouldn't be using this alpha code and even when it is released in October, people with less than 2 yrs of daily Linux use shouldn't touch it.  

Stick with LTS releases.  Today that would be either 22.04 or 24.04. No others should be considered, unless you just want to play for a few weeks with a distro.  For daily use or "production" use, stick with LTS releases and plan to migrate/reinstall new the current LTS every 2-3 yrs.

---

### Post by yancek on 2024-08-08
According to a comment by the lead devloper at the presonus forum (link below), you should be able to use it on 24.04.

  [https://forums.presonus.com/viewtopic.php?f=419&t=53767&p=316479&sid=b764621e1e0e6994fa1fcf36a11b74db](https://forums.presonus.com/viewtopic.php?f=419&t=53767&p=316479&sid=b764621e1e0e6994fa1fcf36a11b74db)

Did you read the Linux-Getting Started page at the link below?  It refers to 6.5 so I'm not sure how much help it would be.  I do see the comment on that page that it is for 'advanced Linux user' for whatever that's worth.

[https://support.presonus.com/hc/en-us/articles/19214558269581-Linux-Getting-Started](https://support.presonus.com/hc/en-us/articles/19214558269581-Linux-Getting-Started)

---

### Post by cloudrunner77 on 2024-08-09
Thanks for the advice on versions.  I could have sworn the download said it was LTS... but I defer to the experienced users all day/every day. 

I am visually impaired and I require high contrast color schemes to be able to read anything on a computer.  I have my Win 11 set up that way.  I found the installer almost impossible to read.  Are there any command line switches I could use to alter the black text of a white background?  It was painful trying to even get through the first part of the install.

I will see what I can do about clearing space on my Win boot drive and shrinking the partition.  I am thinking I can get as much a 80 GB on there.  Even though I have a ton of software on the main partition for C drive.

Thank you again for the responses.

---

### Post by tea for one on 2024-08-09
> **cloudrunner77 said:**
> I am visually impaired and I require high contrast color schemes to be able to read anything on a computer.  I have my Win 11 set up that way.  I found the installer almost impossible to read.  Are there any command line switches I could use to alter the black text of a white background?  It was painful trying to even get through the first part of the install.
There are Accessibility options during the live boot process for Ubuntu 24.04 LTS
More info here [https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

---

### Post by TheFu on 2024-08-09
> **cloudrunner77 said:**
> Thanks for the advice on versions.  I could have sworn the download said it was LTS... but I defer to the experienced users all day/every day.  

Just to clarify LTS.

LTS releases happen in even years, month of April.  So the ".04" is April.  ".10" is October - never an LTS.
Even years.  2018, 2020, 2022, 2024, 2026, 2028 ... there is a clear pattern.

No other release will be LTS. Never in odd years and never in October. There has been 1 exception and that was long ago.

---

