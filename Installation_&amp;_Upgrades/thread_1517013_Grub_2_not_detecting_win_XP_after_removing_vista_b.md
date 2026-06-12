---
title: "Grub 2 not detecting win XP after removing vista bootloader with easybcd 1.7.2"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by windaddy01 on 2010-06-24
Hi I'm new to this forum and Ubuntu and am having a problem getting grub 2 to detect Windows XP all it finds is the vista bootloaders i removed with easybcd 1.7.2 with the remove vista bootoader option and seems to boot in to windowsXP without a hitch when i select the hard drive it is installed on from bios select boot drive option but when i select the Ubuntu drive the vista bootloaders was still there so i tried the sudo update-grub command in the terminal and it still only detected the vista bootloaders  which neither boot anything so i tried reinstalling grub 2 form Ubuntu live CD and is said everything went ok and when i loaded the Ubuntu boot drive the same problem and so i tried deleting my vista partition and then running my windows xp cd and in type fixboot and fixmbr in recovery console and tried updating grub2 agian and that didn't work so  tried  reinstalling grub2 again through the live cd and once agian that didn't work and still able to boot in to windows xp without a problem if i select boot drive through the bios and i don't want to do that every time i want to boot into windows any solution will  be appreciated  

thanks in advance

---

### Post by darkod on 2010-06-24
First of all, don't write a continuous sentence of six lines. Do you think that was easy to read and understand?
I have no clue what you said.
To get more details of your setup, download the boot info script from my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by kalistona on 2010-06-24
stop !
you make a confusion vista has is own rules and xp anothers and linux is something else.

---

### Post by windaddy01 on 2010-06-24
it strange that its says windows xp in the boot info summary
but in the  30_os-prober section says their are two vista bootloaders which what i see when i'm the booting upand neither boot correctly

to see what i'm talking about use the find on page option and type the following 
sda1
sda3  
sda1/boot.ini  
/etc/grub.d/30_os-prober

also i'm sorry for making my post hard to read I'm not very good at writing 




  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 ```
=> Windows is installed in the MBR of /dev/sda
```
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```
sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

```
sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,665,794   241,665,732   7 HPFS/NTFS
/dev/sda3         323,597,295   398,283,479    74,686,185   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sdb2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sdb5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,770,143   976,770,081   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        042447F62447E96E                       ntfs       Local Disk                    
/dev/sda3        3A1FC4DB2B772EE7                       ntfs       chuy recover disk             
/dev/sda: PTTYPE="dos" 
/dev/sdb1        cc390cb9-386d-4397-ad7c-9863e80f1207   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        70919b5b-23e0-4b25-84a9-bdc1c9a92147   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4438FE9338FE836A                       ntfs       500GB                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/500GB             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP on D:\" /FASTDETECT 

=========================== sdb1/boot/grub/grub.cfg: ===========================
```

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
search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
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
search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cc390cb9-386d-4397-ad7c-9863e80f1207 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cc390cb9-386d-4397-ad7c-9863e80f1207 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cc390cb9-386d-4397-ad7c-9863e80f1207 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cc390cb9-386d-4397-ad7c-9863e80f1207 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set cc390cb9-386d-4397-ad7c-9863e80f1207
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 042447f62447e96e
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 4438fe9338fe836a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

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
# / was on /dev/sda1 during installation
UUID=cc390cb9-386d-4397-ad7c-9863e80f1207 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70919b5b-23e0-4b25-84a9-bdc1c9a92147 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
  34.5GB: boot/initrd.img-2.6.32-21-generic
  34.5GB: boot/initrd.img-2.6.32-22-generic
  34.4GB: boot/vmlinuz-2.6.32-21-generic
  34.5GB: boot/vmlinuz-2.6.32-22-generic
  34.5GB: initrd.img
  34.5GB: initrd.img.old
  34.5GB: vmlinuz
  34.4GB: vmlinuz.old

---

### Post by wilee-nilee on 2010-06-24
Would you please edit the scfript into code tags there are two ways to do this. First you can hit the edit button then advanced the highlight the text and click on the # in the panel. Second do this.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

The script takes up to much space and is harder to read as it is.:p

---

### Post by darkod on 2010-06-24
sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini [COLOR=Red]/bootmgr /Boot/BCD /grldr[/COLOR] /ntldr 
                       /NTDETECT.COM

The problem is that windows combines the boot files when you have two versions. I'm not sure whether the easybcd procedure you did was supposed to delete the vista boot files, or just modify them to include only XP but still to exist as a boot file.

/bootmgr and /boot/BCD are vista boot files. And /grldr also has no business there, don't know how it ended up there.

You can try booting ubuntu and moving those three files. Don't delete them in case that breaks the XP boot, just move them to your ubuntu home folder for example.
Then run:
sudo update-grub

See whether grub2 reports XP found, not vista.

As far as the vista loader on /dev/sdc1 is concerned, that looks like restore partition or similar. Grub2 just says what type of boot files it finds, and they look like vista so it's reported as vista loader.

---

### Post by windaddy01 on 2010-06-24
thanks darkod that did the trick it now finds windows xp and it boot perfectly from grub and doesn't find the vista bootloaders anymore

and thanks to everyone that tried to help

---

