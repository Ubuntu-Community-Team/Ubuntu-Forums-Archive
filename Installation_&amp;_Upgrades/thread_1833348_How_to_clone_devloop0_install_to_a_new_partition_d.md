---
title: "How to clone /dev/loop0 install to a new partition /dev/sda ?"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by xgator on 2011-08-25
Newbie, Installed Ubuntu from an iso and now can boot only from /dev/loop0 need to clone this to /dev/sda, is this possible if so what are the commands.

---

### Post by Hakunka-Matata on 2011-08-25
Welcome to the forums.

If you are booting and running Ubuntu, please download and run the 'boot_info_script' script in my signature.  Post the RESULTS.txt file between #code tags in a reply.  Use "Go Advanced" to see code tags (#)

if that all sounds daunting, just post the results of ```
sudo fdisk -lu
```

---

### Post by xgator on 2011-08-26
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  - (cleared BS by FDISK)
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda6/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   117,194,174   117,194,112   7 NTFS / exFAT / HPFS
/dev/sda2         874,353,690   905,069,969    30,716,280  83 Linux
/dev/sda3         117,194,175   874,353,689   757,159,515   f W95 Extended (LBA)
/dev/sda5         117,194,238   608,702,849   491,508,612   7 NTFS / exFAT / HPFS
/dev/sda6         771,955,443   874,353,689   102,398,247   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       dc0eb2e9-1008-4b2c-8b85-e5fb9893e1b7   ext4       
/dev/sda1        7840465F404623EA                       ntfs       XP
/dev/sda2                                               ext3       LINUX
/dev/sda5        0AF8ED96F8ED8075                       ntfs       data
/dev/sda6        D294D25394D23A25                       ntfs       win7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
UnsupportedDebug="do not select this" /debug
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN
c:\tboot="Mac OSX Leopard"
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

======================== sda6/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root D294D25394D23A25
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root D294D25394D23A25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=D294D25394D23A25 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root D294D25394D23A25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=D294D25394D23A25 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root D294D25394D23A25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=D294D25394D23A25 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root D294D25394D23A25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=D294D25394D23A25 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 7840465F404623EA
	chainloader +1
}
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
--------------------------------------------------------------------------------

============================= sda6/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

================= sda6/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   6.810897827 = 7.313145856    boot/grub/grub.cfg                             1
   6.902900696 = 7.411933184    boot/initrd.img-2.6.38-11-generic              1
   1.046779633 = 1.123971072    boot/initrd.img-2.6.38-8-generic               2
   2.984687805 = 3.204784128    boot/vmlinuz-2.6.38-11-generic                 1
   0.427734375 = 0.459276288    boot/vmlinuz-2.6.38-8-generic                  2
   6.902900696 = 7.411933184    initrd.img                                     1
   1.046779633 = 1.123971072    initrd.img.old                                 2
   2.984687805 = 3.204784128    vmlinuz                                        1
   0.427734375 = 0.459276288    vmlinuz.old                                    2

```

---

### Post by Hakunka-Matata on 2011-08-26
OK, thanks.  You are running Ubuntu under Windows, Wubi.  Wubi is convenient way to easily 'try out' Ubuntu.  If you decide later that you like and want to use Ubuntu on a regular basis, and have it separated from your Windows OS, you can install it directly to it's own partition(s).  e.g. "Dual-boot"

Have fun

---

### Post by xgator on 2011-08-26
How do I transfer it to the Linux partition from without burning a media disk?

---

### Post by Hakunka-Matata on 2011-08-26
> **xgator said:**
> How do I transfer it to the Linux partition from without burning a media disk?

The method is not really a 'transfer'.

You would _**install**_ ubuntu to your Hard Drive.  You are now running it as an application within your Windows OS, it's just another program of windows now.  

You must first download the Ubuntu.iso file, then burn it to either a CD/DVD/USB.  That will get you what is called an ubuntu liveCD.  You would then use that liveCD to boot your machine with.  You can either change the "first boot device" in BIOS by entering BIOS Setup, or you can press the appropriate key @ boot time to select the "Boot Menu" which is a one-off, one-time change in which drive, cd, dvd, usb device the machine boots from.  If you have a USB of at least 1GiB capacity, that will obviate the need for using a CD or DVD.  Download and use 'unetbootin' if you're going to use a USBstick.  And before actually installing ubuntu, I suggest selecting the "try ubuntu" without installing it first.  

First and foremost though, you need to backup any important data you have on your windows installation.  You stand a chance of corrupting the hard drive and loosing your windows installation, not a likelihood, but we know about Murphy's Law, right?  You also need to have recovery, or install disks handy for your windows installation in case you mess it up while installing Ubuntu.

What version Windows are you running?

Other people explain this much better (succinctly) than I do.  Go to [www.ubuntu.com](www.ubuntu.com) and have a read, they say it better than I ever could.

---

### Post by bcbc on 2011-08-26
[HOWTO: Migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by Hakunka-Matata on 2011-08-26
> **bcbc said:**
> [HOWTO: Migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354").

My apologies, i was not aware that a guide existed to migrate a Wubi installation to a partition install.  But I am now.  Thanks

---

### Post by bcbc on 2011-08-26
> **Hakunka-Matata said:**
> .

My apologies, i was not aware that a guide existed to migrate a Wubi installation to a partition install.  But I am now.  Thanks

No prob ;)

---

### Post by xgator on 2011-08-31
Thanks bcbc for the link I was able to clone to new partition

---

### Post by bcbc on 2011-08-31
Great! Glad you got it sorted :)

---

### Post by csherwood on 2012-05-04
Hi all -
I have pored over this thread for a day, and am still unsure a) how my installation is set up and b) what to do about it. I initially used Wubi to install Ubuntu in dual-boot mode on my WinXP machine. Worked wonderfully. Recently, I updated to 12.04 LTS. That went fine, but during the installation, I got warnings about "low disk space". Now I would like to assign a healthy amount of disk space to Ubuntu, and later might decide to get rid of Windows entirely.

I have two internal disks (C: and D: in Windowsland) and a big external disks. Here is my file system:

csherwood-pr@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       29G   26G  1.9G  94% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           806M  800K  805M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  288K  2.0G   1% /run/shm
/dev/sdb2       466G   98G  368G  21% /host
/dev/sda1       932G  313G  620G  34% /media/FreeAgent Drive

csherwood-pr@ubuntu:~$ sudo fdisk -lu
[sudo] password for csherwood-pr: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05ad72a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      224909      112423+  de  Dell Utility
/dev/sdb2   *      224910   976751999   488263545    7  HPFS/NTFS/exFAT

Thanks

---

### Post by bcbc on 2012-05-04
csherwood

You have a 29GB wubi install. You've used up 26GB. (1.9GB free space remaining).

You have plenty of space on all your drives and only 1 or 2 partitions used on each. So there shouldn't be much difficulty to re-partition and then migrating the Wubi. It's possible also to resize the Wubi install to make it bigger than 29GB, but I would advise migration instead, especially if you intend to replace windows eventually. The only other option would be to free up space, or move data to the /host partition. 

Why don't you review that migration thread I linked to a few posts above. The first post has a link to a partitioning guide as well. If you have any questions, just post in that thread.

In the meantime, you can quickly make a little more space by:
```
sudo apt-get autoremove
sudo apt-get autoclean

```
and removing older kernels (leave the last two kernels). Refer to this for more info: [http://askubuntu.com/a/107476/14916](http://askubuntu.com/a/107476/14916)

---

