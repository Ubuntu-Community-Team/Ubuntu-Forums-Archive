---
title: "Grub Problems"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by pgs3223 on 2011-01-10
Hi

I am hoping somebody can help me please!

I have a Dell Inspiron laptop which was configured to Dual Boot Windows Vista and Ubuntu.

Tonight I inserted a USB Disk with an image of Ubuntu 10.10 Netbook installed on it and booted from it.

I then tried to install a copy of Ubuntu 10.10 Netbook edition on a second USB disk.

On completion I removed both USB disks and rebooted my Dell laptop to be greeted with the following message.

"error: no such device: fff8e559-d9fd-9e82-2dce7f438007
grub rescue>"

If I plug the USB disk back in that I installed Ubuntu Netbook edition on and reboot I am presented with a Grub boot menu and I can load Vista or Ubuntu that was originally installed on the HDD of my laptop.

Can anybody advise me how to edit the grub menu so that I can boot to Vista or Ubuntu on my HDD without having to have a USB device attached? 

Many thanks.

---

### Post by Quackers on 2011-01-10
From the Ubuntu desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pgs3223 on 2011-01-14
Thanks for your help, sorry for the delay in running the script, results below ;)

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652   6 FAT16
/dev/sda2    *        178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3          21,149,696   118,180,063    97,030,368   7 HPFS/NTFS
/dev/sda4         118,190,266   156,299,263    38,108,998   f W95 Ext d (LBA)
/dev/sda5         152,107,008   156,299,263     4,192,256  dd Dell Media Direct
/dev/sda6         118,190,268   150,593,309    32,403,042  83 Linux
/dev/sda7         150,593,373   152,103,419     1,510,047  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1053 MB, 1053556736 bytes
2 heads, 63 sectors/track, 16331 cylinders, total 2057728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0974ebeb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,057,727     2,057,696   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-031B                              vfat       DellUtility                   
/dev/sda2        6AE687FFE687CA31                       ntfs       RECOVERY                      
/dev/sda3        50EA8B50EA8B3170                       ntfs       OS                            
/dev/sda5        1C8F-AF23                              vfat       MEDIADIRECT                   
/dev/sda6        ffb33961-3fdd-4ee4-b36a-e3933a8758df   ext4                                     
/dev/sda7        2a7b911f-ab7c-4a27-81cf-39c3dc67a59f   swap                                     
/dev/sdb1        4004-BF0D                              vfat       UBUNTU810                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
```

```

---

### Post by oldfred on 2011-01-14
Did you run the script from an older liveCD? It says it cannot see ext4 partitions and Ubuntu since 9.04 has worked with ext4.

Script did not output all of the info on the linux partitions.

But grub says it is trying to boot from sda1 but the linux partition is sda6.

I would first try to reinstall grub to the MBR. But you will need a newer liveCd so it can read the ext4 partition.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by pgs3223 on 2011-01-15
OK I have re run the script with 10.10, please see below.

Can anybody suggest my next move!?

```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652   6 FAT16
/dev/sda2    *        178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3          21,149,696   118,180,063    97,030,368   7 HPFS/NTFS
/dev/sda4         118,190,266   156,299,263    38,108,998   f W95 Ext d (LBA)
/dev/sda5         152,107,008   156,299,263     4,192,256  dd Dell Media Direct
/dev/sda6         118,190,268   150,593,309    32,403,042  83 Linux
/dev/sda7         150,593,373   152,103,419     1,510,047  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
27 heads, 26 sectors/track, 11179 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,847,935     7,839,744   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 124 MB, 124518400 bytes
16 heads, 32 sectors/track, 475 cylinders, total 243200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       243,199       243,168   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       8c862bc1-fcb8-3d47-80a8-6172f9387ad6   ext2       casper-rw                     
/dev/sda1        07D7-031B                              vfat       DellUtility                   
/dev/sda2        6AE687FFE687CA31                       ntfs       RECOVERY                      
/dev/sda3        50EA8B50EA8B3170                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1C8F-AF23                              vfat       MEDIADIRECT                   
/dev/sda6        ffb33961-3fdd-4ee4-b36a-e3933a8758df   ext4                                     
/dev/sda7        2a7b911f-ab7c-4a27-81cf-39c3dc67a59f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5B95-0F81                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7CAD-0095                              vfat       USBDISKPRO                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd         BA21-890E                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd         /media/BA21-890E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/USBDISKPRO        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 

============================= sda6/grub/grub.cfg: =============================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-031b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 50ea8b50ea8b3170
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod fat
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1c8f-af23
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2a7b911f-ab7c-4a27-81cf-39c3dc67a59f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  60.9GB: boot/grub/core.img
  63.7GB: boot/grub/grub.cfg
  70.7GB: boot/initrd.img-2.6.31-14-generic
  70.9GB: boot/initrd.img-2.6.31-15-generic
  62.7GB: boot/initrd.img-2.6.31-16-generic
  70.1GB: boot/initrd.img-2.6.31-17-generic
  73.1GB: boot/initrd.img-2.6.31-19-generic
  64.8GB: boot/initrd.img-2.6.31-20-generic
  61.0GB: boot/initrd.img-2.6.32-21-generic
  62.6GB: boot/vmlinuz-2.6.31-14-generic
  71.5GB: boot/vmlinuz-2.6.31-15-generic
  68.7GB: boot/vmlinuz-2.6.31-16-generic
  61.2GB: boot/vmlinuz-2.6.31-17-generic
  73.1GB: boot/vmlinuz-2.6.31-19-generic
  66.9GB: boot/vmlinuz-2.6.31-20-generic
  65.9GB: boot/vmlinuz-2.6.32-21-generic
  76.7GB: grub/grub.cfg
  61.0GB: initrd.img
  64.8GB: initrd.img.old
  65.9GB: vmlinuz
  66.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 a0 10  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 00 20 00 00  |........?.... ..|
00000020  00 a0 77 00 90 07 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 81 0f 95 5b 54  72 61 6e 73 63 65 6e 64  |..)...[Transcend|
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 20 62 61 00  66 ba 00 00 00 00 bb 00  |}.f. ba.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /media/USBDISKPRO/ubnkern: Input/output error
hexdump: /media/USBDISKPRO/ubnkern: Input/output error
hexdump: /media/USBDISKPRO/ubnkern: Input/output error
```

```

---

### Post by pgs3223 on 2011-01-15
OK I have re run the script using a 10.10 image, please see below.

Can anybody suggest my next move please?

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652   6 FAT16
/dev/sda2    *        178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3          21,149,696   118,180,063    97,030,368   7 HPFS/NTFS
/dev/sda4         118,190,266   156,299,263    38,108,998   f W95 Ext d (LBA)
/dev/sda5         152,107,008   156,299,263     4,192,256  dd Dell Media Direct
/dev/sda6         118,190,268   150,593,309    32,403,042  83 Linux
/dev/sda7         150,593,373   152,103,419     1,510,047  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
27 heads, 26 sectors/track, 11179 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,847,935     7,839,744   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 124 MB, 124518400 bytes
16 heads, 32 sectors/track, 475 cylinders, total 243200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       243,199       243,168   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       8c862bc1-fcb8-3d47-80a8-6172f9387ad6   ext2       casper-rw                     
/dev/sda1        07D7-031B                              vfat       DellUtility                   
/dev/sda2        6AE687FFE687CA31                       ntfs       RECOVERY                      
/dev/sda3        50EA8B50EA8B3170                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1C8F-AF23                              vfat       MEDIADIRECT                   
/dev/sda6        ffb33961-3fdd-4ee4-b36a-e3933a8758df   ext4                                     
/dev/sda7        2a7b911f-ab7c-4a27-81cf-39c3dc67a59f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5B95-0F81                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7CAD-0095                              vfat       USBDISKPRO                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd         BA21-890E                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd         /media/BA21-890E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/USBDISKPRO        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 

============================= sda6/grub/grub.cfg: =============================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-031b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 50ea8b50ea8b3170
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod fat
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1c8f-af23
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2a7b911f-ab7c-4a27-81cf-39c3dc67a59f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  60.9GB: boot/grub/core.img
  63.7GB: boot/grub/grub.cfg
  70.7GB: boot/initrd.img-2.6.31-14-generic
  70.9GB: boot/initrd.img-2.6.31-15-generic
  62.7GB: boot/initrd.img-2.6.31-16-generic
  70.1GB: boot/initrd.img-2.6.31-17-generic
  73.1GB: boot/initrd.img-2.6.31-19-generic
  64.8GB: boot/initrd.img-2.6.31-20-generic
  61.0GB: boot/initrd.img-2.6.32-21-generic
  62.6GB: boot/vmlinuz-2.6.31-14-generic
  71.5GB: boot/vmlinuz-2.6.31-15-generic
  68.7GB: boot/vmlinuz-2.6.31-16-generic
  61.2GB: boot/vmlinuz-2.6.31-17-generic
  73.1GB: boot/vmlinuz-2.6.31-19-generic
  66.9GB: boot/vmlinuz-2.6.31-20-generic
  65.9GB: boot/vmlinuz-2.6.32-21-generic
  76.7GB: grub/grub.cfg
  61.0GB: initrd.img
  64.8GB: initrd.img.old
  65.9GB: vmlinuz
  66.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 a0 10  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 00 20 00 00  |........?.... ..|
00000020  00 a0 77 00 90 07 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 81 0f 95 5b 54  72 61 6e 73 63 65 6e 64  |..)...[Transcend|
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 20 62 61 00  66 ba 00 00 00 00 bb 00  |}.f. ba.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /media/USBDISKPRO/ubnkern: Input/output error
hexdump: /media/USBDISKPRO/ubnkern: Input/output error
hexdump: /media/USBDISKPRO/ubnkern: Input/output error
```

```

---

### Post by oldfred on 2011-01-16
Please use code tags, it preserves formatting and makes it a lot easier to review. Highlight and use # to automatically add code tags which you can do from the advanced tag when editing or just from edit panel when first posting.

Your grub in the MBR says it is looking for the rest of grub in sda1, but your install with the rest of grub is in sda6.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by pgs3223 on 2011-02-03
Thanks oldfred the article solved the problem!

Very grateful for your help and time!

---

