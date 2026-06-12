---
title: "Ubuntu 13.10 install spins, 12.04.4 fails into grub"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by bradsturtevant on 2014-04-08
I 'm having problems with Ubuntu install because me thinks I've instructed BIOS to change boot order of the two disk drives on my computer. I setup BIOS to boot drive with id 1 first, then drive id 0.

I would really like to install 13.10 rather than 12.04.4 but install begins endless loop after message:

    Configuring bcmwl-kernel-source

The installer is not hung at this point. I can disconnect ethernet, add DNS name servers, etc.
Clicking on little arrow below Configuring bcmwl-kernel-source I see additional information about the spin cycle:

    ubuntu dbus [1399]:[system] Acquired the name org.freedesktop.UDisk2 on the system bus
    ubuntu dbus [1399]:[system] Activating service name='org.freedesktop.nm_dispatcher' (using service helper)
    ubuntu dbus [1399]:[system] Successfully activated service 'org.freedesktop.nm_dispatcher'

Some background
---------------

Why? I originally had Vista on drive 0 (C:), then installed Windows 7, 8, 8.1 on drive 1 (D:). Now, I'm a developer and want to utilize KVM (needs Intel® VT) along with bare metal hypervisor on home network.

My attempts have included installing CentOS 6.5 (no problem) to sort of establish ext4, etc. on hard disk, installing Ubuntu 12.04.4 which failed at last moment (after long spin cycle) saying GRUB could not be written (but for the most part installed), then trying to upgrade 12.04.4 to 13.10. Tried installing on first, second partition of disk drive 0 along with CentOS 6.5 (which can install fine on either partition, and dual boot ok). Also, tried 13.10 install with with 'update packages from Internet while installing', and install only from DVD files.

Working with a somewhat old (2009) Dell T7400 with dual E5410 Xeon procs, basic VGA (Radeon HD 6450), Broadcom 802.11g Network adapor on motherboard, dual ATA Hitachi HDP72502 SCSI 230GB drives. Storage controller is Dell SAS 6/iR Integrated Workstation Controller - driver from LSI v1.34.3.82.

Only odd thing about system that I can think of is that I am using BIOS to boot drive with id 1 first, then drive id 0. I originally had Vista on drive id 0, then installed Windows 8 on drive 1. Now I am trying install Ubuntu, CentOS on second drive in boot order (which is drive id 0).

---

### Post by oldfred on 2014-04-08
You should be able to boot from either drive, if hardware allows it. A few older systems would only boot from sda, or if an older IDE system if drives are correctly configured for cable select will it boot from either drive.

If you installed Windows on drive 1 when BIOS was configured to boot drive 0, did Windows put its boot partition on drive 0 even thought main install was drive 1?

Best to see lots of detail. Not sure if it runs from Centos or not, that that is still working, but you can run from Ubuntu live installer or download as a full repair ISO.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bradsturtevant on 2014-04-08
I am downloading ubuntu-repair-disk-64bit.iso...I appreciate your interest in my problem!

Window  8 does not even have a drive letter (e.g., D:) for drive id 0 at this  point. I did install latest Windows on drive 1 when BIOS was configured  to boot drive 0, and Windows did have its boot partition on drive 0.  But, before I began this Ubuntu dual boot project I copied the /Boot  folder from drive 0 to 1 using NeoGrub and then using Windows 8 disk  partitioning software jusk nuked everything associated with that drive.

I  don't have a lot of experience with LVM. I have been creating a 256MB  ext4 for /boot which is seperate from LVM. In LVM I create 100GB / and  16GB swap.
Maybe /boot should be FAT?

My installs end up looking like (on hostname hypervisor13):

LVM Volume Groups
  hypervisor13
    hypervisor-root     100GB    ext4
    swap                    16GB      swap
sdd
    sdd1                     256MB   ext4
    sdd2                     116GB   Extended

---

### Post by oldfred on 2014-04-08
I do not really know LVM. But the normal install uses a Linux formatted /boot partition outside of the LVM. I think that is more for the encrypted install with LVM.
You only need a FAT32 partition if you have a new UEFI hardware based system and also are installing to boot from UEFI.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by bradsturtevant on 2014-04-08
No joy! I am officially preterbed. I am a developer! Let me loose! I need to be typing! (humor intended)

The Boot Info Summary is at
[http://paste.ubuntu.com/7223917](http://paste.ubuntu.com/7223917)

Last message I got was: grub-efi: purge cancelled. Please report this mesage to [email]boot.repair@gmail.com[/email]

EFI is certainly now on my rader screen. Never even heard of it an hour ago. Me thinks PC is not setup for EFI, and probably Ubuntu is focused on it in some way, but my intuitions, well. My Window 8 disk does have a C:\EFI\Microsoft\Boot but I don't think it means bull because it probably got created as part of '/f ALL' from Windows 8 related rescue command 'bcdboot C:\Windows /f ALL'. I had to run that pup when Ubuntu 12.04.4 install failed at last moment of install with a message something like 'Failed to write GRUP some related file'. After that computer booted into GRUB, and quickly fixed that with Windows 8 CD command prompt option and then command 'bcdboot C:\Windows /f ALL' (the /f ALL could be replaced with somethin like /f EFI or /f LeGaCY but can't remember options)

When I initiated repair from boot-repair-disk-64bit one of the first messages I got was 'run this command':
    sodu chroot /mnt/boot-sav/sdd5 dpkg --configure -a
Output was something like:
--- Uninstall Beginning ---
Module : bcmwl
...
Status: Before uninstall, this module version was ACTIVE on this kernel
wl.ko:
-Uninstallation
- Deleting from: /lib/modules/3.11.0-12-generic/updates/dkms
-Original module
-No ... found
-Use dkms install ... to reinstall ...
...
libkmod ERROR ../libkmod/libkmod.c:554 kmod_search_moddcp: could not open moddep file 'lib/modules/3.8.0-19-generic/modules.dep.bin'
...
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic

Next came the Legacy warning related to EFI:

"The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode. Alternatively, you may want to retry after deactivating the [Seperate /boot/efi/partition:] option" Do you want to Continue? Yes

I am not familiar with an EFI mode for my computer. Is there some way to test if I am in EFI mode?

The half baked Ubuntu install I have now did create /boot/efi so maybe I should focus Ubuntu away from EFI toward legacy mode? Not sure how to do that, but read somewhere that I can point Ubuntu to a config file on Internet to change its behavior during install.

---

### Post by bradsturtevant on 2014-04-08
An annoying installation issue in 13.10, 14.daily happens when clicking on 'Something Else' then click on a drive (e.g., /dev/sdd), then clicl on 'New Partition' Button.

The response its a bit whimpy:

No modifications can be made to the partition #4 of device SCSI (0,0,0) (sdd) for the following reasons:
In use by LVM volume group vg_virtualhost6

virtualhost6 is CentOS 6.5 install on first half of disk drive.

I believe the message should actually be: "I have no balls"

---

### Post by oldfred on 2014-04-08
I do not see any UEFI related files, partitions or drives. So it looks like your system is BIOS.

If it newer hardware? Most newer systems with Intel i-series chips have UEFI/BIOS motherboards. 
But Windows was usually in BIOS mode.
The Ubuntu installer will install in UEFI mode if booted in UEFI mode from UEFI/BIOS or will install in BIOS mode if booted in BIOS mode from UEFI/BIOS.
If you have a newer UEFI motherboard, you should have settings for UEFI on/off and/or BIOS/CSM/Legacy or whatever on/off. Some have a UEFI or BIOS setting and system will try to boot in UEFI mode and if not found try to boot in BIOS mode.

Windows only boots in UEFI mode from gpt partitioned drives.
Ubuntu will boot in UEFI or bios mode from gpt partitioned drives.
Both Windows & Ubuntu only boot from MBR(msdos) in BIOS mode.
And I really do not know a lot about LVM but it can be configured for either BIOS or UEFI.

The Ubuntu installer is based on gparted which does not correctly see LVM. You have to use LVM tools to modify LVM partitions not standard partition tools. 
Actually LVM is best if only on a full drive.
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)

With multiple drives like you have, I would have each install on a separate drive and configure so that that drive boots that install. Then if any drive fails you can boot another drive. And data can still be on various drives and temporary/quick backups can be on other drives also.

So the installer will have issue with the existing LVM. But you also made the install difficult since you left Windows 8 hibernated. Linux will not mount Windows partitions needing chkdks or hibernated. After any resize Windows needs chkdsk and Windows 8 is always hibernated or it calls it fast boot.

      This applies whether you have a pre-installed Windows 8 with UEFI or a Windows 8 you installed in BIOS boot mode.
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Do not let Boot-Repair run an auto fix. It wants to install grub2's boot loader to every drive. With multi-drive systems you probably want a different boot loader in every MBR (or efi Partition) on every drive.

Lots of comments, not much help, but I have lost track of where we are at? Must be getting old and slow. :)

To get Ubuntu to see LVM, you may need this. Although newest version does install with LVM (full drive only?) so live installer has LVM driver.
 sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by bradsturtevant on 2014-04-22
I did get Ubuntu 13.10 to install one time, but have not yet been able to recreate the procedure. 
I will probably close this thread and open up a new one with 14.04 in subject.

14.04 came out the day after I got 13.10 installed, so I attempted to install 14.04 over the top of 13.10 but that failed. Then tried for a while to reinstall 13.10 so I could try to 'upgrade to 14.04' but never did work.

I did make some progress. The computer is BIOS based (NO UEFI!).
Adding a 1MB 'ef02 BIOS boot partition' as first partition using gdisk seemed to help things along.

Also opted to 'make hybrid MBR' (in other words, protective MBR data) but I am not sure if that was a good idea or not.

Getting 13.10 to install went something like:
Install 12.04 on first half the hard disk
Attempt to install 13.10/14.04 via 'Try Ubuntu' icon for install so I could gracfully kill the install as it alway goes into an infinate loop as I first reported:
  "The installer is not hung at this point. 
  I can disconnect ethernet, add DNS name servers, etc.
  Clicking on little arrow below [install message] Configuring bcmwl-kernel-source 
  I see additional information about the spin cycle:
    ubuntu dbus [1399]:[system] Acquired the name org.freedesktop.UDisk2 on the system bus
    ubuntu dbus [1399]:[system] Activating service name='org.freedesktop.nm_dispatcher' (using service helper)
    ubuntu dbus [1399]:[system] Successfully activated service 'org.freedesktop.nm_dispatcher'"

After initial install of 13.10 the computer would boot to grub prompt, 14.04 would boot to grub 'rescue' prompt.

The boot-repair stuff did nothing for me (later found it did add many, many unworking entrys to /boot/grub/grub.cfg)

The next steps are strange but true. 
Found that reinstalling 12.04 on top of itself (after 13.10/14.04 installs hosed system), then upgrading 12.04 to grub2 would produce valid grub menu entries for everyone (12.04, 13.10/14.04, Windows 8.1). The 'sudo apt-get install grub2' showed output like: 

root@hypervisor12:~# apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  grub2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,512 B of archives.
After this operation, 32.8 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe grub2 amd64 1.99-21ubuntu3.14 [2,512 B]
Fetched 2,512 B in 0s (11.1 kB/s)
Selecting previously unselected package grub2.
(Reading database ... 200568 files and directories currently installed.)
Unpacking grub2 (from .../grub2_1.99-21ubuntu3.14_amd64.deb) ...
Setting up grub2 (1.99-21ubuntu3.14) ...
root@hypervisor12:~# 
root@hypervisor12:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb4
Found Windows 8 (loader) on /dev/sdc1
done
root@hypervisor12:~# 

Not sure if 'sudo grub-update' helped. Output like below seen. It sure does not delete duplicate entries in grub.cfg

Setting up grub-common (1.99-21ubuntu3.14) ...
Installing new version of config file /etc/grub.d/00_header ...
Installing new version of config file /etc/grub.d/30_os-prober ...
Installing new version of config file /etc/grub.d/20_linux_xen ...
Installing new version of config file /etc/grub.d/10_linux ...
Setting up grub2-common (1.99-21ubuntu3.14) ...
Setting up grub-pc-bin (1.99-21ubuntu3.14) ...
Setting up grub-pc (1.99-21ubuntu3.14) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on /dev/sda4
Found Windows 8 (loader) on /dev/sdb1
done
Setting up libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.4) ...
Setting up liblvm2app2.2 (2.02.66-4ubuntu7.4) ...
Setting up udisks (1.0.4-5ubuntu2.2) ...

I suppose the problem all has to do with my partitioning scheme.
Well, that's all for now...


fdisk, gdisk, partition, grub related Appedix
=============================================

I use same bios_grub and swap partitions for both 12.04 and 14.04

root@hypervisor12:~# parted
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print drives                                                     
Model: ATA Hitachi HDP72502 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  18.9MB  16.8MB  linux-swap(v1)
 3      18.9MB  107GB   107GB   ext2
 4      107GB   250GB   143GB   ext2


root@hypervisor12:~# fdisk /dev/sdb
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


gdisk info
----------

root@hypervisor12:~# gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

p    print the partition table
Command (? for help): p
Disk /dev/sdb: 488281250 sectors, 232.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00C6889E-5D17-45D3-B25A-7B561A80AFFE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488281216
Partitions will be aligned on 2048-sector boundaries
Total free space is 3823 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2            4096           36863   16.0 MiB    8200  
   3           36864       209752063   100.0 GiB   8300  
   4       209752064       488279407   132.8 GiB   8300  


d    display the sector alignment value
Expert command (? for help): d
Partitions will begin on 2048-sector boundaries.

o    print protective MBR data
Recovery/transformation command (? for help): o

Disk size is 488281250 sectors (232.8 GiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1    488281249   primary     0xEE


i    show detailed information on a partition
Expert command (? for help): i
Partition number (1-4): 1
Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)
Partition unique GUID: 4C89F0DF-F453-4C82-B7F1-528CFD4911B6
First sector: 2048 (at 1024.0 KiB)
Last sector: 4095 (at 2.0 MiB)
Partition size: 2048 sectors (1024.0 KiB)
Attribute flags: 0000000000000000
Partition name: ''


Expert command (? for help): i
Partition number (1-4): 4
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: F79A1DE6-184A-4B45-A9F6-61D7B079F86A
First sector: 209752064 (at 100.0 GiB)
Last sector: 488279407 (at 232.8 GiB)
Partition size: 278527344 sectors (132.8 GiB)
Attribute flags: 0000000000000000
Partition name: ''


GRUB.CFG (after grub2 upgrade)
==============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt3)'
  search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux    /boot/vmlinuz-3.8.0-38-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    echo    'Loading Linux 3.8.0-38-generic ...'
    linux    /boot/vmlinuz-3.8.0-38-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    echo    'Loading Linux 3.8.0-29-generic ...'
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 14.04 LTS (14.04) (/vmlinuz root=/dev/sdb4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sdb4
    initrd /initrd.img
}
menuentry "Ubuntu 14.04 LTS (14.04) (/boot/vmlinuz-3.13.0-24-generic root=/dev/sdb4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sdb4
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Ubuntu 14.04 LTS (14.04) (/boot/vmlinuz-3.13.0-24-generic.efi.signed root=/dev/sdb4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic.efi.signed root=/dev/sdb4
}
menuentry "Ubuntu 14.04 LTS (14.04) (root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6)" --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6 ro   quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Ubuntu 14.04 LTS (14.04) (root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6)" --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6 ro   $vt_handoff
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Windows 8 (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 74BC2EC7BC2E83A8
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


GRUB-BAD.CFG (14.04 boots into grub rescue mode)
================================================


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt3)'
  search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux    /boot/vmlinuz-3.8.0-38-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    echo    'Loading Linux 3.8.0-38-generic ...'
    linux    /boot/vmlinuz-3.8.0-38-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    echo    'Loading Linux 3.8.0-29-generic ...'
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=1bfc6f69-d95d-44b4-871c-e3b7229530f4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 1bfc6f69-d95d-44b4-871c-e3b7229530f4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sda4
    initrd /initrd.img
}
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sda4
    initrd /initrd.img
}
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sda4
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic.efi.signed root=/dev/sda4
}
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sda4
    initrd /initrd.img
}
menuentry "Ubuntu 14.04 LTS (14.04) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sda4
    initrd /initrd.img
}
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 74BC2EC7BC2E83A8
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

---

### Post by bradsturtevant on 2014-05-02
On this older BIOS based (NO UEFI!) computer the two significant keys to success, in order of importance seem to be 1) create a /boot partition! - mine is 256MB (initially I only created swap and root partitions) and;  2) Before starting Ubuntu install, unpartition the entire hard disk using gdisk/fdisk and then use either Windows 8.1 or gdisk (from Try Ubuntu terminal) to create a new GPT disk with a special 'BIOS boot partition' of 128MB size (initially 1MB was used). Note: gdisk gives boot partitions code type 'ef02 BIOS boot partition' and Windows 8.1 gives type '0C01  Microsoft reserved part' but both seem to work. And also before Ubuntu install use gdisk to 'make hybrid MBR' or on Windows 8.1 you will get hybrid MBR and 128MB 'reserver part' automagically. Note: You can only initialize a GPT hard disk on Windows 8.1 when disk is completely blank (no partition tree).

---

