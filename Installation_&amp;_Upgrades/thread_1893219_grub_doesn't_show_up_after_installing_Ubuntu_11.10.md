---
title: "grub doesn't show up after installing Ubuntu 11.10 to dual boot with Windows 7"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by mattiv on 2011-12-09
I installed Ubuntu 11.10(x64) along with Windows 7(x64). The problem is silly: when booting Windows starts up normally, just as if I've done nothing. (That is, grub won't show up)

The installation went normally, and Windows Disk Management shows the partitions created by the installation. I am clueless as how to approach this problem, as I can't even get Ubuntu to boot.

What could I have possibly done wrong? Thanks in advance for any help!

---

### Post by lechien73 on 2011-12-09
Hi & welcome to the forums,

To check on your grub installation it would be good if you could boot from a LiveCD or LiveUSB, download the boot info script from [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net), and follow the instructions there to create a RESULTS.txt file.

When the RESULTS.txt file is created, please post it here. You can attach the file or, preferably, paste the contents between CODE tags (the **#** button on the toolbar)

---

### Post by darkod on 2011-12-09
Do you maybe have RAID running?

---

### Post by mattiv on 2011-12-09
I don't have a RAID. Below is the output of the boot info script:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 4137024 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the E:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   409,599,999   409,393,152   7 NTFS / exFAT / HPFS
/dev/sda3         409,600,000 3,497,424,895 3,087,824,896   7 NTFS / exFAT / HPFS
/dev/sda4       3,497,426,942 3,907,028,991   409,602,050   5 Extended
/dev/sda5       3,497,426,944 3,890,290,687   392,863,744  83 Linux
/dev/sda6       3,890,292,736 3,907,028,991    16,736,256  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8015 MB, 8015314944 bytes
5 heads, 32 sectors/track, 97843 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    15,654,911    15,646,848   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BC94EC5994EC1822                       ntfs       System Reserved
/dev/sda2        2C441CB4441C82AE                       ntfs       
/dev/sda3        C6C63722C63711E3                       ntfs       Storage
/dev/sda5        c1738035-a704-47fb-a779-c57261a801b2   ext4       
/dev/sda6        25bc2465-4eb6-403a-b25b-9feec105766e   swap       
/dev/sdb1        D97F-55BC                              vfat       STORE N GO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c1738035-a704-47fb-a779-c57261a801b2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c1738035-a704-47fb-a779-c57261a801b2 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c1738035-a704-47fb-a779-c57261a801b2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root BC94EC5994EC1822
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c1738035-a704-47fb-a779-c57261a801b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=25bc2465-4eb6-403a-b25b-9feec105766e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             2
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

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by darkod on 2011-12-09
From what ever reason, grub2 was not fully installed. The file /boot/grub/core.img is missing.

You can reinstall it if you enter the root partition (sda5) with chroot. From live mode in terminal:

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

To completely remove and reinstall grub2:

```
apt-get --purge remove grub-pc
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
```

That should do it. Exit the chroot and unmount:

```
exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

Reboot and see if it worked.

---

### Post by mattiv on 2011-12-10
Upon trying the above, I found out that no grub-pc was installed, instead I have grub-efi. I tried reinstalling this, but it didn't help with my problem.

What is the difference between these two? Should I try uninstalling grub-efi and installing grub-pc instead? :confused:

---

### Post by darkod on 2011-12-10
If you are using EFI boot, not BIOS, then grub2 needs a small partition with no filesystem which will have the bios_grub flag set. But that should exist before the installation so it can put it's files there, as far as I know.

Not sure if you can add it now. Don't have experience with EFI, still using the good old BIOS boot.

What you could try is boot up in live mode and delete all the ubuntu partitions with Gparted (be careful not to delete windows). Then in Gparted create a small 1MB (or the minimum it can, sometimes it's 8MB) with no filesystem. Not sure if you can create it without filesystem. If you need to select any filesystem, use FAT32.
Once it is create right click on it and select Manage Flags. Activate the bios_grub flag.

After that reinstall ubuntu again and it should work.

---

### Post by mattiv on 2011-12-10
> **darkod said:**
> Activate the bios_grub flag.

I can't see bios_grub flag in the Manage flags menu. Should I select the "boot" flag?

---

### Post by darkod on 2011-12-10
No, the boot flag is already set to /dev/sda1 where the windows boot files are, and that's the correct way.

The bios_grub might have related only to GPT partition tables and you have msdos (which I prefer).

Did you try entering BIOS and changing to BIOS boot? Just disable the EFI boot.

Note that at first it might not boot since you have no grub-pc but you can use the commands earlier and remove grub-efi and install grub-pc.

Since you already have msdos table and with BIOS boot it will most probably work fine.

---

### Post by mattiv on 2011-12-10
I didn't find an option to disable EFI boot in the EFI/BIOS menu. I tried uninstalling grub-efi and installing grub-pc anyway, and now it works! Apparently my system isn't set up to EFI boot, but the Ubuntu installer decided to install grub-efi anyway? For the record, my MB is Asus P8P67 LE.

Thank you all for helping me out! :)

---

### Post by darkod on 2011-12-10
Glad you got it sorted out. Very strange that it installed grub-efi but anyway you got it working. And now you know how to completely remove/reinstall grub2 from chroot. :)

Please mark the thread as SOLVED in Thread Tools above the first post.

---

