---
title: "Upgrade to Lucid messed up dual boot to Windows"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by carltonh on 2010-05-08
I had 9.10 installed and it dual-booted fine into Windows, but the 10.04 upgrade killed it.  Let me first explain my special condition.

At one point I tested out the Windows 7 release candidate, and it installed a Windows boot loader that let me choose to boot my Windows XP hard drive or Windows 7.  I then installed Ubuntu 9.10 and its grub became the new "primary" boot menu.  But to choose Windows on the 9.10 grub menu, it would  bring up the Windows bootloader and from there I would choose Windows 7 or XP.  

Eventually, I deleted Win 7, but the Windows bootloader remained, I just had to choose XP in it after choosing "Windows 7" in the Grub menu.

Now with Lucid 10.04, choosing "Windows 7" no longer brings up the Windows 7 bootloader, and I have no idea how to boot into Win XP.

Any advice?

---

### Post by wilee-nilee on 2010-05-08
I suspect that during the upgrade you were given a choice of where to put grub and a mistake was made there. Post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also removing W7 which provided the default bootloader, is a problem.

---

### Post by carltonh on 2010-05-08
Here is the output below.  I understand half of this, but not enough to fix it:
----
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271479 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 271479 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb6 and 
                       looks at sector 271479 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Slackware 13.0.0.0.0
    Boot files/dirs:   /etc/fstab /etc/lilo.conf /boot/map

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,302,204   195,302,142  83 Linux
/dev/sdb2         195,302,205   488,392,064   293,089,860   5 Extended
/dev/sdb5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris
/dev/sdb6         195,318,333   468,519,659   273,201,327  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7E1854001853B5BD                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6f44db9e-4c08-4cb3-bfd1-6f37e5f878e1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8562a6e4-1261-4f5d-8bb9-9c3a38fc9de3   swap                                     
/dev/sdb6        77077a40-793d-438c-8b1c-a7678eb0f373   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=ch1)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

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
search --no-floppy --fs-uuid --set 6f44db9e-4c08-4cb3-bfd1-6f37e5f878e1
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

---

### Post by Sethcurtis on 2010-05-08
I am having a similar problem, i had WinServ 2008 and Ubuntu Karmic on grub menu Ubuntu boots fine no problem windows however, after being selected from grub menu goes directly to a black screen with a blinking horizontal cursor and does nothing from that point on.  

I have downloaded the Boot-info-script and will post the results along with this post thanks in advance, for any help.
[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 8996799 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 9006727 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CA45871A458303E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3a22ce12-0f10-4f5c-b7f8-4a4aaa53c3d7   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (rw,nosuid,nodev,utf8,user=seth)
/dev/sda1        /media/7CA45871A458303E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
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
search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
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
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Server 2008 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7ca45871a458303e
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3a22ce12-0f10-4f5c-b7f8-4a4aaa53c3d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.9GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.31-14-generic
   4.7GB: boot/initrd.img-2.6.32-22-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-22-generic
   4.7GB: initrd.img
   1.6GB: vmlinuz[/PHP]

---

### Post by wilee-nilee on 2010-05-08
@sethcurtis please start your own thread with the same information, it is difficult enough to take care of one of these problems at a time. ;)

Original thread starter pleas edit your script to look like the other by edit>highlight the script>then click on the # symbol in the edit panel, you have to have the flash block and all other blocks off to see the #. It is very difficult to read it without t\he scrolling text. :)

---

### Post by wilee-nilee on 2010-05-08
> **Sethcurtis said:**
> I am having a similar problem, i had WinServ 2008 and Ubuntu Karmic on grub menu Ubuntu boots fine no problem windows however, after being selected from grub menu goes directly to a black screen with a blinking horizontal cursor and does nothing from that point on.  

I have downloaded the Boot-info-script and will post the results along with this post thanks in advance, for any help.
[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 8996799 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 9006727 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CA45871A458303E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3a22ce12-0f10-4f5c-b7f8-4a4aaa53c3d7   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (rw,nosuid,nodev,utf8,user=seth)
/dev/sda1        /media/7CA45871A458303E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
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
search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
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
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Server 2008 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7ca45871a458303e
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=b654fdfd-2f6e-41fe-8e0b-3b2eb9ad2165 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3a22ce12-0f10-4f5c-b7f8-4a4aaa53c3d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.9GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.31-14-generic
   4.7GB: boot/initrd.img-2.6.32-22-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-22-generic
   4.7GB: initrd.img
   1.6GB: vmlinuz[/PHP]

You have grub in the windows area, try this, follow the directions carefully.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by carltonh on 2010-05-09
Thanks much Wilee-Nilee.  Test disk worked. I didn't do the last optional part of re-running "update-grub", and the grub menu is back to directing me to the Windows 7 bootloader where I have to choose Win XP, because I deleted Win 7, but that's no big deal.

This is why I love Ubuntu.  As long as wireless works, I can find someone who will help me.

---

