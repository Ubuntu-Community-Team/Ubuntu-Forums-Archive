---
title: "grub lost in upgrade"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by .volatile. on 2010-05-14
I would like to have your help.
I upgraded from 9.10 to 10.04 and lost my grub in  between.
During the upgrade I installed grub on sda1.

Can you help me to recover my grub.

I inserted the contents of the RESULTS.txt here.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 70052551 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector 39 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda8 and 
                       looks at sector 69700583 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #8 for /boot/grub.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,096,574     4,096,512   7 HPFS/NTFS
/dev/sda2           4,096,575   160,055,594   155,959,020   f W95 Ext d (LBA)
/dev/sda5           4,096,638    34,877,114    30,780,477   7 HPFS/NTFS
/dev/sda6          34,877,178    55,359,989    20,482,812   7 HPFS/NTFS
/dev/sda7          55,360,053    65,545,199    10,185,147   7 HPFS/NTFS
/dev/sda8          65,545,263    86,734,934    21,189,672  83 Linux
/dev/sda9          86,734,998    87,779,159     1,044,162  82 Linux swap / Solaris
/dev/sda10         87,779,223   160,055,594    72,276,372   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda10       4CDC5576DC555B72                       ntfs       iWORK                         
/dev/sda1        520C96BC0C969B15                       ntfs       base                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D2D03EF1D03EDC03                       ntfs       XP                            
/dev/sda6        087CFEDF7CFEC70A                       ntfs       TRANS-L                       
/dev/sda7        049865E59865D5A8                       ntfs       PROGs                         
/dev/sda8        b0eb733c-283e-45ba-9abd-f45d1d1838df   ext4                                     
/dev/sda9        92c4be46-1693-460a-95c4-03052aa2537c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=================== sda1: Location of files loaded by Grub: ===================


    hpGB: grub/core.img
    hpGB: grub/stage2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 520c96bc0c969b15
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=92c4be46-1693-460a-95c4-03052aa2537c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  35.8GB: boot/grub/core.img
  34.1GB: boot/grub/grub.cfg
  39.8GB: boot/initrd.img-2.6.31-20-generic
  42.7GB: boot/initrd.img-2.6.32-22-generic
  34.6GB: boot/vmlinuz-2.6.31-20-generic
  41.8GB: boot/vmlinuz-2.6.32-22-generic
  35.6GB: grub/core.img
  42.7GB: initrd.img
  41.8GB: vmlinuz
```

---

### Post by RascallHunter on 2010-05-14
If you hold down the shift key while booting, you should get a boot menu (grub) after the motherboard splash screen.

---

### Post by .volatile. on 2010-05-23
NO, unfortunately it has no effect.
With or without shift, the following message appears with the cursor at the end:

GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue>

---

### Post by wojox on 2010-05-23
Grub needs to be on /dev/sda 

Look here to reinstall from a LiveCD [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You should be able to reboot into ubuntu after and then run 

```
sudo update-grub
```

To get it to recognize your other partitions.

---

### Post by darkod on 2010-05-23
1. Boot into live mode and use this to remove grub2 from /dev/sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you want to fix partition #1 of disk /dev/sda.

Also, delete /grub/core.img from /dev/sda1.

2. Reinstall grub2 to the MBR of /dev/sda pointing to the correct root partition:

sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

3. Have you recently deleted any partitions? Your fstab says:
# / was on [COLOR=Red]/dev/sda9[/COLOR] during installation

however, right now / is /dev/sda8. Even if you manage to boot ubuntu it might not work OK because of this.

---

### Post by .volatile. on 2010-06-05
I followed WOJOX instructions and recovered my ubuntu grub properly.
However, after updating grub, although the windows partition was recognised, 
using it will not boot into Windows.
Can you help me with this?
Thank you.

---

### Post by darkod on 2010-06-05
> **darkod said:**
> 1. Boot into live mode and use this to remove grub2 from /dev/sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you want to fix partition #1 of disk /dev/sda.

Also, delete /grub/core.img from /dev/sda1.



Did you do this as suggested? Grub2 on /dev/sda1 is blocking windows boot.

---

