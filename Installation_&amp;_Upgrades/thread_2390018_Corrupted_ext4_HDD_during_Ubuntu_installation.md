---
title: "Corrupted ext4 HDD during Ubuntu installation"
date: 2018-04-24
forum: Installation &amp; Upgrades
---

### Post by webber42 on 2018-04-24
Hello,

I have installed Lubuntu 16.04 on a new Windows 10 machine.  I did some mistakes during the install.. I wanted to keep Ubuntu as primary while win10 as secondary - But did some mistakes with the UEFI and ended up messing up with the Win10 partition. After few attempts, I managed to only have Lubuntu 16.04 working from a USB stick on this machine now.. The 1Tb hdd is all ext4 now but has some 17Gb used..

I am now trying to install Win 10 as Secondary while keeping Lubuntu 16.04 primary from the USB stick. But I want to recover the 17Gb on the installed 1Tb HDD if possible.  But the problem is that 17Gb seems unreadable.. And also getting some e2fsck errors when trying to resize the 1Tb partition...

Here are some outputs.. 

```
700-15ISK:~$ sudo fdisk -l


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 635C934E-A96C-4266-BD7B-7CFA12506907


Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem




Disk /dev/sdb: 57.9 GiB, 62109253632 bytes, 121307136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa764d48d


Device     Boot   Start       End   Sectors  Size Id Type


/dev/sdb1          2048   3999743   3997696  1.9G 82 Linux swap / Solaris
/dev/sdb2       3999744 121305087 117305344   56G 83 Linux

[HR][/HR]700-15ISK:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=6a6ab507-34c2-47a1-9ae3-8bb9a6814c27 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=12BE-EF3C  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdc1 during installation
UUID=b41e6898-55ce-4efc-a683-0141ca5806aa none            swap    sw              0       0
[HR][/HR]700-15ISK:~$ sudo mkfs -n /dev/sda2
mke2fs 1.42.13 (17-May-2015)
/dev/sda2 contains a ext4 file system
    last mounted on /media/humanoid/3dfca893-fa27-4094-98b0-086695db9500 on Tue Apr 24 02:50:14 2018
Proceed anyway? (y,n) y
Creating filesystem with 244059136 4k blocks and 61022208 inodes
Filesystem UUID: 2487d1f0-dd16-4444-bf55-ce89b6b6d277
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848





```

---

### Post by oldfred on 2018-04-24
You show sdc & sda as drives, do you have 3 drives or is one your flash drive installer?

Post this:
       
 lsblk -f 

Often with multiple drives, better to disconnect other drives and install just to the one drive, unless you really want both installs on same drive and other drives as data only. Even my data only larger drives have a small install of Ubuntu, possibly test or emergency boot.

---

### Post by webber42 on 2018-04-24
sdc could be the live usb which I used to setup initially. But I never used it afterwards and have no plans to do so.


```
700-15ISK:~$ lsblk -f
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sdb                                                      
&#9500;&#9472;sdb2 ext4         6a6ab507-34c2-47a1-9ae3-8bb9a6814c27 /
&#9492;&#9472;sdb1 swap         b41e6898-55ce-4efc-a683-0141ca5806aa [SWAP]
sda                                                      
&#9500;&#9472;sda2 ext4         3dfca893-fa27-4094-98b0-086695db9500 /media/userxx/3dfca893-fa27-4094-98b0-086695db9500
&#9492;&#9472;sda1 vfat         12BE-EF3C                            /boot/efi

```

---

### Post by oldfred on 2018-04-24
Is your 17GB of data in / or sdb2 or your data partition sda2 which you have reformatted?

Did you run the full fsck like these 2 commands?

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb2

---

### Post by webber42 on 2018-04-24
The 17Gb is in sda2.

```
700-15ISK:~$ sudo parted -l


Model: ATA TOSHIBA MQ02ABF1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4




Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdb: 62.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2048MB  2047MB  primary  linux-swap(v1)
 2      2048MB  62.1GB  60.1GB  primary  ext4



```

No i have not run any fsck so far
So as per your advise, should I be running > [COLOR=#000000]sudo e2fsck -C0 -p -f -v /dev/sda2 ?[/COLOR]  Also what is the consequence of running this command ? Would I be able view the contents then ?

---

### Post by oldfred on 2018-04-24
If you reformatted partition, I am not sure there will be anything to recover.

Normally you run the e2fsck commands first.
Then testdisk and/or photorec to see if you can recover data.

---

### Post by webber42 on 2018-04-24
I am having trouble with e2fsck

```
700-15ISK:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
/dev/sda2 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!


700-15ISK:~$ apt-cache policy e2fsprogs
e2fsprogs:
  Installed: 1.42.13-1ubuntu1
  Candidate: 1.42.13-1ubuntu1
  Version table:
 *** 1.42.13-1ubuntu1 500
        500 http://uk-mirrors.evowise.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by oldfred on 2018-04-24
I have had that same error.

I formatted a partition with gparted from 18.04, but then tried to run fsck from 16.04.
Or as it says you need a newer version. Something in ext4 or e2fsck has changed enough that is now is not backwards compatible.

---

### Post by webber42 on 2018-04-25
I have e2fsck version 1.42.13 installed right now.  I originally formatted the HDD using a live USB, which I no longer have. So not sure which exact version of e2fsck is needed now for Gparted to work. Can anyone please suggest the correct version or a possible solution?

Thanks in advance.

---

### Post by webber42 on 2018-04-26
> **oldfred said:**
> I have had that same error.

I formatted a partition with **gparted from 18.04, but then tried to run fsck from 16.04.**
Or as it says you need a newer version. Something in ext4 or e2fsck has changed enough that is now is not backwards compatible.

I have uninstalled Gparted which I installed from the software center.  I have installed Gparted 0.31.0 manually to /usr/local, in hopes that e2fsck would update accordingly. But when I try to use Gparted 0.31.0, it still gives me the same e2fsck upgrade error... Still not sure what version e2fsck is needed..

---

### Post by webber42 on 2018-04-27
ok.. Trying a different approach. I am trying to run Gparted live USB.  But when I stick the Gparted USB and boot, nothing happens and gets stuck at Grub prompt.. 

I have disabled secure boot, disabled UEFI, USB is enabled and the boot order is USB first.. 

But when I stick back my 16.04 USB, everything boots fine.. How would I make it bootable with any live USB ?  Help Please

---

### Post by oldfred on 2018-04-27
I would think 18.04 flash drive is not correctly configured.
Or ISO not downloaded correctly.
Occasionally the brand of flash drive or port on system makes a difference.

Check that ISO is correct as downloaded.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

I almost always use zsync which only updates an ISO and verifies it is correct.

There are some other differences with 18.04. You may not to review to see if any apply to your configuration.
      [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

---

### Post by webber42 on 2018-04-27
@oldfred

I have verified the checksum and looks good. I have made another 18.04 live USB just to rule out the flash drive and I have used this in the past..

Could it be that it is not able to fetch the boot cfg file during bootup for the live USB's ?

This is what I see at the grub rescue
```
grub> ls
(hd0) (hd0,msdos1) (hd1) (hd1,gpt2) (hd1,gpt1)
```

---

### Post by oldfred on 2018-04-27
The Ubuntu live installer is configured for both BIOS boot using MBR and syslinux boot loader and with grub for UEFI boot. UEFI on all external devices only boots from /EFI/Boot/bootx64.efi. With the Ubuntu installer that file is a version of grub for the installer.

So from your UEFI boot menu you should get two boot options, one UEFI and one BIOS which may be just name of flash drive.
If Secure boot is on, you will only see UEFI boot option. 
Some systems boot either UEFI or Legacy/BIOS/CSM if Secure boot off.
Many systems require USB boot allowed setting to let anything boot from flash drive.

My motherboard does not have UEFI Secure boot setting per se, but has "Windows" and "Other". But fine print says use "Other" for Windows 7 as it does not support Secure Boot. So that really is the Secure Boot setting.

---

### Post by webber42 on 2018-04-27
I dont see the syslinux bootloader at all... both for Gparted live and 18.04 live - I am stuck at the Grub rescue..  I have disabled secure boot, disabled UEFI, USB is enabled and the boot order is USB first.. 

But when I stick my 16.04, it boots up fine...

---

### Post by oldfred on 2018-04-27
Is system not booting flash drive and just going to internal drive as default?
If UEFI/BIOS does not see USB drive or see USB drive with bootable info, it goes to next in boot order or back to internal drive.

---

### Post by webber42 on 2018-04-28
> **oldfred said:**
> Is system not booting flash drive and just going to internal drive as default? 
hmm.. It doesnt seem to do that for my 16.04 drive but it doesn't seem to work for any other USB drives irrespective of the OS

So now thinking if I should install a second linux alongside 16.04 on the same USB drive.. ? Is that a good option ? Or is it risky, jeopardizing my only working option at the moment ?

---

### Post by oldfred on 2018-04-28
Most installers erase entire flash drive and reconfigure it.
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
External SSD & flash drive issues  by TheFu
[https://ubuntuforums.org/showthread.php?t=2390247&p=13760330#post13760330](https://ubuntuforums.org/showthread.php?t=2390247&p=13760330#post13760330) 

I would try this:
      
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

Or this:

 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by webber42 on 2018-04-28
Still no joy..

I have formatted to FAT32 and extracted the Gparted live 0.31.0.1 and ensured the boot flag is also set.. I checked the md5 too just to be sure.. But When I stick the USB and boot, nothing works the same Grub prompt appears.. sigh

So I also verified if my system is efi or bios while running 16.04 on USB. I checked using 
***test -d /sys/firmware/efi && echo efi || echo bios***
and it returned efi...

So to sum it up.. My system is using efi settings and doesn't boot with a formatted FAT32 with all the iso extracted files with the boot flags set..  Not sure what my next trial should be..

---

### Post by oldfred on 2018-04-28
Does UEFI show the flash drive boot entries?
You should see UEFI:flash drive where flash drive is name or label of flash drive.
Just rebooting may not boot USB drive.
Did you check that UEFI secure boot is off & allow USB boot or allow full USB access or whatever your system calls it?

---

### Post by webber42 on 2018-04-28
> **oldfred said:**
> Does UEFI show the flash drive boot entries?
Where and how to check this ? 

>  You should see UEFI:flash drive where flash drive is name or label of flash drive.
This is to be checked in BIOS with the desired USB plugged in ?

>  Just rebooting may not boot USB drive.
I would usually shut the system down and then stick the USB in the slot and power it on...

>  Did you check that UEFI secure boot is off & allow USB boot or allow full USB access or whatever your system calls it?
Yes checked, checked & checked :)

---

### Post by webber42 on 2018-04-28
FYI.. snapshots of my drives

[URL="https://ubuntuforums.org/album.php?albumid=2646&attachmentid=279471"]https://ubuntuforums.org/album.php?albumid=2646&attachmentid=279471

[https://ubuntuforums.org/album.php?albumid=2646&attachmentid=279470](https://ubuntuforums.org/album.php?albumid=2646&attachmentid=279470)


[/URL]

---

### Post by oldfred on 2018-04-28
Cannot tell if sdb is UEFI install or BIOS install.
But just rebooting with flash drive plugged in, usually will not boot flash drive.
You have to go into UEFI boot menu, often f10 or f12, HP are escape & f9 to choose what entry to boot.

---

### Post by webber42 on 2018-05-09
So i plugged in Gparted USB and hit F12 during bootup and was given the boot menu.. From there i selected the Gparted USB and .. tada.. got the Gparted bootloader.. and after the default selection, was booted into Gparted live

Used Gparted from Gparted live and split my HDD partition successfully. :)

So i am guessing it is in UEFI install mode.

---

### Post by oldfred on 2018-05-09
From UEFI boot menu you should get two choice to boot, one usually UEFI:flash and the other flash where flash is name or label of flash drive.

With Ubuntu you also get different screens, this shows both:
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by webber42 on 2018-12-21
So now that I have Ubuntu running perfectly fine from the USB, and still have 300gb of unused space on my HDD. Can I install windows10 on 300gb from a windows live USB while also have Ubuntu as dual boot running from another USB ?  Thanks in advance.

---

### Post by oldfred on 2018-12-21
I would think so.
With Windows as with Ubuntu is it important to be sure to boot in correct mode. Either UEFI or BIOS/CSM/Legacy.
Windows only installs in UEFI boot mode to gpt partitioned drives and only in BIOS boot mode to MBR partitioned drives. So drive partitioning has to match install boot mode.
And if you force install in wrong mode, Windows will convert drive to correct partitioning, erasing it.

---

