---
title: "windows to ubuntu"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by rahulife007 on 2010-11-15
hi, i had ubuntu 10.04 installed on my system..
i wanted to install windows xp also, so after
installation MBR got overwritten and i couldnt
boot ubuntu.. so i inserted a liveCD of 9.04 and 
changed the MBR by installing grub.. now when i boot
it is going to a CLI for grub and i have no clue what
to do.. 
from there i type in
chainloader (hd0,0)+1
which boots windows..
how can i get the grub menu from here??
thanks

---

### Post by kucerarichard on 2010-11-15
um,  newbe here.

why did you use a 9.04 live CD to deal with a 10.04 grub reinstall?   I thought there was a new grub for 10.04.

surely you mistyped your message...

---

### Post by Rubi1200 on 2010-11-15
kucerarichard is absolutely right on this one.

If you tried to install GRUB from a 9.04 CD you have likely mixed things up between legacy-GRUB (the former version) and GRUB2, which is used from version 9.10 onwards.

Please use the LiveCD and post the results of the boot info script linked at the bottom of my post.

The information will give us a definitive view of your setup and make offering solutions easier.

Thanks.

---

### Post by wilee-nilee on 2010-11-15
Click on the bootscript link in my signature, follow the instructions. The come back to the thread open a reply click on the # in the reply panel, this generates code tags paste the text from the generated file from running the boot script in between.

Edit: doh, rubi1200 beat me to it.;)

---

### Post by rahulife007 on 2010-11-15
yeah, im a newbee :) it was just that i didnt have the 10.04 cd at that time.. so tried it out with 9.04.. anyways i'll get back to u guys asap.. thanks a lot for ur help :)

---

### Post by rahulife007 on 2010-11-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

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

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,216   488,396,799   437,197,584   f W95 Ext d (LBA)
/dev/sda5          51,199,218   153,597,464   102,398,247   7 HPFS/NTFS
/dev/sda6         153,597,528   174,080,339    20,482,812   7 HPFS/NTFS
/dev/sda7         174,080,403   194,563,214    20,482,812   7 HPFS/NTFS
/dev/sda8         194,563,278   354,695,902   160,132,625   7 HPFS/NTFS
/dev/sda9         354,697,216   482,854,911   128,157,696  83 Linux
/dev/sda10        482,856,960   488,396,799     5,539,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       4c9c8d5f-cdf6-4db4-986c-a7c49c59878c   swap                                     
/dev/sda1        12D4206ED42055EF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7CE8EA24E8E9DD00                       ntfs                                     
/dev/sda6        FAC41F8AC41F4871                       ntfs       Rajendra                      
/dev/sda7        861067B71067ACBD                       ntfs                                     
/dev/sda8        7C48540F4853C714                       ntfs                                     
/dev/sda9        afa9636f-8a82-4ca6-ad77-1b753d446cdb   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/7CE8EA24E8E9DD00  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda9        /media/sda9              ext4       (rw)
/dev/sda1        /media/12D4206ED42055EF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Rajendra          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/861067B71067ACBD  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /media/7C48540F4853C714  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
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
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
insmod png
if background_image /home/rahul/Public/grub/bootpic.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set afa9636f-8a82-4ca6-ad77-1b753d446cdb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=afa9636f-8a82-4ca6-ad77-1b753d446cdb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=4c9c8d5f-cdf6-4db4-986c-a7c49c59878c none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 183.9GB: boot/grub/core.img
 201.3GB: boot/grub/grub.cfg
 183.7GB: boot/grub/stage2
 184.1GB: boot/initrd.img-2.6.32-21-generic
 184.3GB: boot/initrd.img-2.6.32-22-generic
 184.3GB: boot/initrd.img-2.6.32-23-generic
 184.3GB: boot/initrd.img-2.6.32-24-generic
 185.7GB: boot/initrd.img-2.6.32-25-generic
 184.0GB: boot/vmlinuz-2.6.32-21-generic
 184.1GB: boot/vmlinuz-2.6.32-22-generic
 184.2GB: boot/vmlinuz-2.6.32-23-generic
 184.3GB: boot/vmlinuz-2.6.32-24-generic
 184.9GB: boot/vmlinuz-2.6.32-25-generic
 185.7GB: initrd.img
 184.3GB: initrd.img.old
 184.9GB: vmlinuz
 184.3GB: vmlinuz.old

```

this is what i got in RESULTS.txt

---

### Post by Rubi1200 on 2010-11-16
Are you able to boot into Ubuntu?

The script seems fairly normal except for the fact that there are extra files in the GRUB configuration and that the script seems to indicate that Windows is not an option on the GRUB menu.

Have you tried booting Ubuntu from the prompt?

See here for some options:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052)

Go to the section entitled > **[COLOR=DarkRed][SIZE=3]'grub rescue>' Boot Procedures[/SIZE][/COLOR]**and try using what drs305 has put together.

If you can get into Ubuntu from there, run this command in the terminal and see if it picks up the Windows install as well as allowing you to boot Ubuntu normally:
```
sudo update-grub
```
**[COLOR=DarkRed][SIZE=3][/SIZE][/COLOR]**

---

### Post by rahulife007 on 2010-11-16
thanks so much for ur help :)

---

### Post by Rubi1200 on 2010-11-16
You are more than welcome :)

I am assuming since you marked this Solved that everything is working again?

But, it would have been nice to hear some of the dirty details ;)

---

