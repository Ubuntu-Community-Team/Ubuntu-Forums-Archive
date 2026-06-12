---
title: "Error loading Operating System on boot"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by ~Z~ on 2010-09-30
Hello everyone!

Yes! It's another newbie here messing things up playing with multiple OS in an external disk... and things got messed up...

I have ubuntu 10.04 installed on an external disk (my desktop pc runs winXP), but then I tried to make another installation of winXP in that HD's first primary partition, wich was empty... but installation couldn't finish. After so many trials finally I give up in my attempt to get a "portable" winXP and try to boot as usual from the external hd to run Ubuntu, but I get this message instead: error loading Operating System (translated).

I'm pretty sure it just needs a small fix but I'm completely lost at this point, so any help will be much appreciated.

That's the RESULTS from boot_info_script.sh:
(to clarify, sda is "C", for windows and programs, sdb is only for data, and sdc is the external disk. sdc1 is a primary partition meant to hold an XP os installed, and sdc2 is an extended that have 2 partitions for 2 linux, a data partition and a swap).

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1953523056 sectors, but according to the info from 
                       fdisk, it has 1953525104 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disc /dev/sda: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disc /dev/sdb: 1000.2 GB, 1000204886016 octets
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,525,167 1,953,525,105  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disc /dev/sdc: 251.0 GB, 251000193024 octets
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048    40,962,047    40,960,000   7 HPFS/NTFS
/dev/sdc2          40,964,094   490,233,855   449,269,762   5 Extended
/dev/sdc5          40,964,096    81,924,095    40,960,000  83 Linux
/dev/sdc6          81,926,144   122,886,143    40,960,000  83 Linux
/dev/sdc7         122,888,192   479,993,855   357,105,664   7 HPFS/NTFS
/dev/sdc8         479,995,904   490,233,855    10,237,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8EBC95BDBC95A06F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F29820FA9820BF4B                       ntfs       DADES                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        DC04DD9904DD774C                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        8595e0d4-d8a7-4781-b791-fa1441307243   ext4       User00 L1                     
/dev/sdc6        21f23eca-d8ba-4102-aae4-9062e168076a   ext4       User00 L2                     
/dev/sdc7        02988F1C73CCB642                       ntfs       User00 D                      
/dev/sdc8        cf890c0e-5789-4288-bdff-d860101dc3c2   swap       User00 S                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/User00 L1         ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6        /media/User00 L2         ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/DC04DD9904DD774C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc7        /media/User00 D          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(2)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
set locale_dir=($root)/boot/grub/locale
set lang=ca
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
menuentry 'Ubuntu, amb Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8595e0d4-d8a7-4781-b791-fa1441307243 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, amb Linux 2.6.32-25-generic (mode de restabliment)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    echo    'Carregant Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8595e0d4-d8a7-4781-b791-fa1441307243 ro single 
    echo    'S'\''està carregant la ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, amb Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8595e0d4-d8a7-4781-b791-fa1441307243 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, amb Linux 2.6.32-21-generic (mode de restabliment)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    echo    'Carregant Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8595e0d4-d8a7-4781-b791-fa1441307243 ro single 
    echo    'S'\''està carregant la ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8595e0d4-d8a7-4781-b791-fa1441307243
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8ebc95bdbc95a06f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=8595e0d4-d8a7-4781-b791-fa1441307243 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc8 during installation
UUID=cf890c0e-5789-4288-bdff-d860101dc3c2 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


  31.9GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
  32.7GB: boot/initrd.img-2.6.32-21-generic
  32.9GB: boot/initrd.img-2.6.32-25-generic
  32.6GB: boot/vmlinuz-2.6.32-21-generic
  32.7GB: boot/vmlinuz-2.6.32-25-generic
  32.9GB: initrd.img
  32.7GB: initrd.img.old
  32.7GB: vmlinuz
  32.6GB: vmlinuz.old
```Yours,
~Z~

---

### Post by mikewhatever on 2010-09-30
Try reinstalling Grub.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
It's usually required after installing or attempting to install Windows.

---

### Post by ~Z~ on 2010-10-01
Thanks, it works fine now

---
PS: how can I change thread's tag to solved?
--
PS: nevermind ... I've found it!

---

