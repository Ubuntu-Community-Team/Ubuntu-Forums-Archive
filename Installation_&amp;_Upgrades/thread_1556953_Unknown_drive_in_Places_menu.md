---
title: "Unknown drive in Places menu"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by gavdari on 2010-08-20
I have a NTFS partition called Local Disk on my hard drive. But beside that, there is another Local Disk in my places menu that whenever I click on it, I get the following error:
[HTML]Unable to mount Local Disk
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged[/HTML]There is no sign of this drive in /media or /mnt or even fstab. Here's my fstab file:
[HTML]UUID=36CC3005CC2FBE4D /media/Windows ntfs-3g defaults 0 0
UUID=C228E7D328E7C48F /media/Local\040Disk ntfs-3g users 0 0
UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 / ext4 defaults 0 1
UUID=810a447c-938a-4486-a8fe-0781b07c3fa5 swap swap sw 0 0[/HTML]

---

### Post by presence1960 on 2010-08-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by gavdari on 2010-08-20
Sorry it took long. Downloading from sourceforge in Iran is always a serious challenge.

[HTML]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/burg.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda2          20,563,261   625,141,759   604,578,499   f W95 Ext d (LBA)
/dev/sda5          20,563,263   122,961,509   102,398,247   7 HPFS/NTFS
/dev/sda6         122,961,573   522,915,749   399,954,177   7 HPFS/NTFS
/dev/sda7         522,915,840   620,869,631    97,953,792  83 Linux
/dev/sda8         620,871,680   625,141,759     4,270,080  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,952,151,551 1,952,149,504   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AAB6D921B6D8EEB7                       ntfs       RECOVERY                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36CC3005CC2FBE4D                       ntfs       Windows                       
/dev/sda6        C228E7D328E7C48F                       ntfs       Local Disk                    
/dev/sda7        37a593aa-f7f4-49a6-90f6-3926bea80590   ext4                                     
/dev/sda8        810a447c-938a-4486-a8fe-0781b07c3fa5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12C23AD8C23AC031                       ntfs       Siavash                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1161-F433                              vfat       ABNOOS                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/ABNOOS            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="Custom Menu"
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=300
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set aab6d921b6d8eeb7
    chainloader +1
}
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
menuentry "Custom Menu"{
        set root='(hd0,7)'
        search --no-floppy --fs-uuid --set 37a593aa-f7f4-49a6-90f6-3926bea80590
        configfile /boot/grub/custom_menu.cfg
        }

### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

UUID=36CC3005CC2FBE4D /media/Windows ntfs-3g defaults 0 0
UUID=C228E7D328E7C48F /media/Local\040Disk ntfs-3g users 0 0
UUID=37a593aa-f7f4-49a6-90f6-3926bea80590 / ext4 defaults 0 1
UUID=810a447c-938a-4486-a8fe-0781b07c3fa5 swap swap sw 0 0

=================== sda7: Location of files loaded by Grub: ===================


 306.5GB: boot/grub/core.img
 315.2GB: boot/grub/grub.cfg
 306.7GB: boot/initrd.img-2.6.32-21-generic
 306.7GB: boot/initrd.img-2.6.32-23-generic
 307.1GB: boot/initrd.img-2.6.32-24-generic
 267.8GB: boot/vmlinuz-2.6.32-21-generic
 306.7GB: boot/vmlinuz-2.6.32-23-generic
 307.0GB: boot/vmlinuz-2.6.32-24-generic
 307.1GB: initrd.img
 306.7GB: initrd.img.old
 307.0GB: vmlinuz
 306.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  34 16 00 00 34 16 00 00  34 16 00 00 34 16 00 00  |4...4...4...4...|
*
00000090  34 16 00 00 3c 2b 00 00  34 16 00 00 34 16 00 00  |4...<+..4...4...|
000000a0  34 16 00 00 f4 44 00 00  b0 14 00 00 34 16 00 00  |4....D......4...|
000000b0  34 16 00 00 3c 2b 00 00  34 16 00 00 34 16 00 00  |4...<+..4...4...|
000000c0  34 16 00 00 f4 44 00 00  b0 14 00 00 34 16 00 00  |4....D......4...|
000000d0  34 16 00 00 34 16 00 00  34 16 00 00 34 16 00 00  |4...4...4...4...|
*
00000110  34 16 00 00 84 1f 00 00  34 16 00 00 34 16 00 00  |4.......4...4...|
00000120  34 16 00 00 a0 2a 00 00  00 1e 00 00 34 16 00 00  |4....*......4...|
00000130  34 16 00 00 d4 3f 00 00  2c 2c 00 00 34 16 00 00  |4....?..,,..4...|
00000140  34 16 00 00 ac 27 00 00  2c 2c 00 00 34 16 00 00  |4....'..,,..4...|
00000150  34 16 00 00 2c 3f 00 00  78 3d 00 00 34 16 00 00  |4...,?..x=..4...|
00000160  34 16 00 00 34 16 00 00  34 16 00 00 34 16 00 00  |4...4...4...4...|
*
000001a0  34 16 00 00 80 1e 00 00  34 16 00 00 34 16 00 00  |4.......4...4...|
000001b0  34 16 00 00 ec 3f 00 00  34 16 00 00 34 16 00 fe  |4....?..4...4...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff 29 79  1a 06 40 d1 d6 17 00 00  |......)y..@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200[/HTML]

There is also a 1TB external hard drive and a 4GB flash memory connected.

---

### Post by gavdari on 2010-08-20
_bump_[]("http://ubuntuforums.org/showthread.php?t=1556931")

---

### Post by presence1960 on 2010-08-20
To tell you the truth I don't know how your windows is still booting because your windows 7 is in a logical partition (sda5) and it's boot files are combined with the boot files for your recovery partition (sda1)


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/burg.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR="Red"]Boot files/dirs:[/COLOR]   [COLOR="Blue"]/bootmgr /Boot/BCD /Windows/System32/winload.exe [/COLOR]
                       [COLOR="Purple"]/grldr /ntldr /NTDETECT.COM[/COLOR]

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

[COLOR="Red"]sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
[/COLOR]
sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda2          20,563,261   625,141,759   604,578,499   f W95 Ext d (LBA)
[COLOR="Red"]/dev/sda5          20,563,263   122,961,509   102,398,247   7 HPFS/NTFS[/COLOR]
/dev/sda6         122,961,573   522,915,749   399,954,177   7 HPFS/NTFS
/dev/sda7         522,915,840   620,869,631    97,953,792  83 Linux
/dev/sda8         620,871,680   625,141,759     4,270,080  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,952,151,551 1,952,149,504   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
[COLOR="Red"]/dev/sda1        AAB6D921B6D8EEB7                       ntfs       RECOVERY   [/COLOR]                   
/dev/sda2: PTTYPE="dos" 
[COLOR="Red"]/dev/sda5        36CC3005CC2FBE4D                       ntfs       Windows   [/COLOR]                    
/dev/sda6        C228E7D328E7C48F                       ntfs       Local Disk                    
/dev/sda7        37a593aa-f7f4-49a6-90f6-3926bea80590   ext4                                     
/dev/sda8        810a447c-938a-4486-a8fe-0781b07c3fa5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12C23AD8C23AC031                       ntfs       Siavash                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1161-F433                              vfat       ABNOOS                        
/dev/sdc: PTTYPE="dos"
```

---

