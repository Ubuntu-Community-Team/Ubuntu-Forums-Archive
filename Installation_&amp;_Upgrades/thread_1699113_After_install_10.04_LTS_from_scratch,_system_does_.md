---
title: "After install 10.04 LTS from scratch, system does not boot"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by andimeier on 2011-03-03
--- START prologue ---
[I]Once I had a perfectly working 10.04 LTS PC. One day I chose to upgrade to 10.10 which left me with an unbootable PC.
After fruitless efforts of having this fixed (by reinstalling Grub2, by trying this and that) I decided I reinstall the whole system from scratch.
[/I]--- END prologue ---


I installed 10.04 LTS on a software RAID1 (mirror). The installation went flawlessly without errors, including the writing of GRUB2 to the MBR's of the mirrored disks. At least I thinks so - no error messages.

But I cannot boot the system: after the BIOS messages, the screen goes blank and a lone white cursor is blinking left top.

What can that be?

TIA
Andi

---

### Post by Joe of loath on 2011-03-03
Have you tried a separate /boot/ partition? Many motherboards don't support booting from

---

### Post by p.gogarty on 2011-03-03
I am also having this issue after installing using a soft raid 5 configuration.
I will try a seperate boot partion and psot back with results

---

### Post by andimeier on 2011-03-05
I have no separate boot partition. But I apparently don't need one, because ... please read on:

In fact, I used to have a fully functional system (with bootable root partition on RAID1) until I decided to upgrade from 10.04 LTS to 10.10. After that upgrade (2 months ago), the PC would never ever boot again. After BIOS messages -> black screen with blinking cursor.

So I tried to install a 10.04 LTS from scratch, but to no avail: still after boot messages blinking cursor.

So I would assume in this configuration (without a boot partition) it is well possible to have a working system with my hardware - because I had one! And I want to get back exactly the same system which worked before the upgrade attempt.

Cheers

---

### Post by andimeier on 2011-03-06
**Finally got it!**

The problem was that the BIOS fooled me into thinking that the boot order was correct when it was actually wrong.

That's my explanation:

I have 3 HDs, being partitioned identically: 20 GB / 160 GB

```
/dev/sda:
  20 GB boot/root partition (RAID1)
 160 GB data partition (RAID5)
/dev/sdb: 
  20 GB boot/root partition (RAID1)
  160 GB data partition (RAID5)
/dev/sdc: 
  20 GB swap partition
  160 GB data partition (RAID5)
```Important detail: on sda and sdb GRUB2 is installed in the MBR, whereas on sdc it is not (since sdc only contains the swap partition and the data partition for RAID5).

When I checked the boot order I could see no evil:


[LIST]
[*]SAMSUNG SPINPOINT F1
[*]SAMSUNG SPINPOINT F1
[*]SAMSUNG SPINPOINT F1
[/LIST]
But I assume that the first entry actually referenced sdc. The three entries are visually non distinguishable from each other. But sdc does not contain a boot loader. Thus, the PC tried to boot from sdc, could not find any boot loader, got stuck => black, blank screen, blinking cursor.

**Solution:**

I switched order in the list of boot devices so that the order looks like this:


[LIST]
[*]SAMSUNG SPINPOINT F1
[*]SAMSUNG SPINPOINT F1
[*]SAMSUNG SPINPOINT F1
[/LIST]
Yeah, you're right: you can see no difference. But I managed to get another drive first. This time the PC booted into the 10.04 system.

I have to say, I find it awkward that:


[LIST=1]
[*]the BIOS displays the three HDs in a way that noone can tell which one references actually to which of the three, you cannot distinguish them.
[*]Why does the BIOS not realise that it is not possible to boot from sdc (which does not even contain a boot loader) and then advances to the next HD in the boot order? Why does it get stuck?
[/LIST]

---

### Post by xx58 on 2011-03-06
Cannot understand, what is resolved and how??

---

### Post by andimeier on 2011-03-06
I had the initial problem (not described in *this* thread) that after upgrading from Ubuntu 10.04 to 10.10, the system would not boot anymore, but just display a GRUB error message.

Some attempts to cure the problem would require booting from USB pen drive into live Ubuntu system (for instance, for a grub-install etc.) I guess it was this configuring the BIOS that introduced the "black screen problem".

Now the very problem described in *this *thread is that I do not even get to the GRUB error message anymore but only to a blank screen after the BIOS messages, nothing more.

This situation persisted even after re-installing a Ubuntu 10.04 from scratch. Whatever I did, I just got the BIOS messages and after them: a blank, black screen with a blinking cursor.

This is the problem .

The solution: another guy gave me the idea of the BIOS having something to do with this. So I found out that it was really the boot order configured in the BIOS which was the problem why there was actually no boot process. After correcting the order of the hard disks (the order in which the BIOS tries to find a boot loader), the system boots again.

This is what I tried to describe with my "solution" in my previous post.

Hope I could make it somewhat clearer ...

---

### Post by groundup on 2011-04-06
I am having the same issue. I installed 10.10 on a fresh install using unetbootin with a USB drive. Installation went fine, then I go to restart, removing the USB drive and I get the blinking cursor.

Details:
Boot order: USB, HDD, CD-R (I've tried every combination of this by changing the BIOS config)

I can boot from the USB drive and access the hard drive but it won't boot from the hard drive.

I've searched far and wide and asked in #ubuntu. Nothing seems to fix it. I can't really keep a USB drive in this to boot from since it is not going to be in my hands after I finish loading it.

---

### Post by groundup on 2011-04-06
root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root
                       44G  1.4G   41G   4% /
none                  993M  244K  992M   1% /dev
none                 1000M     0 1000M   0% /dev/shm
none                 1000M   60K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
/dev/sda1             228M   21M  196M  10% /boot
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000aa01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       30395   243889153    5  Extended
/dev/sda5              32       30395   243889152   8e  Linux LVM

Disk /dev/dm-0: 47.6 GB, 47617933312 bytes
255 heads, 63 sectors/track, 5789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2076 MB, 2076180480 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 2020 MB, 2020539904 bytes
32 heads, 63 sectors/track, 1957 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13044ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1957     1972624+   b  W95 FAT32

---

### Post by groundup on 2011-04-06
Even more information:

root@ubuntu:~# di
Filesystem         Mount              Mebis     Used    Avail %Used fs Type
/dev/mapper/ubuntu /                44699.0   1418.4  41010.0   8%  ext4
/dev/sda1          /boot              227.7     20.2    195.4  14%  ext2

---

### Post by groundup on 2011-04-06
In BIOS setup:

Hard Disk Priority: HDD, USB, bootable add-in cards

CMOS features: SATA-0 = HDD; SATA-1 = CD; SATA-2 = not present; SATA-3 = not present; SATA-4 = none; SATA-5 = none;

SATA mode: RAID

---

### Post by groundup on 2011-04-06
root@ubuntu:~# mount | tail -l
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)


root@ubuntu:~# mount /dev/sda1
mount: /dev/sda1 already mounted or /boot busy
mount: according to mtab, /dev/sda1 is already mounted on /boot


root@ubuntu:~# blkid
/dev/sda1: UUID="e9435795-5f6d-45c0-9066-b6a436351e2b" TYPE="ext2"
/dev/sda5: UUID="g8WVyX-i3TH-CMoI-1ciL-NCyG-5Cev-lypKZq" TYPE="LVM2_member"
/dev/mapper/ubuntu-root: UUID="c84d3df6-1059-466b-ad6b-a0eabca143ae" TYPE="ext4"
/dev/mapper/ubuntu-swap_1: UUID="2165373b-4dbc-46de-be43-4244b18a4393" TYPE="swap"
/dev/sdb1: UUID="16B0-FA9D" TYPE="vfat"



# /etc/fstab: static file system information.
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=e9435795-5f6d-45c0-9066-b6a436351e2b /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0


root@ubuntu:~# lshw -C disk
  *-disk
       description: ATA Disk
       product: WDC WD2500JS-75N
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WCANKL866878
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000aa01
  *-cdrom
       description: DVD reader
       product: CDRWDVD TS-H493B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: D200
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       size: 1926MiB (2020MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=13044ed2


root@ubuntu:/# lshw -short
H/W path           Device      Class       Description
======================================================
                               system      Vostro 200
/0                             bus         0CU409
/0/0                           memory      128KiB BIOS
/0/4                           processor   Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
/0/4/a                         memory      32KiB L1 cache
/0/4/b                         memory      1MiB L2 cache
/0/24                          memory      2GiB System Memory
/0/24/0                        memory      1GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/24/1                        memory      DIMM [empty]
/0/24/2                        memory      1GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/24/3                        memory      DIMM [empty]
/0/100                         bridge      82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                       bridge      82G33/G31/P35/P31 Express PCI Express Root Port
/0/100/2                       display     82G33/G31 Express Integrated Graphics Controller
/0/100/19          eth0        network     82562V-2 10/100 Network Connection
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1f                      bridge      82801IR (ICH9R) LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801 SATA RAID Controller
/0/100/1f.2/0      /dev/sda    disk        250GB WDC WD2500JS-75N
/0/100/1f.2/0/1    /dev/sda1   volume      243MiB Linux filesystem partition
/0/100/1f.2/0/2    /dev/sda2   volume      232GiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume      232GiB Linux LVM Physical Volume partition
/0/100/1f.2/1      /dev/cdrom  disk        CDRWDVD TS-H493B
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/1               scsi6       storage
/0/1/0.0.0         /dev/sdb    disk        2020MB SCSI Disk
/0/1/0.0.0/1       /dev/sdb1   volume      1926MiB Windows FAT volume

---

### Post by groundup on 2011-04-06
Here is an image of how my drive is setup.

---

### Post by groundup on 2011-04-06
boot info script:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

ubuntu-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

ubuntu-swap_1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   488,280,063   487,778,306   5 Extended
/dev/sda5             501,760   488,280,063   487,778,304  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2020 MB, 2020539904 bytes
32 heads, 63 sectors/track, 1957 cylinders, total 3946367 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,945,311     3,945,249   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/ubuntu-root c84d3df6-1059-466b-ad6b-a0eabca143ae   ext4                                     
/dev/mapper/ubuntu-swap_1 2165373b-4dbc-46de-be43-4244b18a4393   swap                                     
/dev/sda1        e9435795-5f6d-45c0-9066-b6a436351e2b   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        g8WVyX-i3TH-CMoI-1ciL-NCyG-5Cev-lypKZq LVM2_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        16B0-FA9D                              vfat                                     
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
ubuntu-root
ubuntu-swap_1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext2       (rw)


============================= sda1/grub/grub.cfg: =============================

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
}

insmod lvm
insmod part_msdos
insmod ext2
set root='(ubuntu-root)'
search --no-floppy --fs-uuid --set c84d3df6-1059-466b-ad6b-a0eabca143ae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e9435795-5f6d-45c0-9066-b6a436351e2b
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e9435795-5f6d-45c0-9066-b6a436351e2b
	linux	/vmlinuz-2.6.35-28-generic root=/dev/mapper/ubuntu-root ro   splash quiet
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e9435795-5f6d-45c0-9066-b6a436351e2b
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=/dev/mapper/ubuntu-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e9435795-5f6d-45c0-9066-b6a436351e2b
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e9435795-5f6d-45c0-9066-b6a436351e2b
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-28-generic
    .0GB: vmlinuz-2.6.35-28-generic

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Server" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Install in expert mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed priority=low --
	initrd	/install/initrd.gz
}
menuentry "Install Ubuntu Enterprise Cloud" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/cloud.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
	initrd	/install/initrd.gz
}
menuentry "Rescue a broken system" {
	set gfxpayload=keep
	linux	/install/vmlinuz  rescue/enable=true --
	initrd	/install/initrd.gz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

============================ ubuntu-root/etc/fstab: ============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=e9435795-5f6d-45c0-9066-b6a436351e2b /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0

================ ubuntu-root: Location of files loaded by Grub: ================


    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 f6 01  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  21 33 3c 00 05 0f 00 00  00 00 00 00 02 00 00 00  |!3<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9d fa b0 16 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 10  a8 14 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by groundup on 2011-04-06
Solved:

[15:38] <Jordan_U> groundup: Boot Ubuntu using your flash drive (it will boot your installed Ubuntu from the hard drive) then run "sudo dpkg-reconfigure grub-pc".

Everything default except the last screen where I had to check the first box.

---

