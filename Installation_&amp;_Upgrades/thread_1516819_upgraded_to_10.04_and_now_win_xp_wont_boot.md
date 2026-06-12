---
title: "upgraded to 10.04 and now win xp wont boot"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by whoya on 2010-06-24
Hello all, i just upgraded from 9.10 to 10.04 and now i cant get win xp to boot. win xp will show up on the grub list but when i select it all i get is a blank screen with a cursor flashing in the top left corner. i dunno whats happend, i have never had many problems with dual boot.
cheers

---

### Post by byStanderone on 2010-06-24
...haven't encountered this problem personally, but have seen threads about this in the forum. would catchup should i be able to look over it, and post it here.

---

### Post by whoya on 2010-06-24
thanks byStanderone, im having a look but not having much luck.

---

### Post by darkod on 2010-06-24
You probably installed grub2 to the XP partition when asked where to install. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You should know which your XP partition is, if not sure, ask.

---

### Post by whoya on 2010-06-24
i ran the boot info code from meierfra, here is the results, sorry if it doesnt post propley. 

  ```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 160821575 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb2 starts at sector 1040385465.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,043,129   151,043,067   7 HPFS/NTFS
/dev/sda2         156,280,320   312,576,704   156,296,385   5 Extended
/dev/sda5         156,280,383   234,340,154    78,059,772  83 Linux
/dev/sda6         234,340,218   309,267,314    74,927,097  83 Linux
/dev/sda7         309,267,378   312,576,704     3,309,327  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,040,385,464 1,040,385,402  83 Linux
/dev/sdb2    *  1,040,385,465 1,352,946,104   312,560,640   7 HPFS/NTFS
/dev/sdb3       1,352,946,105 1,953,520,064   600,573,960   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C0434550434448C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        628c0358-4a25-431e-8765-914676dbe195   ext4                                     
/dev/sda6        d8da4edd-83d7-43ee-9dcb-53714bb041bf   ext4                                     
/dev/sda7        b3494dc6-8f77-499d-bf07-a1fcfccc3e2d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a37ec84d-2bd7-432d-9003-e54f60caaf89   ext3                                     
/dev/sdb2        A4FCB5B6FCB582DA                       ntfs                                     
/dev/sdb3        04B9822637E29394                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noexecute=optout 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=628c0358-4a25-431e-8765-914676dbe195 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=628c0358-4a25-431e-8765-914676dbe195 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=628c0358-4a25-431e-8765-914676dbe195 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=628c0358-4a25-431e-8765-914676dbe195 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 628c0358-4a25-431e-8765-914676dbe195
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c0434550434448c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a4fcb5b6fcb582da
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=628c0358-4a25-431e-8765-914676dbe195 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d8da4edd-83d7-43ee-9dcb-53714bb041bf /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b3494dc6-8f77-499d-bf07-a1fcfccc3e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  82.3GB: boot/grub/core.img
  86.7GB: boot/grub/grub.cfg
  85.7GB: boot/initrd.img-2.6.31-22-generic
  88.4GB: boot/initrd.img-2.6.32-22-generic
  85.5GB: boot/vmlinuz-2.6.31-22-generic
  87.6GB: boot/vmlinuz-2.6.32-22-generic
  88.4GB: initrd.img
  85.7GB: initrd.img.old
  87.6GB: vmlinuz
  85.5GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```                i think i might have put grub on the wrong partion. 
i hope this helps
thanks for the replys so far

---

### Post by darkod on 2010-06-24
Yes, you installed grub2 to /dev/sda1, your XP partition.

With the link in my previous post, just remove it from there. So, it's partition #1 on disk /dev/sda.

---

### Post by whoya on 2010-06-24
darkod, that link work a treat, i did the testdisk, and now it all works, i didnt even have to update grub. cheers mate. now i can crash for the night.
thanks for your help

---

