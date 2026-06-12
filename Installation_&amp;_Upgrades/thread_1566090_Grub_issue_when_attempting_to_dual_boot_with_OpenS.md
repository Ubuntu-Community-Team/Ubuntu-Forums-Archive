---
title: "Grub issue when attempting to dual boot with OpenSuSE"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2010-09-01
I've attempted to install OpenSuSE 11.3 to my spare 10GB partition, and mount my usual /home to /data in the OpenSuSE install.

The problem is that during the opensuse install, there was an error installing grub legacy (.97, if I remember the version number correctly), and the installer quit.  I rebooted, and my BIOS isn't finding any OS. I believe the error was 'No Operating System Detected' or something like that.

I tried to have OpenSuSE install its bootloader to its partition (sda4), but apparently there's some sort of conflict. I wanted to have OpenSuSE install its bootloader to its root partition, then boot into Kubuntu and run a Grub2 update. I can't boot into Kubuntu now, though.  

I'm in a LiveCD session; where would I start to tackle this situation?

---

### Post by confused57 on 2010-09-01
You could reinstall Ubuntu grub2 to the mbr, see section 13 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This should at least get you back into Ubuntu?

---

### Post by tarahmarie on 2010-09-01
> **confused57 said:**
> You could reinstall Ubuntu grub2 to the mbr, see section 13 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This should at least get you back into Ubuntu?

Excellent!  All better--I'm back and booted into Kubuntu. Notably, when I booted, I got an error message that /altos, the extra partition that I'd created when partitioning my disk and saved for another OS, was not ready for mounting; I skipped mounting it, and Kubuntu booted right up.

So, WTH happened?  If OpenSuSE is attempting to install grub legacy to its own root partition, shouldn't it work fine, and when I boot up Kubuntu and run grub-update, it should add OpenSuSE to the list of bootable OSes, right? What's the step I'm missing here?

---

### Post by tarahmarie on 2010-09-02
Here's my output from attempting to run update-grub:

```

~ : Yes, Supreme Empress? $ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.3 (i586) on /dev/sda4
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda4.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda4.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda4.  Check your device.map.
done
~ : Yes, Supreme Empress? $ 


```

So, it's not finding a bootloader for OpenSuSE. What's the next step?

---

### Post by oldfred on 2010-09-02
To see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by tarahmarie on 2010-09-02
> **oldfred said:**
> To see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 23679232 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048         4,094         2,047  83 Linux
/dev/sda2               4,096    41,947,134    41,943,039  83 Linux
/dev/sda3          41,947,136    58,724,350    16,777,215  82 Linux swap / Solaris
/dev/sda4                   1             1             1  ee GPT


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Bios Boot Partition
/dev/sda2           4,096    41,947,135    41,943,040 Linux or Data
/dev/sda3      41,947,136    58,724,351    16,777,216 Linux Swap
/dev/sda4      58,724,352    79,695,871    20,971,520 System/Boot Partition
/dev/sda5      79,695,872 3,907,029,134 3,827,333,263 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,192    31,116,287    31,108,096   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        349c4872-7bcb-4505-8c29-71fc6a6591f1   ext3                                     
/dev/sda3        0caab535-bd20-4682-802c-bad8a829f735   swap                                     
/dev/sda4        a6bee561-7af2-4169-b4d5-742552b832f8   ext3                                     
/dev/sda5        b46ca189-e954-4e61-bbd4-2e3b31c2dd7c   ext3                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        0febc6e8-f571-4f5b-8f6d-352944b59827   ext3       secondDrive                   
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        3638-3034                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /media/secondDrive       ext3       (rw)
/dev/sda5        /home                    ext3       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 349c4872-7bcb-4505-8c29-71fc6a6591f1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 349c4872-7bcb-4505-8c29-71fc6a6591f1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 349c4872-7bcb-4505-8c29-71fc6a6591f1
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=349c4872-7bcb-4505-8c29-71fc6a6591f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 349c4872-7bcb-4505-8c29-71fc6a6591f1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 349c4872-7bcb-4505-8c29-71fc6a6591f1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Desktop -- openSUSE 11.3 - 2.6.34-12 (on /dev/sda4)" {
	set root=''
	linux /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part4 resume=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part3 splash=silent quiet showopts vga=0x31a
	initrd /boot/initrd-2.6.34-12-desktop
}
menuentry "Failsafe -- openSUSE 11.3 - 2.6.34-12 (on /dev/sda4)" {
	set root=''
	linux /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part4 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
	initrd /boot/initrd-2.6.34-12-desktop
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=349c4872-7bcb-4505-8c29-71fc6a6591f1 /               ext3    errors=remount-ro 0       1
# /altos was on /dev/sda4 during installation
UUID=d3975bbf-a552-4228-9b2b-9346f50bc7bf /altos          ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=b46ca189-e954-4e61-bbd4-2e3b31c2dd7c /home           ext3    defaults        0       2
# /media/secondDrive was on /dev/sdb1 during installation
UUID=0febc6e8-f571-4f5b-8f6d-352944b59827 /media/secondDrive ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=0caab535-bd20-4682-802c-bad8a829f735 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  12.1GB: boot/grub/core.img
  12.1GB: boot/grub/grub.cfg
  12.1GB: boot/initrd.img-2.6.32-24-generic-pae
  12.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  12.1GB: initrd.img
  12.0GB: vmlinuz

=========================== sda4/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Wed Sep  1 19:41:03 PDT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,3)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.3 - 2.6.34-12
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part4 resume=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part3 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.34-12-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3 - 2.6.34-12
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part4 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.34-12-desktop

=============================== sda4/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part3 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part4 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD2001FASS-00W2B0_WD-WMAY00085646-part5 /data                ext3       defaults              1 2
/dev/disk/by-id/ata-WDC_WD7500AAKS-00RBA0_WD-WCAPT1056346-part1 /media/secondDrive   ext3       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda4: Location of files loaded by Grub: ===================


  10.1GB: boot/grub/menu.lst
  10.0GB: boot/grub/stage2
  10.0GB: boot/initrd
  10.0GB: boot/initrd-2.6.34-12-desktop
  10.1GB: boot/vmlinuz
  10.1GB: boot/vmlinuz-2.6.34-12-desktop
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sde sdf sdg sdh 


```

---

### Post by tarahmarie on 2010-09-02
I found two links that may be helpful, but I'm not sure I should implement them. I'm in unfamiliar territory here, and I don't want to nuke my grub 2 install.

[http://tuxnetworks.blogspot.com/2010/01/grub-probe-error-cannot-find-grub-drive.html](http://tuxnetworks.blogspot.com/2010/01/grub-probe-error-cannot-find-grub-drive.html)

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)

---

### Post by oldfred on 2010-09-02
You have gpt which causes some confusion in grub2. Not sure if grub legacy even works with gpt.

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos"  posted by meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
I added insmod part_msdos to 40_custom & both windows on sda1 and Ubuntu
on sdc5 booted without any issues. 


They are making major improvements in grub2 with Maverick for efi which uses gpt.
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)


Legacy BIOS Issues with GPT
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

### Post by srs5694 on 2010-09-02
It appears that the SuSE install created a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which may be confusing GRUB. In particular, the 0xEE partition comes last in your new converted MBR, and in such a configuration, GRUB sees the disk as an MBR disk, not as a GPT disk. I recommend you convert back to a conventional GPT configuration and re-install GRUB in Ubuntu:


[list=1]
[*]Install gdisk, if it's not already installed. (I recall advising you a few days ago, and I believe you installed gdisk then.)
[*]Type "sudo gdisk /dev/sda" to launch gdisk.
[*]Type "x" to enter the experts' menu.
[*]Type "n" to create a new protective MBR.
[*]Type "w" to write your changes to disk. You'll have to verify this action.
[*]Back at your shell prompt, type "sudo grub-install" to re-install GRUB. It should redetect the partition table type and install a pure-GPT configuration rather than the MBR configuration it's probably got now. This should fix the problems you're having.
[/list]


As to why SuSE did what it did, I don't know. If you're certain you told it to install GRUB to its own partition, it certainly shouldn't have overwritten the GRUB 2 code you already had in your MBR. FWIW, I recall noticing that SuSE converted a GPT disk to a hybrid MBR when I installed it on one of my systems a few months ago. I didn't bother to investigate further, though. [rant]IMHO, that's bad behavior. Despite the fact that my GPT fdisk supports hybrid MBRs, I think they're a Bad Idea (capitalized), and Linux distributions should not be converting legal GPT disks into hybrid MBR disks unless explicitly told to do so.[/rant]

---

### Post by tarahmarie on 2010-09-02
> **srs5694 said:**
> It appears that the SuSE install created a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which may be confusing GRUB. In particular, the 0xEE partition comes last in your new converted MBR, and in such a configuration, GRUB sees the disk as an MBR disk, not as a GPT disk. I recommend you convert back to a conventional GPT configuration and re-install GRUB in Ubuntu:


[list=1]
[*]Install gdisk, if it's not already installed. (I recall advising you a few days ago, and I believe you installed gdisk then.)
[*]Type "sudo gdisk /dev/sda" to launch gdisk.
[*]Type "x" to enter the experts' menu.
[*]Type "n" to create a new protective MBR.
[*]Type "w" to write your changes to disk. You'll have to verify this action.
[*]Back at your shell prompt, type "sudo grub-install" to re-install GRUB. It should redetect the partition table type and install a pure-GPT configuration rather than the MBR configuration it's probably got now. This should fix the problems you're having.
[/list]


As to why SuSE did what it did, I don't know. If you're certain you told it to install GRUB to its own partition, it certainly shouldn't have overwritten the GRUB 2 code you already had in your MBR. FWIW, I recall noticing that SuSE converted a GPT disk to a hybrid MBR when I installed it on one of my systems a few months ago. I didn't bother to investigate further, though. [rant]IMHO, that's bad behavior. Despite the fact that my GPT fdisk supports hybrid MBRs, I think they're a Bad Idea (capitalized), and Linux distributions should not be converting legal GPT disks into hybrid MBR disks unless explicitly told to do so.[/rant]

Unfortunately, that seems to have bricked my hard drive. I can't boot with either a Kubuntu or OpenSuSE live cd. When I attempt to either load Kubuntu's live session or its installer, I get this error: (process:350): GLIB WARNING ** GLib - getpwuid_r(): failed due to unknown user id (0)

What's wrong?

---

### Post by srs5694 on 2010-09-03
That's very weird. Could you try with [System Resuce CD](http://www.sysresccd.org/) or [PartedMagic](http://partedmagic.com/) and post the output of "gdisk -l /dev/sda"? You might also be able to check that your partition data are intact; maybe an fsck would fix any filesystem problems that might exist....

---

### Post by tarahmarie on 2010-09-03
> **srs5694 said:**
> That's very weird. Could you try with [System Resuce CD](http://www.sysresccd.org/) or [PartedMagic](http://partedmagic.com/) and post the output of "gdisk -l /dev/sda"? You might also be able to check that your partition data are intact; maybe an fsck would fix any filesystem problems that might exist....

I will try with one of those as soon as I can borrow my husband's computer. The one I'm using right now has no burner, so I can't make a disk.

Which one of those (system rescue or parted magic) is likely to be the most friendly to a bash user?

---

### Post by srs5694 on 2010-09-03
Both provide bash. I've used both of them, and I don't recall any really big advantages of either of them, although I've used neither of them intensively enough to have a strong impression of either.

---

### Post by garvinrick4 on 2010-09-03
Just for anyone reading this: There is an option in OpenSuse to not install any bootloader and then boot to your grub2 install after OpenSuse install and update grub finds OpenSuse or Fedora for that matter and puts them in your Grub2 and you are set.
It is a 2 tabbed page in OpenSuSe and one of the tabs says Boot I do believe. Look around
you will find it. Option in Fedora also.

---

### Post by tommcd on 2010-09-03
> **tarahmarie said:**
>  I can't boot with either a Kubuntu or OpenSuSE live cd. When I attempt to either load Kubuntu's live session or its installer, I get this error: (process:350): GLIB WARNING ** GLib - getpwuid_r(): failed due to unknown user id (0)

Booting from a live CD should not be affected by the condition of the hard drive. The whole OS is loaded to memory from the CDROM drive and the hard drive is not even mounted.

And I thought you were trying to dual boot with Mandriva?
[http://ubuntuforums.org/showthread.php?t=1565296](http://ubuntuforums.org/showthread.php?t=1565296)

---

### Post by tarahmarie on 2010-09-06
Ok, here is the solution:

If one should want to triple boot, as I've done, install the OS with grub legacy first.

What I did was create 9 partitions using gdisk--a mini MBR partition, 6 10GB small partitions, one swap partition, and my /data partition at 1.8TB.  Then, I installed OpenSuSE 11.3 to sda2 with its home at sda3, installing grub legacy to the MBR and OpenSuSE's / partition. Then, I installed Fedora 9 to sda4 (and its own bootloader to this partition) with its home at sda5.

This has all been about figuring out how to multiboot a mix of grub legacy and grub2, in case you were wondering. I didn't care WHICH distros I was using besides Kubuntu, so long as they used grub legacy by default (and I wanted to experiment with differing package systems. OpenSuSE uses YaST with RPM, and Fedora uses YUM with RPM).

I updated OpenSuSE's menu.lst (by using the OpenSuSE install cd to boot to hard disk, which booted up OpenSuSE) with a chainloading entry for Fedora and tested that.

Finally, I installed Kubuntu 10.04 to sda6 (including grub2) with its home at sda7. I then used OpenSuSE's install cd to boot to hard disk and add a chainloading entry to menu.lst for Kubuntu.

All three installations found swap space at sda8, and I mounted my /data partition in all three, as well as my backup drive.

Notably, I had to reflag the MBR partition as a BIOS boot partition AND reinstall OpenSuSE's grub to the MBR after every single installation.  See these instructions for how I used gdisk to wipe my drive and create the partitions, as well as how I reflagged the BIOS boot partition.

[http://ubuntuforums.org/showthread.php?t=1563699&page=3](http://ubuntuforums.org/showthread.php?t=1563699&page=3)

srs5694, you are teh king (or possibly queen) of the buntus. ):P

And here's the instructions I used for reinstalling grub to the MBR through OpenSuSE:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks, all! If anyone has any questions about this process, I'm more than happy to answer them!

---

### Post by tommcd on 2010-09-06
> **tarahmarie said:**
> 
Notably, I had to reflag the MBR partition as a BIOS boot partition AND reinstall OpenSuSE's grub to the MBR after every single installation. ...

Most distros provide the option to install grub-legacy or grub2 to that distro's root partition instead of the MBR. Many distros (e.g., Slackware, and Slackware based distros) even offer the option not to install any bootloader at all. In this way you can avoid having to reinstall the grub version that you want to control your MBR when you install another distro.
For example, Garvinrick4 mentioned this about Suse in post #14 of this thread.
Also, Mandriva offers an "advanced" option for installing grub to where you want it as per the screen shot for installing grub in this tutorial:
[http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome](http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome)
There are some distros (for example Lubuntu) that will not give you this option. They just proceed to take over your MBR and give you no other options. In this case it is a simple matter to reinstall K/Ubuntu's grub to the MBR.

Anyway, glad you got it sorted out.
If you are using grub-legacy to control your MBR, you should read through Ubuntu forum member and all things grub guru Herman's tutorials for grub-legacy:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
Most everything I know about grub-legacy came from Herman's site.

---

### Post by tarahmarie on 2010-09-06
> **tommcd said:**
> Most distros provide the option to install grub-legacy or grub2 to that distro's root partition instead of the MBR. Many distros (e.g., Slackware, and Slackware based distros) even offer the option not to install any bootloader at all. In this way you can avoid having to reinstall the grub version that you want to control your MBR when you install another distro.
For example, Garvinrick4 mentioned this about Suse in post #14 of this thread.
Also, Mandriva offers an "advanced" option for installing grub to where you want it as per the screen shot for installing grub in this tutorial:
[http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome](http://howtoforge.com/the-perfect-desktop-mandriva-one-2010.1-spring-with-gnome)
There are some distros (for example Lubuntu) that will not give you this option. They just proceed to take over your MBR and give you no other options. In this case it is a simple matter to reinstall K/Ubuntu's grub to the MBR.

Anyway, glad you got it sorted out.
If you are using grub-legacy to control your MBR, you should read through Ubuntu forum member and all things grub guru Herman's tutorials for grub-legacy:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
Most everything I know about grub-legacy came from Herman's site.

The distros may offer the option to install to a root partition instead of the MBR, but they still write to it. That's the problem I was having; I described it in more detail in the previous thread where srs was helping me with my dual boot issue.

Again, while distros may offer the option not to install bootloaders, OpenSuSE still wrote to the MBR even after I'd selected no bootloader installation. That's how I ended up with a hybrid MBR. Same issue with Mandriva.

Sorting out what the distros SAID they were doing as opposed to what they were ACTUALLY doing was the real work here.  For more on that, see srs's excellent set of instructions to me.

---

