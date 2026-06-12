---
title: "Boot Repair"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2012-02-05
What does 'The boot of your PC is in EFI mode. Please change it to BIOS mode. Do you what to continue?' mean?

I have make a FAT partitiion and stuff, I have no idea what they mean????

---

### Post by oldfred on 2012-02-05
You may not want to change from UEFI to BIOS/MBR mode.

Post output of boot info script. May be better to run the git/beta version of boot script as it has some fixes that includes parsing the efi partition.

Direct download to your Ubuntu or liveCD:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

### Post by Azyx on 2012-02-05
> **oldfred said:**
> You may not want to change from UEFI to BIOS/MBR mode.

Post output of boot info script. May be better to run the git/beta version of boot script as it has some fixes that includes parsing the efi partition.

Direct download to your Ubuntu or liveCD:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Will try to morrow. I'm so tired just now :( I don't understand I  have a 2GB live-sd card, and make the rest of the disk as storage during 'making a boot-disk' but nothing I have configured are there when I reboot :( 
not languish, not network connection.. Never happend before with Ubuntu :(

---

### Post by YannBuntu on 2012-02-06
Hello

> **Azyx said:**
> What does 'The boot of your PC is in EFI mode. Please change it to BIOS mode. Do you what to continue?' mean?

Answer here:

[https://answers.launchpad.net/boot-repair/+question/186958](https://answers.launchpad.net/boot-repair/+question/186958)


@OldFred: Boot-Repair now uses last GIT version of BIS.

---

### Post by Azyx on 2012-02-07
> **oldfred said:**
> You may not want to change from UEFI to BIOS/MBR mode.

Post output of boot info script. May be better to run the git/beta version of boot script as it has some fixes that includes parsing the efi partition.

Direct download to your Ubuntu or liveCD:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

I have get little more active now and have downloaded the boot info script and it give us this:

```
Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:  Syslinux looks at sector 1434632 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       309,247       307,200   b W95 FAT32
/dev/sda2             309,248    23,531,519    23,222,272  83 Linux
/dev/sda3          23,537,664   222,756,863   199,219,200  83 Linux
/dev/sda4         222,757,290   488,392,064   265,634,775  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        646E-B3AE                              vfat       
/dev/sda2        412b2832-1935-40b2-a8b6-fcb35ae97aed   ext4       
/dev/sda3        84b30111-5052-43ab-887c-c954788e7890   ext4       
/dev/sda4        6a0838f8-2b9a-4597-8fa6-a0a0f7b3610b   ext4       120GB
/dev/sdb1        E128-3DB1                              vfat       2GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
  insmod gettext
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
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=412b2832-1935-40b2-a8b6-fcb35ae97aed ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-12-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
	echo	'Läser in Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=412b2832-1935-40b2-a8b6-fcb35ae97aed ro recovery nomodeset 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 412b2832-1935-40b2-a8b6-fcb35ae97aed
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=412b2832-1935-40b2-a8b6-fcb35ae97aed /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda5 during installation
UUID=6502-886A  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda3 during installation
UUID=84b30111-5052-43ab-887c-c954788e7890 /home           ext4    defaults        0       2
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
bootinfoscript: line 1656: [: 2.73495e+09: integer expression expected
```

/Cheers

---

### Post by Azyx on 2012-02-07
May this in the beguinning the boot script out-putbe the problem?

Boot sector info:  According to the info in the boot sector, sda1 starts at sector 0. But according to the info from fdisk, sda1 starts at sector 2048.

Anyone knowing how to fix it?

/Cheers

---

### Post by oldfred on 2012-02-07
I have not seen enough boot scripts from efi systems to know if this is a standard efi entry or not, but you are in BIOS/MBR mode and should not have it in fstab.

> # /boot/efi was on /dev/sda5 during installation
UUID=6502-886A  /boot/efi       vfat    defaults        0       1

From liveCD.
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab

Windows uses a boot flag, grub does not, but some BIOS need to see  a boot flag to let you boot. From gparted or Disk Utility add the boot flag to any primary partition.

Normally the script also shows core.img in the boot partition if grub is installed correctly. Not sure if it needs full reinstall or just a install to the MBR again.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

You have used all 4 primary partitions. If you want to add more, one should be the extended partition and then inside the extended you can create any number of logical partitions. 

If gpt all partitions are primary, but you cannot install Windows 64 bit unless in UEFI mode. I use gpt on my Linux only drives with BIOS, but then have to have a bios_grub partition for core.img.

---

### Post by Azyx on 2012-02-07
Oldfred.
Have little understanding between BIOS/MBR and EFI and EFI-partitions :(

I think I do a new install. You see that sda1 started on 0 or 2048 wich it complainde about in the beguinning. Could It be that befor I hade an extended partition, but now have changed to primary?


If I erase sda1,sda2 and sda3 (will keep sda4, becouse I have some data there I want to keep. After I have erased these 3 partisions, should I first make an extended partition and then under there make my other partiton?  I don't really understand the diffenens between primary vs extended, exept that you may have more than 4 if you have extended. Why have primary partition  at all?

/Cheers

---

### Post by Azyx on 2012-02-07
I made a new install and used extended- instead of primary-partitions. Now when I tried to boot from my hardisk after a successfull install ;) the Grub  rescue promp appear with a message like "unknown file system" I run the boot script as Oldfred  showed me with this out-put:

```
Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:  Syslinux looks at sector 1434632 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               4,094   214,358,015   214,353,922   5 Extended
/dev/sda5    *          4,096       229,375       225,280   6 FAT16
/dev/sda6             231,424    22,759,423    22,528,000  83 Linux
/dev/sda7          22,761,472   214,358,015   191,596,544  83 Linux
/dev/sda2         214,358,016   222,756,863     8,398,848  82 Linux swap / Solaris
/dev/sda4         222,757,290   488,392,064   265,634,775  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        664c7fa0-d194-4dd7-81e1-a84705dc2135   swap       
/dev/sda4        6a0838f8-2b9a-4597-8fa6-a0a0f7b3610b   ext4       120GB
/dev/sda5        BE60-FF54                              vfat       
/dev/sda6        0b8e1990-d857-4010-886d-89178c50577a   ext4       
/dev/sda7        529e4aa4-7119-46b4-b5b9-645d2ed1e3c7   ext4       
/dev/sdb1        E128-3DB1                              vfat       2GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
  insmod gettext
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
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=0b8e1990-d857-4010-886d-89178c50577a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-12-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
    echo    'Läser in Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=0b8e1990-d857-4010-886d-89178c50577a ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 0b8e1990-d857-4010-886d-89178c50577a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=0b8e1990-d857-4010-886d-89178c50577a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda5 during installation
UUID=BE60-FF54  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda7 during installation
UUID=529e4aa4-7119-46b4-b5b9-645d2ed1e3c7 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=664c7fa0-d194-4dd7-81e1-a84705dc2135 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
bootinfoscript: line 1656: [: 2.73495e+09: integer expression expected
```

Cheers

---

### Post by YannBuntu on 2012-02-07
Hello
your current EFI partition is on sda5, which may not be adequate. If I were you, i would format everything, then with gParted live-CD (some problems with the gParted of 11.10 CD have been reported), create the EFI partition (FAT32, EFI flag, 200Mo) at the beginning of the disk (sda1), then run Ubuntu installer.

EDIT: i've been told that the Ubuntu installer does a bad automatic partitioning, so when you run the Ubuntu installer, choose manual partitioning ("Other"), and create yourself a SWAP partition (~size of your RAM), and a Ubuntu system partition (EXT4, minimum 20Go, mounted on / ).

---

### Post by oldfred on 2012-02-07
If you are booting in UEFI mode, the efi partition has to be sda1. But to get efi mode to work I think you have to partition with gpt not MBR. You can convert from mbr to gpt (or vice-versa) if you want to keep the one partition, but any major change to system has risks and you need to have good backups.

As YannBuntu says the installer does not really work correctly with UEFI and you have to partition in advance. And even in MBR mode it is better to partition in advance.

Windows has to have a primary to boot from. When hard drives first appeared in the '80s with DOS they only allowed primary partitions. But then they realized they need more and let you make one primary into an extended to hold the logical. Some computers will not boot without  a primary partition with the boot flag (assumes Windows?).

Info on gpt & UEFI, but I think in your case it just would be better to stay with BIOS/MBR mode. Then you do not have an efi partition.

[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

[http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

---

### Post by Azyx on 2012-02-07
Okey. Yannabuntu and Oldfred.

To change MBR to GTP i need to change the hole sda, and then all partition get lost, so the solution seems to be to clean the hole disk. Will see where I may put the data./Cheers

Or  maybe not but it is the easiest way i think.

---

### Post by oldfred on 2012-02-07
Is this a brand new system with a smaller drive? Only new systems/motherboards support the UEFI boot. Were you ever going to install Windows on this drive. If not gpt is better whether in BIOS or UEFI mode. With BIOS you also need the 1MB bios_grub partition.

Direct link to the instructions on converting from mbr to gpt.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

I used gparted to create gpt drives but that does reformat entire drive.

---

### Post by Azyx on 2012-02-07
> **oldfred said:**
> Is this a brand new system with a smaller drive? Only new systems/motherboards support the UEFI boot. Were you ever going to install Windows on this drive. If not gpt is better whether in BIOS or UEFI mode. With BIOS you also need the 1MB bios_grub partition.

Direct link to the instructions on converting from mbr to gpt.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

I used gparted to create gpt drives but that does reformat entire drive.

The motherboard is new and have EFI instead of BIOS. [http://www.asus.se/Motherboards/AMD_CPU_on_Board/E45M1M_PRO/](http://www.asus.se/Motherboards/AMD_CPU_on_Board/E45M1M_PRO/)
with 8GB RAM
I do not intend to have any windows on it, maybe a virtal-machine... I have now formated the 250GB sda with GTP, not MBR and made a 200MB FAT32 partition named sda1 :) Whait on the install just now...

---

### Post by Azyx on 2012-02-07
It worked :)
Not a nice way to fix it, but it worked. Thanx YannBuntu and Oldfred :)

---

### Post by oldfred on 2012-02-07
Glad you got it working.

Could you post a new run of boot info script, just so we can see a working install with efi. Thanks

---

### Post by Azyx on 2012-02-07
> **oldfred said:**
> Glad you got it working.

Could you post a new run of boot info script, just so we can see a working install with efi. Thanks
. Here it comes.

```
              Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    13849423 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 huvuden, 63 sektorer/spår, 30401 cylindrar, totalt 488397168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       410,190       410,157 Data partition (Windows/Linux)
/dev/sda2         410,191    22,939,487    22,529,297 Data partition (Windows/Linux)
/dev/sda3      22,939,488    30,751,988     7,812,501 Swap partition (Linux)
/dev/sda4      30,751,989   245,595,739   214,843,751 Data partition (Windows/Linux)
/dev/sda5     245,595,740   488,396,521   242,800,782 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DD6E-864D                              vfat       
/dev/sda2        e744f7bb-b932-4603-afc3-e5030b66dcdc   ext4       
/dev/sda3        aee6a155-4b79-40c4-b59c-c615556b4cf7   swap       
/dev/sda4        d2586b39-0c53-41e0-bf8f-fc6f5d9e13f8   ext4       
/dev/sda5        124487c6-f4f5-4b7a-8cae-2647d30ff1e4   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /home                    ext4       (rw,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
  insmod gettext
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
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e744f7bb-b932-4603-afc3-e5030b66dcdc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-12-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
    echo    'Läser in Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e744f7bb-b932-4603-afc3-e5030b66dcdc ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root e744f7bb-b932-4603-afc3-e5030b66dcdc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=e744f7bb-b932-4603-afc3-e5030b66dcdc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=d2586b39-0c53-41e0-bf8f-fc6f5d9e13f8 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=DD6E-864D  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=aee6a155-4b79-40c4-b59c-c615556b4cf7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

/Cheers

---

### Post by Azyx on 2012-02-07
Seems to be some corrupted data in the end?

Seems to be possible to have more than 4 primary partitions in GPT? And do they not have extended and logical partions?

---

### Post by oldfred on 2012-02-07
You just do not have gawk installed so it could not calculate where on drive the kernel files were. Not an issue.

You are still in BIOS mode. It is not booting with UEFI.

Since you are in BIOS mode you should create a small 1MB bios_grub partition. It can be anywhere on drive.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.


In gpt all partitions are primary, one of its advantages.

How did you create partitions? All the new partition tools set starts of partitions to be divisible by 8 for greatest compatibility with all types of new systems.

This is my new SSD with gpt. I create the efi partition for future use, but actually use the bios_grub as I still boot with BIOS. I may get a new system this year and then an UEFI install will not require me to totally reformat.

```
Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1   117,231,407   117,231,407  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048       616,447       614,400 EFI System partition
/dev/sdd2         616,448       618,495         2,048 BIOS Boot partition
/dev/sdd3         618,496    58,925,055    58,306,560 Data partition (Windows/Linux)
/dev/sdd4      58,925,056   117,229,567    58,304,512 Data partition (Windows/Linux)

```

---

### Post by Azyx on 2012-02-07
I made all changes in a livemedia. First format with disk-utilities and made a GPT disk. Then I used gparted to make five primary partitions. But then I rebooted and installed, there where some 'hole between the patitions so I removed all partitions and created them again  in the partitioner in the installation application. I could not find any EFI-boot or something in the install partiton, but when I continiied so did it ask for mounting point on the 200MB FAT. I could only find two. windows or dos. I chose windows.. 

It is late here, so I will check more tomorow. Thanx. Cheers

---

### Post by Azyx on 2012-02-08
Have some questions in [COLOR="red"]red[/COLOR].

> **oldfred said:**
> 
You are still in BIOS mode. It is not booting with UEFI.

Since you are in BIOS mode you should create a small 1MB bios_grub partition. It can be anywhere on drive.

[COLOR="Red"]Why is a separate Grub partition necessary? Tried to shrink sda1 (200MiB big with FAT), but get some error message that Gparted was not able to make a lesser partiton, than the file system, or some like that.... The massage also said that they work on the problem....
[/COLOR]

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

[COLOR="red"]How do I change between EFI mode and BIOS mode?[/COLOR]

How did you create partitions? All the new partition tools set starts of partitions to be divisible by 8 for greatest compatibility with all types of new systems.

[COLOR="Red"]Can you explain this more? I have five partiitions now, do I need 8?[/COLOR]
[/CODE]

/Cheers

---

### Post by oldfred on 2012-02-08
It is not 8 partitions but the sectors are divisable by 8. So instead of starting at sector 34, the first sector starts at 40, but all the new partition tools start at sector 2048.

The bios_grub partition only has to be 1MB which is (I think) the smallest that gparted will let you make. Are you using gparted from liveCD? Just shrink any partition by 1MB and create a new one. Right click on flags and set bios_grub flag. Then reboot into your system and run this:

```
sudo grub-install /dev/sda
```

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.

Use BIOS Boot Partition of 1 MiB for partition alignment.

From what I gather with others with UEFI, there is no way to change from UEFI to BIOS. UEFI has a BIOS mode. It seems that it will try to boot from a efi partition and if not found, it reverts to BIOS mode and boots from MBR. Not sure how Windows or Ubuntu know to install automatically. But with Ubuntu only those who have partitioned in advance have gotten it to work.

---

### Post by Azyx on 2012-02-08
> **oldfred said:**
> 
The bios_grub partition only has to be 1MB which is (I think) the smallest that gparted will let you make. Are you using gparted from liveCD? Just shrink any partition by 1MB and create a new one. Right click on flags and set bios_grub flag. Then reboot into your system and run this:

```
sudo grub-install /dev/sda
```

[COLOR="Red"]I made a partition with no file system on it and flagged it as 'bios_grub' in the end of sda. I reboot, but it still boot from my /-partition that have the flag 'boot'. I don't what to damage the installation, but do I need to remove the 'boot' flag on my root partition? May I need to mark the first FAT32 partition as 'boot' for the computer to boot into EFI?[/COLOR]

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.

Use BIOS Boot Partition of 1 MiB for partition alignment.

From what I gather with others with UEFI, there is no way to change from UEFI to BIOS. UEFI has a BIOS mode. It seems that it will try to boot from a efi partition and if not found, it reverts to BIOS mode and boots from MBR. Not sure how Windows or Ubuntu know to install automatically. But with Ubuntu only those who have partitioned in advance have gotten it to work.

/Cheers

---

### Post by oldfred on 2012-02-08
Grub does not use boot flag at all. And as I posted before the "boot flag" in gpt is not really a MBR type boot flag.

The bios_grub is just used automatically on grub install as a place for core.img in gpt. In MBR it puts core.img in the sectors after the MBR where there is unused space. If there is no place for core.img it does a workaround that is less reliable.

---

### Post by Azyx on 2012-02-08
> **oldfred said:**
> Grub does not use boot flag at all. And as I posted before the "boot flag" in gpt is not really a MBR type boot flag.

The bios_grub is just used automatically on grub install as a place for core.img in gpt. In MBR it puts core.img in the sectors after the MBR where there is unused space. If there is no place for core.img it does a workaround that is less reliable.

Ok. but nothing happen, it's boot as it boot before I made a 1 MiB partition and in gparted 'flagged' is as 'bios_grub'. In gparted I also saw that sda2 was flagged as 'boot'.

Cheers

---

### Post by oldfred on 2012-02-08
Post this just to see what partitioning you have quickly.

sudo parted /dev/sda unit s print

---

### Post by Azyx on 2012-02-08
> **oldfred said:**
> Post this just to see what partitioning you have quickly.

sudo parted /dev/sda unit s print

```
sudo parted /dev/sda unit s print
[sudo] password for Azyx: 
Modell: ATA ST3250318AS (scsi)
Disk /dev/sda: 488397168s
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: gpt

Nummer  Början      ****        Storlek     Filsystem       Namn  Flaggor
 1      34s         410190s     410157s     fat32
 2      410191s     22939487s   22529297s   ext4                  startbar
 3      22939488s   30751988s   7812501s    linux-swap(v1)
 4      30751989s   245595739s  214843751s  ext4
 5      245595740s  488394751s  242799012s  ext4
 6      488394752s  488397134s  2383s       ext4                  bios_grub

Azyx@Blackus:~$ 
```

I see now it was formmatted as ext4 :(

---

### Post by oldfred on 2012-02-08
Ext4 is the default. You should not have formated it. I am not sure if you have to delete it and recreate it or can just change to unformated?

I would also remove the boot flag from sda2. That should only be on sda1 if you want to totally reinstall and create the efi boot. You may be able to create a efi boot by moving flag to sda1 and totally reinstalling grub, but there is no real advantage to UEFI over BIOS unless you also want to dual boot with Windows. And then it is more complex.

Edit - unformated is one of the format options in gparted, so I would just change it to unformated.

---

### Post by Azyx on 2012-02-08
> **oldfred said:**
> Ext4 is the default. You should not have formated it. I am not sure if you have to delete it and recreate it or can just change to unformated?

I would also remove the boot flag from sda2. That should only be on sda1 if you want to totally reinstall and create the efi boot. You may be able to create a efi boot by moving flag to sda1 and totally reinstalling grub, but there is no real advantage to UEFI over BIOS unless you also want to dual boot with Windows. And then it is more complex.

Edit - unformated is one of the format options in gparted, so I would just change it to unformated.

I tested with no partition after, but the same result. Maybe I want to run OpenIndian or OSX, no windos here, so your recomendation is to remove 'startbar=boot' on sda2? How does i get to grub, if I remove boot-flag on sda2? Desent I need to first install grub on sda

```
Modell: ATA ST3250318AS (scsi)
Disk /dev/sda: 488397168s
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: gpt

Nummer  Början      ****        Storlek     Filsystem       Namn  Flaggor
 1      34s         410190s     410157s     fat32
 2      410191s     22939487s   22529297s   ext4                  startbar
 3      22939488s   30751988s   7812501s    linux-swap(v1)
 4      30751989s   245595739s  214843751s  ext4
 5      245595740s  488394751s  242799012s  ext4
 6      488394752s  488396799s  2048s                          bios_grub
```

---

### Post by oldfred on 2012-02-08
Windows uses a boot flag, grub does not use a boot flag. If booting with BIOS and gpt grub will automatically find the bios_grub partition and put core.img in the bios_grub.

You can try this to reinstall grub also:

sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

