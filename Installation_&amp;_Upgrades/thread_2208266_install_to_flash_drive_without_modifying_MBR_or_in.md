---
title: "install to flash drive without modifying MBR or installing GRUB"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by aspergerian on 2014-02-27
Recently, I tried to have my HP dv7 run Xubuntu 12.04 from an external HDD (1tb). Converting the drive to GPT partitioning was also enacted. Sudodus and oldfred were very helpful ([here]("http://ubuntuforums.org/showthread.php?t=2204995")). I have not yet attempted chainloading as recommended by sudodus ([here]("http://ubuntuforums.org/showthread.php?t=2196858")). Instead, I want to try running Xubuntu 12.04 on my dv7 via a USB flash drive. My dv7 does boot Knoppix 7.2.0 from USB - via a flash drive and via Knoppix CD in an external CD/DVD player. If the soon-to-be created flash drive doesn't work to boot dv7 into Xubuntu, I'll then try chainloading or will try installing Xubuntu to the thumb drive while the dv7's internal HDD is removed. 

I prefer to install to USB drive without the procedure changing the boot process on the dv7. Two possibilities seem available: [LinuxLive USB Creator]("http://www.linuxliveusb.com/") and [Universal USB Installer]("http://www.pendrivelinux.com/"). Two questions: Will either of those two programs install to the flash drive w/o modifying MBR or installing GRUB on dv7? Is either of the two programs preferable?

---

### Post by SuperFreak on 2014-02-27
I had look at  LinuxLive USB Creator and it looks interesting. I use a similar USB Creator called [EASY2Boot]("http://www.rmprepusb.com/documents/rmprepusb-beta-versions") which supports multi boot and  I can install from my Ubuntu machine with some caveats. From what I could see on the LinuxLive USB Creator it can only be installed from a Windows machine, is that right?
I have never changed the Grub menu or MBR on my machine with Easy2Boot but my PC is Linux only

---

### Post by aspergerian on 2014-02-27
Thanks for mentioning Easy2Boot. I also have an Acer 1410 running only Xubuntu and could install by that instead of by the dv7. Yes, LinuxLive USB Creator can only be installed from a Windows machine. Another option is to buy a ready made 
[Xubuntu 12.04.4 LTS - 8GB USB Flash Drive (64-bit PC)]("https://www.osdisc.com/products/linux/xubuntu/xubuntu-12044-lts-8gb-usb-flash-drive-64bit-pc.html"). 

I'm concerned about LiveUSB limitations (if any) regarding persistence, saving files, adding programs, and Xubuntu updates.

---

### Post by SuperFreak on 2014-02-27
I think Easy2Boot allows persistence on some distros(I haven't tried it). It is fairly easy to use once set up (set up instructions for Linux are on linked site [HERE]("http://www.rmprepusb.com/tutorials/114")   and once that is done you just add ISOs of the distros you want into the appropriate folder on your USB. The only issue that will crop up is that the ISO files have to be contiguous on the USB or they won't load when you boot to Easy2Boot. The simplest way to fix this is to have the associated program RMPrepUSB installed on a Windows machine as it has a simple utility to make the ISOs on the USB contiguous. I am trying now to find a simple way of doing this on a Linux machine so Windows is not needed at all. Will update when I know more.

---

### Post by oldfred on 2014-02-28
You do have to have a boot loader somewhere.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
Live session failed to start from USB with persistence enabled
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Grub is the boot loader for Ubuntu full install, but the live Installer uses Syslinux which is more of a Windows type boot loader and works from FAT32 flash drives. Windows type boot loaders expect a boot flag and more boot code in a PBR or partition boot sector.

---

### Post by aspergerian on 2014-03-16
I raised the issue in a different forum, as a suggestion:
> **aspergerian said:**
> Canonical could develop an installation procedure that allows a person to install to a USB drive (eg, flash or HDD) and do so without modifying the MBR on sda. Removing or disconnecting an internal HDD seems excessive for what instead could/should be a accomplished by a GUI choice:
_install as dual boot and modify MBR or GRUB on sda.
_install only to external device without modifying MBR or installing GRUB on sda.{thread [here]("http://ubuntuforums.org/showthread.php?t=2210728")}

If the two responders read my question clearly, including: "install only to external device without modifying MBR or installing GRUB on sda", then I wonder how this is done. Here are the responses:

The first response surprised me:
> **coffeecat said:**
> You can do that already with the GUI installer - it's been possible for years. I've done that a few times myself, installing to a USB drive and installing grub only on the mbr of the USB drive.

I queried:
> **aspergerian said:**
> Are you referring to a full install to the USB drive or to an install which includes the iso file as a necessary part of the USB-drive installation?

Responses to query:
> **coffeecat said:**
> A full bootable install.

> **cariboo907 said:**
> I'm currently running Trusty Gnome-shell on a 32GiB usb thumb drive, this is a full install:

```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        28G  3.7G   23G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G   12K  2.0G   1% /dev
tmpfs           404M  1.2M  403M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  380K  2.0G   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sr0        7.5G  7.5G     0 100% /media/cariboo/<RED_2>
```

This is the fdisk -l output, the drive I'm running from is the second one, /dev/sdb:

```
sudo fdisk -l
[sudo] password for cariboo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531344     9764648+  83  Linux
/dev/sda2        19531776    23437311     1952768   82  Linux swap / Solaris
/dev/sda3        23437312   488396799   232479744   83  Linux

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000151fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    58593844    29295898+  83  Linux
/dev/sdb2        58595326    62529535     1967105    5  Extended
/dev/sdb5        58595328    62529535     1967104   82  Linux swap / Solaris
```

---

### Post by oldfred on 2014-03-16
All the automatic installs assume one drive and simple / & swap install. Then grub is installed to sda.

If more than one drive whether internal or external, USB hard drive or flash drive, you have to use Something else or manual install. That does require you to create partition(s), choose which drive you want grub boot loader installed into as it may be sda, or the second drive. Usually best to install to same drive as install especially with removable drives or flash drives, but some old systems only boot from sda and you have to install to that drive.

Something Else or manual install does require you to know or learn about partitions.

I always partition in advance as gparted is a bit easier to use. But I still have to use Something else to specify mount as /, /home or other, format as ext4 for each partition and location of boot loader. I now use gpt partitioning on all drives  for future use with UEFI, but current use with BIOS. But Windows on internal drive will only boot from gpt with UEFI.

---

### Post by aspergerian on 2014-03-17
oldfred,

Thank you for your most recent replies. Perhaps a narrower focus would be helpful. My goal is to create a bootable USB drive which will boot an HP dv7 with 6 gig of RAM. The dv7 is not UEFI, and I prefer a full install to the USB drive (eg, 32 gb flash, new) and would prefer that during the installation, sda (my dv7's internal HDD) would not be modified in regard to its current MBR.

Although I have installed Ubuntu and Xubuntu ~15-20 times, those events have always used sda and included no external HDDs. For most of these installs, I have selected Something Else and have used the install-CD's (DVD's) partitioning mechanism to create /, /home, and swap. My endeavor with the 1-TB HDD led us to dealing with GPT partitioning and related GRUB-complexities [here]("http://ubuntuforums.org/showthread.php?t=2204995"). Using a 32 gb flash removes GPT from what is needed for a full install to the USB drive.

My dv7 boots 3 flash drives obtained from [OSDisc]("http://www.osdisc.com"): (Knoppix, Xubuntu 12.04, and PCLinuxOS), so we know that the dv7 is capable of booting from its USB ports. Apparently, I have not noticed the point at which a Something Else install allows me to choose the drive on which to install GRUB.

Perhaps someone can provide a link for screenshots or instructions for the installation parameters I have specified.

Perhaps someone can specify the point at which I can select *install grub only to sdb* during a Something Else install to the USB drive (sdb).

> **oldfred said:**
> All the automatic installs assume one drive and simple / & swap install. Then grub is installed to sda. If more than one drive whether internal or external, USB hard drive or flash drive, you have to use Something else or manual install. That does require you to create partition(s), choose which drive you want grub boot loader installed into as it may be sda, or the second drive. Usually best to install to same drive as install especially with removable drives or flash drives, but some old systems only boot from sda and you have to install to that drive...

---

### Post by oldfred on 2014-03-17
This is my install to a partition on sdc, I am overwriting an older install that was previously labeled. If you look at the bottom of screen shot it still shows a combo box install to sda drive. You have to change that to the correct drive.

This is my 32GB flash drive. I have both efi for future use and bios_grub for current use. First partition of 15GB is install and second is just data.

```
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys

```

---

### Post by SuperFreak on 2014-03-17
I do have a full install on a USB stick of 14.04 with separate root and home partitions. I am forced to use USB 2.0 connections on my computer with it, because for some reason my computer will not boot to USB 3 devises only USB 2. The reason I mention this is that with the USB 2 setup it runs painfully slow and is almost useless for testing out 14.04 (which was my intention). So if you plan to use USB 2   expect a slow install

---

### Post by oldfred on 2014-03-17
I find on my system with only USB ports install or any writes are very slow. But once installed it is functional, just not as speedy as hard drive. Once an app is in memory it is really just as fast as Linux caches recent apps in RAM.
I also find a USB3 flash drive is about 10% faster even on my USB2 ports.

But I use ext4 but turn off journal so that writing is eliminated and change to noatime in fstab.

 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

Update - Another link showing combo box for grub boot loader install.
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29)

---

### Post by aspergerian on 2014-03-18
old fred,

Thank you for the additional responses, including the image! With the intent to keep the install simple for my now "middle aged" HP dv7 with 6 gig of ram, I'm tempted to try the following partitions on a 32 gb USB flash:

8 gb as /
14 gb as /home
9 gb as nfts (for saving when w7 is running)

I notice that bios_grub seems to have a purpose I won't be needing ([here]("https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29")):
> BIOS/GPT Notes: If the BIOS is setup to boot the disk in Legacy/mbr mode, installing GRUB2 on a GPT (GUID Partition Table) disk requires a dedicated BIOS boot partition with a recommended size of at least 1 MiB. This partition can be created via GParted or other partitioning tools, or via the command line. It must be identified with a bios_grub flag. The necessary GPT modules are automatically included during installation when GRUB 2 detects a GPT scheme. 

Is my proposed partitioning scheme likely to be functional?

Will I need to specify one partition or another with Manage Flags during install?

---

### Post by oldfred on 2014-03-18
Only if partitioning with gpt(GUID) do you need an efi partition if booting in UEFI mode or a bios_grub partition if booting in BIOS mode.
I now partition all new drives including my larger flash drives with full installs with gpt and put both efi &  bios_grub partitions on them.

But if just booting in BIOS mode you can use MBR(msdos) partitioning with the partitions you show.
With 32GB flash drive I might not have separate / & /home. You may run out of room in one or the other and having shared unused space may offer some advantage.
Your 8GB for / may work, but you should plan on regular housecleaning of logs & older kernels. And you may not have room for installing lots of software. I do not use my flash drive a lot. It is more for an emergency boot incase of issues with main install.

---

### Post by aspergerian on 2014-03-21
Yesterday I installed Xubuntu 12.04.3 onto a 32gb flashdrive, using my Acer 1410 netbook and an HP external DVD. I used /, /home, and nfts. The flash drive booted the 1410 and then booted the larger HP dv7. While running on the dv7, Xubuntu recognized the need for a Broadcom wifi driver and installed it (it works). Today I used the same procedure on a 320gb USB HDD, and Xubuntu 12.04.3 USB-boots runs well on the dv7. Thanks again to oldfred and sudodus for nudging me along.

---

### Post by oldfred on 2014-03-23
Glad you got it working. :)

---

