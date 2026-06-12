---
title: "windows 7 lost after ubuntu 10.10 install"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by devil_me on 2010-12-08
Hello, I just installed Ubuntu and running it. I wanted to have windows  xp, 7 and ubuntu on my 1tb hdd. I installed xp first and then seven and  ubuntu at last in different partitions. The problem now is the grub  seems to have replaced my windows boot loader. The menu shows windows 7  loader but when I hit it it returns to the grub boot menu. Please help  with this and thanks in advance for any help. I have run the bootscript  file provided. here is the output I got.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 163430648 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    24,579,449    24,579,387   7 HPFS/NTFS
/dev/sda2          24,579,511 1,953,503,999 1,928,924,489   f W95 Ext d (LBA)
/dev/sda5          24,579,513   157,694,039   133,114,527   7 HPFS/NTFS
/dev/sda6         198,659,853   608,253,029   409,593,177   7 HPFS/NTFS
/dev/sda7         608,253,093 1,017,846,269   409,593,177   7 HPFS/NTFS
/dev/sda8       1,017,846,333 1,427,439,509   409,593,177   7 HPFS/NTFS
/dev/sda9       1,427,439,573 1,953,503,999   526,064,427   7 HPFS/NTFS
/dev/sda10        182,839,296   198,658,047    15,818,752  82 Linux swap / Solaris
/dev/sda11        157,696,000   182,835,199    25,139,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       f5a106df-cc1b-49f3-99eb-3a2bb784c76a   swap                                     
/dev/sda1        1200D01E00D00B1D                       ntfs                                     
/dev/sda11       a4657051-db80-4ded-89d2-0bbcc4aa67fc   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        547C64027C63DCEC                       ntfs                                     
/dev/sda6        084C05BD4C05A692                       ntfs       My STuff                      
/dev/sda7        2430FF4530FF1D0C                       ntfs       Games & Soft                  
/dev/sda8        F850F50A50F4CFFC                       ntfs       Music & Photos                
/dev/sda9        54C4D2A6C4D2899E                       ntfs       Movies                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

========================== sda11/boot/grub/grub.cfg: ==========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1200d01e00d00b1d
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

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f5a106df-cc1b-49f3-99eb-3a2bb784c76a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


  83.6GB: boot/grub/core.img
  83.5GB: boot/grub/grub.cfg
  83.6GB: boot/initrd.img-2.6.35-22-generic
  83.6GB: boot/initrd.img-2.6.35-23-generic
  83.5GB: boot/vmlinuz-2.6.35-22-generic
  83.5GB: boot/vmlinuz-2.6.35-23-generic
  83.6GB: initrd.img
  83.6GB: initrd.img.old
  83.5GB: vmlinuz
  83.5GB: vmlinuz.old

```The partition table is
```

root@DOOM-PC:/home/doom# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01fb01fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531      121600   964462244+   f  W95 Ext'd (LBA)
/dev/sda5            1531        9816    66557263+   7  HPFS/NTFS
/dev/sda6           12367       37862   204796588+   7  HPFS/NTFS
/dev/sda7           37863       63358   204796588+   7  HPFS/NTFS
/dev/sda8           63359       88854   204796588+   7  HPFS/NTFS
/dev/sda9           88855      121600   263032213+   7  HPFS/NTFS
/dev/sda10          11382       12366     7909376   82  Linux swap / Solaris
/dev/sda11           9817       11381    12569600   83  Linux

Partition table entries are not in disk order

```

---

### Post by Quackers on 2010-12-08
The first thing I would try is to repair the XP bootloader with the fixmbr command from the command prompt in the repair console of the XP repair disc.
Then I would try to repair the Win 7 bootloader by running Startup repair 3 times from the Win 7 repair disc.
If both of those systems then boot ok I would install grub to where it would normally be installed - the mbr of sda.
That would be accomplished by booting from the Ubuntu Live cd and selecting "try ubuntu" from the initial menu, then start a terminal (Applications > Accessories > terminal) then running the following commands. You can copy/paste these commands into the terminal one at a time and pressing enter after each one.
```
sudo mkdir /mnt
sudo mount /dev/sda11 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note no partition number in the last command!

Then reboot. It will probably boot right into Ubuntu the first time.
If it does open a terminal and then run
```
sudo update-grub
```
and watch the terminal screen as grub.cfg is configured to see if the Windows XP loader and the Win 7 loader appear. If they do just reboot and you should be greeted by a grub menu with all three boot options.
I would urge you to check that all three options boot as expected.

---

### Post by devil_me on 2010-12-09
thank you very much about the help, I have tried a different approach to solve it myself.
I used test disk to recover the mbr by pressing backup mbr in utilities which got my windows loader menu back.
After that I tried installing grub from live cd onto sda11 which showed some flexnet message although the grub got it installed like a miracle. :) thank you very much. :)
And is there any solution for FlexNet issue. I was trying to search around the forums but found no solution. :(

---

### Post by sikander3786 on 2010-12-09
> **devil_me said:**
> thank you very much about the help, I have tried a different approach to solve it myself.
I used test disk to recover the mbr by pressing backup mbr in utilities which got my windows loader menu back.
After that I tried installing grub from live cd onto sda11 which showed some flexnet message although the grub got it installed like a miracle. :) thank you very much. :)
And is there any solution for FlexNet issue. I was trying to search around the forums but found no solution. :(
Can you please post the output of bootinfoscript once again, just for the sake of posterity?

If you can boot Ubuntu from HDD, you can run that boot script from there. No need to boot and Ubuntu Live CD/USB.

Thanks.

---

### Post by wilee-nilee on 2010-12-09
> **devil_me said:**
> thank you very much about the help, I have tried a different approach to solve it myself.
I used test disk to recover the mbr by pressing backup mbr in utilities which got my windows loader menu back.
After that I tried installing grub from live cd onto sda11 which showed some flexnet message although the grub got it installed like a miracle. :) thank you very much. :)
And is there any solution for FlexNet issue. I was trying to search around the forums but found no solution. :(

Grub would normally only go into sda the mbr, are you set on another bootloader like easybcd2 or another.

So can you boot W7 with its bootloader  but not Ubuntu?

See above post about the bootscript and let us know what is actually going on now.

---

### Post by devil_me on 2010-12-09
sorry I think I installed it on sda itself . Here is the commands I used
sudo -i
mount /dev/sda11 /mnt
grub-install --root-directory=/mnt/ /dev/sdaBut could you tell me why sda11 is mounted when the grub is actually needed to be installed on sda. I am a newbie with linux and grub. so please dont mind if my question is silly :)

---

### Post by wilee-nilee on 2010-12-09
> **devil_me said:**
> sorry I think I installed it on sda itself . Here is the commands I used
sudo -i
mount /dev/sda11 /mnt
grub-install --root-directory=/mnt/ /dev/sdaBut could you tell me why sda11 is mounted when the grub is actually needed to be installed on sda. I am a newbie with linux and grub. so please dont mind if my question is silly :)

Don't worry about the questions post the script so we can see what the mbr says and some other stuff. Same concerns as skander3786

---

### Post by sikander3786 on 2010-12-09
> **devil_me said:**
> sorry I think I installed it on sda itself . Here is the commands I used
sudo -i
mount /dev/sda11 /mnt
grub-install --root-directory=/mnt/ /dev/sdaBut could you tell me why sda11 is mounted when the grub is actually needed to be installed on sda. I am a newbie with linux and grub. so please dont mind if my question is silly :)
Those commands seem pretty ok but I am worried about the highlighted text here.

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  **Grub 2 is installed in the boot sector of sda1** and 
                       looks at sector 163430648 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM


---

### Post by devil_me on 2010-12-09
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for (,msdos11)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    24,579,449    24,579,387   7 HPFS/NTFS
/dev/sda2          24,579,511 1,953,503,999 1,928,924,489   f W95 Ext d (LBA)
/dev/sda5          24,579,513   157,694,039   133,114,527   7 HPFS/NTFS
/dev/sda6         198,659,853   608,253,029   409,593,177   7 HPFS/NTFS
/dev/sda7         608,253,093 1,017,846,269   409,593,177   7 HPFS/NTFS
/dev/sda8       1,017,846,333 1,427,439,509   409,593,177   7 HPFS/NTFS
/dev/sda9       1,427,439,573 1,953,503,999   526,064,427   7 HPFS/NTFS
/dev/sda10        182,839,296   198,658,047    15,818,752  82 Linux swap / Solaris
/dev/sda11        157,696,000   182,835,199    25,139,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       f5a106df-cc1b-49f3-99eb-3a2bb784c76a   swap                                     
/dev/sda1        1200D01E00D00B1D                       ntfs       winxp                         
/dev/sda11       a4657051-db80-4ded-89d2-0bbcc4aa67fc   ext3       ubuntu                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        547C64027C63DCEC                       ntfs       windows 7                     
/dev/sda6        084C05BD4C05A692                       ntfs       My STuff                      
/dev/sda7        2430FF4530FF1D0C                       ntfs       Games & Soft                  
/dev/sda8        F850F50A50F4CFFC                       ntfs       Music & Photos                
/dev/sda9        54C4D2A6C4D2899E                       ntfs       Movies                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/AHL               iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5        /media/windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

========================== sda11/boot/grub/menu.lst: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4657051-db80-4ded-89d2-0bbcc4aa67fc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-23-generic
uuid        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro quiet splash 
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro  single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        a4657051-db80-4ded-89d2-0bbcc4aa67fc
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

========================== sda11/boot/grub/grub.cfg: ==========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set a4657051-db80-4ded-89d2-0bbcc4aa67fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1200d01e00d00b1d
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

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=a4657051-db80-4ded-89d2-0bbcc4aa67fc /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f5a106df-cc1b-49f3-99eb-3a2bb784c76a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


  83.6GB: boot/grub/core.img
  83.5GB: boot/grub/grub.cfg
  83.5GB: boot/grub/menu.lst
  83.6GB: boot/initrd.img-2.6.35-22-generic
  83.6GB: boot/initrd.img-2.6.35-23-generic
  83.5GB: boot/vmlinuz-2.6.35-22-generic
  83.5GB: boot/vmlinuz-2.6.35-23-generic
  83.6GB: initrd.img
  83.6GB: initrd.img.old
  83.5GB: vmlinuz
  83.5GB: vmlinuz.old

```

---

### Post by devil_me on 2010-12-09
> **sikander3786 said:**
> Those commands seem pretty ok but I am worried about the highlighted text here.
I think it installed in sda1 because while installing I selected "windows 7 loader" from the drop down that says "device for boot loader installation" which should be sda1 however I don't remember it exactly. :|

---

### Post by sikander3786 on 2010-12-09
> sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   [COLOR="Red"]**/boot/grub/menu.lst**[/COLOR] /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img


What is menu.lst doing there? Gotta go.

wilee-nilee would definitely guide you ;-)

---

### Post by wilee-nilee on 2010-12-09
see above post.

---

### Post by devil_me on 2010-12-09
above post??

---

### Post by wilee-nilee on 2010-12-09
Post #11 points out that you have now mixed grub-legacy  with grub2 

My mistake follow this link to purge grub and reinstall it use the correct cd to reload grub a maverick cd.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

