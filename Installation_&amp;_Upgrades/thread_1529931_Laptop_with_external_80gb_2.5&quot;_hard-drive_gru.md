---
title: "Laptop with external 80gb 2.5&quot; hard-drive grub won't boot to /dev/sdb!!"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by mrwaterdancer on 2010-07-12
I have HP 6930p laptop with an external 2.5" 80gb hard drive and at the end of the installation, I clicked "Advanced" and set grub to install to "[x] /dev/sdb". Installation went fine, no trouble.

Then when I click boot from USB drive (I manually press 9), the screen would flicker, but Ubuntu 10.04 that I've installed will just skip and it will load windows.

I tried booting from the liveCD and it seems it's correct .. but /boot/grub.cfg list it as hd1,1 (I read somewhere that grub boot drive always has to be hd0,1 ??)

At this point, I've tried modifying /boot/grub.cfg then tried to install ... then gave me an error message something about GPT in that 80gb USB drive. I'm assuming this was created by GRUB2 ...

Anyways, I've tried booting to a USB drive from my HP 6930p for Knoppix and it works. Not sure why Ubuntu won't boot.

Does anyone know how to fix it? grub-install /dev/sdb --root-directory=/media/43612412-123123123 doesn't work and it gave me that error. And oh .. there's already a 1Mb partition listed apparently.

I don't have lots of time to tinker as I'm not young anymore, I'd love something that works and willing to pay for something that works out of the box without bugs like this.

I'm still willing to try it one more time, but after that I'm just going to skip .. appreciate it if someone can give me an instruction on how to fix it. I just want to see what's so great with Ubuntu.

---

### Post by mrwaterdancer on 2010-07-12
By the way, /dev/sda works (and later I restored Windows 7 MBR) but I don't want it to install to my laptop harddrive. I want it to be installed on that USB drive. If Windows XP works, why not Ubuntu? This is quite a basic procedure and I was hoping that Ubuntu would work when I checked that box [x] to install to /dev/sdb

---

### Post by mrwaterdancer on 2010-07-13
Here's the result of Boot_info_script if anyone can help 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 33860224 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   620,021,759   619,814,912   7 HPFS/NTFS
/dev/sda3         620,021,760   625,137,663     5,115,904   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048   148,488,191   148,486,144 Linux or Data
/dev/sdb2     148,488,192   156,301,311     7,813,120 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   D206-68B2                              vfat                                     
/dev/sda1        4AE277C6E277B533                       ntfs       System Reserved               
/dev/sda2        0A02858602857809                       ntfs                                     
/dev/sda3        DC4F-5282                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a03cfdd0-c4a4-42fd-8bca-03ad795bf623   ext4                                     
/dev/sdb2        82074f85-77df-4096-84f4-fba4323d4579   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/a03cfdd0-c4a4-42fd-8bca-03ad795bf623 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a03cfdd0-c4a4-42fd-8bca-03ad795bf623 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a03cfdd0-c4a4-42fd-8bca-03ad795bf623 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a03cfdd0-c4a4-42fd-8bca-03ad795bf623
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ae277c6e277b533
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a03cfdd0-c4a4-42fd-8bca-03ad795bf623 /               ext4    errors=remount-ro 0       1
# /mnt/windows was on /dev/sda2 during installation
UUID=0A02858602857809 /mnt/windows    ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb2 during installation
UUID=82074f85-77df-4096-84f4-fba4323d4579 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  64.5GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: initrd.img
  17.3GB: vmlinuz

```

---

### Post by mrwaterdancer on 2010-07-13
root@ubuntu:/media/a03cfdd0-c4a4-42fd-8bca-03ad795bf623/boot/grub# grub-install /dev/sdb --root-directory=/media/a03cfdd0-c4a4-42fd-8bca-03ad795bf623/
/usr/sbin/grub-setup: **warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.**
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by mrwaterdancer on 2010-07-13
root@ubuntu:/# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       38595   309907456    7  HPFS/NTFS
/dev/sda3           38595       38914     2557952    c  W95 FAT32 (LBA)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfea99daf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9730    78150743+  ee  GPT

Disk /dev/mmcblk0: 3980 MB, 3980394496 bytes
9 heads, 8 sectors/track, 107975 cylinders
Units = cylinders of 72 * 512 = 36864 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             114      107976     3883008    b  W95 FAT32
root@ubuntu:/# ^C

---

