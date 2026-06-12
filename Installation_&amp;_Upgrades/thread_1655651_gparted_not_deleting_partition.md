---
title: "gparted not deleting partition"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by degarb on 2010-12-29
I tried to install ubuntu on exernal drive and install grub there.  But no joy.   I had to do on primary master.

Now grub shows 2 linuxes on machine, which is a pain, since I cannot boot this other install on external from grub.

I am trying to delete and create that partion with gparted.  But won't delete it, even after unmounting it.

---

### Post by Quackers on 2010-12-29
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by degarb on 2010-12-29
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst /boot.ini /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 68660608 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    55,627,775    55,627,713   7 HPFS/NTFS
/dev/sda2          55,627,776    59,734,015     4,106,240  82 Linux swap / Solaris
/dev/sda3          59,734,016    78,163,967    18,429,952  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   240,107,489   240,107,427   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,934,559   234,934,497   7 HPFS/NTFS
/dev/sdc2         234,934,560   390,716,864   155,782,305   f W95 Ext d (LBA)
/dev/sdc5         234,934,623   390,716,864   155,782,242   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   918,177,797   918,177,735   7 HPFS/NTFS
/dev/sde2         918,179,838   976,771,071    58,591,234   5 Extended
/dev/sde5         918,181,888   976,771,071    58,589,184  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3ECC2741CC26F337                       ntfs       =you                          
/dev/sda2        fa0ac7e1-6154-4e96-afc7-37865af56e71   swap                                     
/dev/sda3        54dc02da-1408-440d-8017-d93a744fda1f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01C71EEF4317D1C0                       ntfs       200g part1                    
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        01C71EEF45728AA0                       ntfs       200gig p2 74 gig              
/dev/sdc: PTTYPE="dos" 
/dev/sde1        32C4647DC46444E7                       ntfs       Iomega HDD                    
/dev/sde2: PTTYPE="dos" 
/dev/sde5        bd312c42-22f1-41a7-815b-ff49d970bc52   ext4                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/200gig p2 74 gig  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/=you              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde5        /media/usb0              ext4       (rw,noexec,nodev,sync,noatime,nodiratime)


=========================== sda1/boot/grub/menu.lst: ===========================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default


title Boot from hard disk 3 image
#   map (hd3,0)/aa.dsk (hd3)
   map (hd3) (hd3)
   map --hook
   chainloader (hd3,0)+1
   rootnoverify (h3,0)
savedefault --wait=2

title find and load grub2
find --set-root /boot/grub/core.img
kernel /boot/grub/core.img
boot
savedefault --wait=2

title UBuntu attempt 1
fallback 3
root (hd3,0) ##(remember, this is Grub 1 Notation = /dev/sda7)
kernel /boot/grub/core.img
boot
savedefault --wait=2

title UBuntu attempt 2
fallback 4
root (hd3,4)
kernel /casper/vmlinuz root=/dev/sde5 ro 
initrd /casper/initrd.lz
boot
savedefault --wait=2

title UBU attempt 3
fallback 3
root (hd3,0)
/boot/vmlinuz-2.6.10-5-386.acpi root=/dev/hde5 ro quiet splash
/boot/initrd.img-2.6.10-5-386.acpi
savedefault
boot
savedefault --wait=2

title base grub chainloaderrrrrrrr
fallback 6
root (hd3,0)
chainloader +1
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)



================================ sda1/menu.lst: ================================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default


title Boot from hard disk 3 image
#   map (hd3,0)/aa.dsk (hd3)
   map (hd3) (hd3)
   map --hook
   chainloader (hd3,0)+1
   rootnoverify (h3,0)
savedefault --wait=2

title find and load grub2
find --set-root /boot/grub/core.img
kernel /boot/grub/core.img
boot
savedefault --wait=2

title UBuntu attempt 1
fallback 3
root (hd3,0) ##(remember, this is Grub 1 Notation = /dev/sda7)
kernel /boot/grub/core.img
boot
savedefault --wait=2

title UBuntu attempt 2
fallback 4
root (hd3,4)
kernel /casper/vmlinuz root=/dev/sde5 ro 
initrd /casper/initrd.lz
boot
savedefault --wait=2

title UBU attempt 3
fallback 3
root (hd3,0)
/boot/vmlinuz-2.6.10-5-386.acpi root=/dev/hde5 ro quiet splash
/boot/initrd.img-2.6.10-5-386.acpi
savedefault
boot
savedefault --wait=2

title base grub chainloaderrrrrrrr
fallback 6
root (hd3,0)
chainloader +1
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)



================================ sda1/boot.ini: ================================

[boot loader] 
timeout=4 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
C:\grldr="Grub 4 Dos" 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: menu.lst

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=7
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png ; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/09_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ecc2741cc26f337
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sde6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
    linux /boot/vmlinuz-2.6.32-5-686 root=UUID=bd312c42-22f1-41a7-815b-ff49d970bc52 ro quiet
    initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sde6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
    linux /boot/vmlinuz-2.6.32-5-686 root=UUID=bd312c42-22f1-41a7-815b-ff49d970bc52 ro single
    initrd /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/09_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=54dc02da-1408-440d-8017-d93a744fda1f ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 54dc02da-1408-440d-8017-d93a744fda1f
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=54dc02da-1408-440d-8017-d93a744fda1f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
##UUID=39dce7bc-28c6-4d48-a3e1-b2d48712856e /               ext3    errors=remount-ro 0       1
UUID=54dc02da-1408-440d-8017-d93a744fda1f /               ext4    errors=remount-ro 0       1


# swap was on /dev/sda5 during installation should be sda2
#UUID=f5355ad1-6de9-497b-a8d4-e2abe7336d4d none            swap   
UUID=fa0ac7e1-6154-4e96-afc7-37865af56e71 none            swap   
 sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda3    /    ext4    rw,errors=remount-ro    0    0
/dev/sdb1    /media/hdd ntfs  iocharset=utf8,umask=000  0    0

=================== sda3: Location of files loaded by Grub: ===================


  35.1GB: boot/grub/core.img
  37.6GB: boot/grub/grub.cfg
  30.9GB: boot/initrd.img-2.6.32-5-686
  35.1GB: boot/vmlinuz-2.6.32-5-686
  30.9GB: initrd.img
  35.1GB: vmlinuz

=========================== sde5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
if terminal_output gfxterm ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal gfxterm
fi
insmod part_msdos
insmod ext2
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=bd312c42-22f1-41a7-815b-ff49d970bc52 ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set bd312c42-22f1-41a7-815b-ff49d970bc52
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=bd312c42-22f1-41a7-815b-ff49d970bc52 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ecc2741cc26f337
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 01c38b5c54257960
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux Mint Debian Edition (1) (on /dev/sdd5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 430ef5ec-e514-4a55-a74f-6773b102301f
    linux /boot/vmlinuz-2.6.32-5-686 root=/dev/sdd5
    initrd /boot/initrd.img-2.6.32-5-686
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation

##UUID=39dce7bc-28c6-4d48-a3e1-b2d48712856e /               ext3   
#sde6 is  bd312c42-22f1-41a7-815b-ff49d970bc52
#sda1: LABEL="=you" UUID="3ECC2741CC26F337
# sda3
UUID=54dc02da-1408-440d-8017-d93a744fda1f /               ext4   

errors=remount-ro 0       1


# swap was on /dev/sda5 during installation
UUID=f5355ad1-6de9-497b-a8d4-e2abe7336d4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sdd6    /    ext4    rw,errors=remount-ro    0    0

=================== sde5: Location of files loaded by Grub: ===================


 474.5GB: boot/grub/grub.cfg
 470.2GB: boot/initrd.img-2.6.32-5-686
 474.5GB: boot/vmlinuz-2.6.32-5-686
 470.2GB: initrd.img
 474.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde2

00000000  2e a4 7a ea e5 e0 0f fa  82 46 d4 20 0c 3f 11 b6  |..z......F. .?..|
00000010  b3 1c 81 03 65 c0 19 bb  5c 56 f6 36 93 47 73 0b  |....e...\V.6.Gs.|
00000020  ff f3 38 c4 20 19 09 fe  c1 9e 48 4d 80 b4 18 01  |..8. .....HM....|
00000030  04 89 8a d4 65 79 ee e7  aa 5d b9 7a bd c5 db ac  |....ey...].z....|
00000040  9c 27 a9 a3 a8 1b 37 1d  7d b4 33 77 97 30 21 0e  |.'....7.}.3w.0!.|
00000050  62 1d f4 c4 2c a2 19 fb  10 92 80 08 5b 00 d6 10  |b...,.......[...|
00000060  eb 10 85 c2 64 0f 84 47  5a e5 00 2c 40 75 b9 99  |....d..GZ..,@u..|
00000070  16 aa 0e dc 92 72 ff af  a0 00 a5 6e 15 16 ce 53  |.....r.....n...S|
00000080  ac ba c2 08 a5 0d 40 d3  4d 15 7b a3 ff f3 28 c4  |......@.M.{...(.|
00000090  1a 13 a1 c6 e2 5e 02 d0  09 2a 0a 8f 43 c1 50 5c  |.....^...*..C.P\|
000000a0  34 02 e7 5b 24 2c 29 ce  a8 d3 15 77 53 12 41 b2  |4..[$,)....wS.A.|
000000b0  79 8a a6 df 1f ff d5 a4  0d 29 25 1e fa bb 86 2c  |y........)%....,|
000000c0  d7 30 7d 94 68 a8 a8 94  59 c1 c4 a1 e8 aa 15 dd  |.0}.h...Y.......|
000000d0  25 ae 49 77 ff f3 28 c4  06 0e 39 4a e2 58 01 86  |%.Iw..(...9J.X..|
000000e0  05 39 5b c0 6f b0 6c 95  08 18 a8 d5 59 8e 29 74  |.9[.o.l.....Y.)t|
000000f0  bf fe a9 55 aa 70 be 4f  bf 0c fd fd 93 8c 21 1c  |...U.p.O......!.|
00000100  04 0c 59 89 03 33 17 68  76 66 61 4e 14 e0 b1 5f  |..Y..3.hvfaN..._|
00000110  f9 79 cc 2d 07 67 23 24  07 b8 00 6c ff f3 28 c4  |.y.-.g#$...l..(.|
00000120  08 0e b9 9a c5 be 03 04  15 53 71 4a 37 ea c4 5b  |.........SqJ7..[|
00000130  72 99 e7 63 57 f5 0d d5  b2 b6 fc bc ad d7 76 3e  |r..cW.........v>|
00000140  7f cd a1 b4 14 69 48 fa  3c ac 95 6d dd a6 3e e8  |.....iH.<..m..>.|
00000150  2c fc 47 c5 24 72 7f df  68 b7 e0 00 c0 15 bb ff  |,.G.$r..h.......|
00000160  80 a8 56 08 ff f3 28 c4  08 10 88 46 c0 5e 00 86  |..V...(....F.^..|
00000170  00 ec ea 7b 09 13 01 1e  ff fd 44 cc a0 0a 76 1d  |...{......D...v.|
00000180  09 2c 42 22 63 96 48 b0  2a 19 15 18 b0 d4 44 05  |.,B"c.H.*.....D.|
00000190  c3 82 23 c0 d0 71 f0 d7  2c 14 4d 4d b9 6d d4 09  |..#..q..,.MM.m..|
000001a0  9f ac a4 58 e1 03 e7 37  67 ea 0c 55 ff f3 48 c4  |...X...7g..U..H.|
000001b0  00 1b a3 a6 c9 5e 09 53  a8 06 00 26 bb ff 00 fe  |.....^.S...&....|
000001c0  ff ff 83 fe ff ff 02 08  00 00 00 00 7e 03 00 00  |............~...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by Quackers on 2010-12-29
Wow. 
In sda1 you have 2 of XP's boot files, the menu.list file from Grub Legacy and grldr, which I think is from wubi.
In sda3 you have grub2 installed (should be in the mbr of sda) and Linux Mint with its correct boot files.
sdb1 is not being recognised and could have anything in it.
sdc1 has Windows XP, but none of its boot files.
sde5 has Linux Mint and all of its boot files.

Can you please explain what exactly is booting and what exactly you want to delete please? Thanks :-)

---

### Post by degarb on 2010-12-29
> **Quackers said:**
> Wow. 
In sda1 you have 2 of XP's boot files, the menu.list file from Grub Legacy and grldr, which I think is from wubi.
In sda3 you have grub2 installed (should be in the mbr of sda) and Linux Mint with its correct boot files.
sdb1 is not being recognised and could have anything in it.
sdc1 has Windows XP, but none of its boot files.
sde5 has Linux Mint and all of its boot files.

Can you please explain what exactly is booting and what exactly you want to delete please? Thanks :-)


Close,  I tried grub4dos, but not supported by any useful forum, and gave up.  (I just deleted the boot.ini reference to it.)

Sda has xp
sda2 swap
sda3 mint (seems to boot fine. It installed grub there?  I don't recall code to force it to a particular partion, just drive.  No need to move? )

sdb and sdc are just storage, but used to have xp in the poast.
sde had ubuntu, then attempted Mint with a smoother install and no crash like ubuntu, however I cannot get it to boot.  I feel it is a bios or some advanced issue relating to phyiscal disk structure.

I just want the sde linux either to work (which is outside this thread) or not in grub2 menu.

thnks

---

### Post by Quackers on 2010-12-30
Mint in sde is not booting because Grub is looking for the boot files in partition 3, whereas those boot files are in partition 5. However one of its boot files is missing.
If you wanted to fix that you would need to boot from a live cd and then follow the chroot method in the guide by drs305 to purge and re-install grub to the mbr of sde, by first mounting sde5.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you want to delete those partitions you should first delete sde5, then sde2, as sde2 is an extended partition.

---

