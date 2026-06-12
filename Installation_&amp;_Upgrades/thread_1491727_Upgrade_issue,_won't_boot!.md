---
title: "Upgrade issue, won't boot!"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by iluciferi on 2010-05-23
I just upgraded from 9.10 to 10.04 LTS. Did some Partial Update thing last night, and today all it will do is I get ready to login, the screen goes to black with [B]fsck from util-linux-ng 2.17.2
Clean something or other.
You can actually see the mouse cursor still there. How do I fix this? Oh and somehow grub is fudged (I have to select the hdd in a boot menu to get it to come up) and I have windows on a separate hdd and that is not booting either. Any help is greatly appreciated, as right now I am on a live thumb drive (thank god I created that thing)
[/B]

---

### Post by Arla on 2010-05-24
I'm seeing the same thing on a clean CLI install now.

I'm sure I booted into it once fine, but now it just comes up with that, I've tried using alt+f1 to goto the first terminal, and nothing there, only terminal that seems to have anything in it is the alt+f7 terminal, and that's normally the graphics, anyone have any idea?

---

### Post by wilee-nilee on 2010-05-24
So the only way to direct the problems with any accuracy is with posting this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You want to post it in code tags by pasting the results into a reply window highlight the text and click on the # in the reply panel, otherwise it is almost impossible to read.

Second post go ahead and start your own thread and post this script as no two problems are the same and this makes it much easier to get you some help. ;)

---

### Post by Arla on 2010-05-24
Well I SEEM to have solved mine by just unplugging the network cable, seems to boot fine if I don't have the network cable in during boot.

---

### Post by wilee-nilee on 2010-05-24
> **Arla said:**
> Well I SEEM to have solved mine by just unplugging the network cable, seems to boot fine if I don't have the network cable in during boot.

That is great.

---

### Post by iluciferi on 2010-05-25
Here is the output of the script. Sorry it took so long, my computer blew up exactly at the right time for me to have no time to fix it if you know what I mean.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 275966 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 286590 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde and 
                       looks at sector 276862 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sde has 0 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x012741a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeced7968

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *             63   321,669,494   321,669,432   5 Extended
/dev/sdb5                 126   314,343,854   314,343,729  83 Linux
/dev/sdb6         314,343,918   321,669,494     7,325,577  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4e78c640

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4126 MB, 4126146560 bytes
127 heads, 62 sectors/track, 1023 cylinders, total 8058880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a2747

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62     8,055,101     8,055,040   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       55f87ee2-7341-4d10-9f51-140d948b4858   ext3                                     
/dev/sda1        50BCEB96BCEB74BE                       ntfs                                     
/dev/sdb5        b3e28253-30a3-41ad-b8dd-b423da688ce8   ext4       Linux                         
/dev/sdb6        e1293ace-caba-4b87-b7d2-22d07cb019f5   swap                                     
/dev/sdc1        32FCFC99FCFC5895                       ntfs       STORAGE                       
/dev/sdd1        3D72-3D30                              vfat                                     
/dev/sde         C07E-5FAC                              vfat       PHONE                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3e28253-30a3-41ad-b8dd-b423da688ce8 ro splash vga=789  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3e28253-30a3-41ad-b8dd-b423da688ce8 ro single splash vga=789
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b3e28253-30a3-41ad-b8dd-b423da688ce8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 50bceb96bceb74be
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 32fcfc99fcfc5895
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b3e28253-30a3-41ad-b8dd-b423da688ce8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e1293ace-caba-4b87-b7d2-22d07cb019f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.32-22-generic
   1.0GB: boot/vmlinuz-2.6.32-22-generic
   3.6GB: initrd.img
   1.0GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
```
I hope there is an easy solution to this, as everything was running stable until this latest upgrade, and I would hate to have reinstall and reconfigure everything.

---

### Post by iluciferi on 2010-05-27
Ok I just wiped clean and did a fresh install. Same Issue. Goes to login, then goes to a black screen with text and the mouse cursor is frozen in the middle of it. Must be some sort of hardware incompatibility. As I am reading it is probably the graphics as I have a Intel 865G. [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes). I am going to try one of the work a rounds on this site and see if it works then I will report back, hopefully this will help other people that loaded this on a DELL OPTIPLEX.

---

### Post by iluciferi on 2010-05-27
Great. That didn't solve it either. And I have a dell d600 laptop that the netgear pmcia wifi card wont work in ubuntu 10.04 either. So far I am not liking this release one bit.

---

