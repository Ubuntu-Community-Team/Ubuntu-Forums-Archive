---
title: "Flashing cursor on first boot"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dunge on 2010-03-06
I just downloaded Ubuntu 10.04 Lucid Lynx x64 Alpha 3 live cd. I booted on the disk and tried the live cd option. Ubuntu seems to work fine. I reboot and selected install Ubuntu. The first time, at the "select documents and settings to import" I just checked something, then unchecked it and pressed next. At 83% of the installation in "importing documents in settings", it just froze there. I waited 15min and forced a reboot. I tried again, this time without touching any checkbox and it finally installed successfully and rebooted by itself at the end.

With my BIOS, I can decide which HDD to boot from, so I select the one I just installated Ubuntu on, and imediately I see a flashing cursor in the top left of the screen and it just stop there. No grub, no Ubuntu logo, no disk activity, nothing. I tried to boot back in the live cd, check the disk utility, checked my partition flags and "bootable" was unchecked, so I checked it, rebooted, same thing. Any idea? Would 9.10 react better?

---

### Post by sikander3786 on 2010-03-06
> **Dunge said:**
> I just downloaded Ubuntu 10.04 Lucid Lynx x64 Alpha 3 live cd. I booted on the disk and tried the live cd option. Ubuntu seems to work fine. I reboot and selected install Ubuntu. The first time, at the "select documents and settings to import" I just checked something, then unchecked it and pressed next. At 83% of the installation in "importing documents in settings", it just froze there. I waited 15min and forced a reboot. I tried again, this time without touching any checkbox and it finally installed successfully and rebooted by itself at the end.

With my BIOS, I can decide which HDD to boot from, so I select the one I just installated Ubuntu on, and imediately I see a flashing cursor in the top left of the screen and it just stop there. No grub, no Ubuntu logo, no disk activity, nothing. I tried to boot back in the live cd, check the disk utility, checked my partition flags and "bootable" was unchecked, so I checked it, rebooted, same thing. Any idea? Would 9.10 react better?

Don't know exactly what the problem is. Is GRUB installed? If even GRUB doesn't show up I think the problem is with GRUB.

Surely Ubuntu 9.10 will react a lot better than that. 10.04 is still in Alpha state. It is meant for testing only not for use on Productivity Machines.

---

### Post by Dunge on 2010-03-06
I don't know if GRUB is installed, is it supposed to get installed with a default installation?

I just grabbed the latest version because I though since it allow updating to it from 9.10, why don't I just install it directly? Will save some bandwidth and I'll have the latest versions of all applications. I could download 9.10, (another 700mb), burn another CD and try again with it, but I'm afraid it will probably do the same thing.

---

### Post by presence1960 on 2010-03-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Dunge on 2010-03-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdf: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdf has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdd2             206,848   293,044,223   292,837,376   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        98c571a3-53d9-43fa-9f3a-b6345aa35af5   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        481412aa-bdbc-4371-b203-a31542d54686   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        64E86A07E869D7B6                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        7EBA3C48BA3BFAEB                       ntfs       System Reserved               
/dev/sdd2        D89A3FFD9A3FD6AA                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde         6CBB-1E22                              vfat                                     
/dev/sdf         3E68-C5E2                              vfat       Mitsubishi                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro,relatime)
/dev/sdd2        /media/D89A3FFD9A3FD6AA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0000000000000000
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 0000000000000000 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0000000000000000
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 0000000000000000 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 64e86a07e869d7b6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
    insmod ntfs
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 7eba3c48ba3bfaeb
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
UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=481412aa-bdbc-4371-b203-a31542d54686 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  60.2GB: boot/grub/grub.cfg
   4.4GB: boot/initrd.img-2.6.32-14-generic
   4.4GB: boot/vmlinuz-2.6.32-14-generic
   4.4GB: initrd.img
   4.4GB: vmlinuz

=========================== sde/boot/grub/menu.lst: ===========================

default 0
timeout 30

title     Default settings (Runs from RAM / USB usable)\n * Parted Magic version: 4.8, (C) 2010, Patrick Verner\n * http://www.partedmagic.com\n * Disclaimer: Author excluded from any liability.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Live with default settings (media not usable)\n Live mode intended for 128-192MB based systems.\n The Live CD medium must remain in the drive.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 vga=791 livemedia noeject max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Live with low RAM settings\n Disables most daemons and other RAM-exhausting\n processes. The preferred Live option for systems\n with minimal memory (128MB of RAM).
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal lowram livemedia noeject nogpm nolvm nonfs nofstabdaemon nosmart noacpid nodmeventd nohal nosshd nosound nobluetooth loglevel=0 xvesa max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Do not eject CD (*emulators)\n Same as option 2 except for the noreplace-paravirt\n parameter, which is needed for some emulators.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 noeject noreplace-paravirt livemedia loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Alternate graphical server\n Same as option 1. except Xvesa is used by default\n instead of Xorg. (Try this option if Xorg fails.)
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 xvesa loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Safe Graphics settings (vga=normal)\n Disables splash screen and console frame buffer support.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Failsafe settings\n vga=normal,, noapic, nolapic, nopcmcia, noscsi,\n nogpm, nosmart, & boots to console.
kernel /pmagic/bzImage edd=off acpi=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal nolapic nopcmcia noscsi nogpm consoleboot nosmart keymap=us nosshd nosound max_loop=256
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Console (Boots to the shell)\n Normal vga, verbose kernel messages, and\n no automatic graphical environment.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal consoleboot max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Help\n Displays help texts.
terminal console
cat /boot/syslinux/message.txt
pause
clear
cat /boot/syslinux/message2.txt
pause
clear
cat /boot/syslinux/message3.txt
pause
clear
cat /boot/syslinux/message4.txt
pause
clear
cat /boot/syslinux/message5.txt
configfile /boot/grub/grub4dos.lst

title     Local boot\n Boot from your first hard disk.
rootnoverify (hd0)
chainloader +1

title     Reboot\n Restart the computer.
reboot

title     Memtest86+\n Check system RAM for errors.
kernel /boot/syslinux/memtest
map --unmap=0:0xff

title Super Grub Disk 1\nEasily restore the grub bootloader.
map --mem /boot/sgd/sgd.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

title Super Grub Disk 2\nEasily restore the grub bootloader.
map --mem /boot/sgd/sgd2.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

title Hardware Detection Tool (HDT)\nAn interactive hardware analyzer by Erwan Velu.
map --mem /boot/syslinux/hdt.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

==================== sde: Location of files loaded by Grub: ====================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2


```

I guess I just need to register grub to the partition or something?!

---

### Post by overdrank on 2010-03-06
Moved to Lucid Lynx Testing and Discussion

---

### Post by presence1960 on 2010-03-06
> **Dunge said:**
> ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdf: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdf has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdd2             206,848   293,044,223   292,837,376   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        98c571a3-53d9-43fa-9f3a-b6345aa35af5   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        481412aa-bdbc-4371-b203-a31542d54686   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        64E86A07E869D7B6                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        7EBA3C48BA3BFAEB                       ntfs       System Reserved               
/dev/sdd2        D89A3FFD9A3FD6AA                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde         6CBB-1E22                              vfat                                     
/dev/sdf         3E68-C5E2                              vfat       Mitsubishi                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro,relatime)
/dev/sdd2        /media/D89A3FFD9A3FD6AA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 98c571a3-53d9-43fa-9f3a-b6345aa35af5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0000000000000000
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 0000000000000000 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0000000000000000
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 0000000000000000 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 64e86a07e869d7b6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
    insmod ntfs
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 7eba3c48ba3bfaeb
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
UUID=98c571a3-53d9-43fa-9f3a-b6345aa35af5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=481412aa-bdbc-4371-b203-a31542d54686 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  60.2GB: boot/grub/grub.cfg
   4.4GB: boot/initrd.img-2.6.32-14-generic
   4.4GB: boot/vmlinuz-2.6.32-14-generic
   4.4GB: initrd.img
   4.4GB: vmlinuz

=========================== sde/boot/grub/menu.lst: ===========================

default 0
timeout 30

title     Default settings (Runs from RAM / USB usable)\n * Parted Magic version: 4.8, (C) 2010, Patrick Verner\n * http://www.partedmagic.com\n * Disclaimer: Author excluded from any liability.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Live with default settings (media not usable)\n Live mode intended for 128-192MB based systems.\n The Live CD medium must remain in the drive.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 vga=791 livemedia noeject max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Live with low RAM settings\n Disables most daemons and other RAM-exhausting\n processes. The preferred Live option for systems\n with minimal memory (128MB of RAM).
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal lowram livemedia noeject nogpm nolvm nonfs nofstabdaemon nosmart noacpid nodmeventd nohal nosshd nosound nobluetooth loglevel=0 xvesa max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Do not eject CD (*emulators)\n Same as option 2 except for the noreplace-paravirt\n parameter, which is needed for some emulators.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 noeject noreplace-paravirt livemedia loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Alternate graphical server\n Same as option 1. except Xvesa is used by default\n instead of Xorg. (Try this option if Xorg fails.)
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 xvesa loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Safe Graphics settings (vga=normal)\n Disables splash screen and console frame buffer support.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=0 max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Failsafe settings\n vga=normal,, noapic, nolapic, nopcmcia, noscsi,\n nogpm, nosmart, & boots to console.
kernel /pmagic/bzImage edd=off acpi=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal nolapic nopcmcia noscsi nogpm consoleboot nosmart keymap=us nosshd nosound max_loop=256
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Console (Boots to the shell)\n Normal vga, verbose kernel messages, and\n no automatic graphical environment.
kernel /pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal consoleboot max_loop=256 keymap=us
initrd /pmagic/initramfs
map --unmap=0:0xff

title     Help\n Displays help texts.
terminal console
cat /boot/syslinux/message.txt
pause
clear
cat /boot/syslinux/message2.txt
pause
clear
cat /boot/syslinux/message3.txt
pause
clear
cat /boot/syslinux/message4.txt
pause
clear
cat /boot/syslinux/message5.txt
configfile /boot/grub/grub4dos.lst

title     Local boot\n Boot from your first hard disk.
rootnoverify (hd0)
chainloader +1

title     Reboot\n Restart the computer.
reboot

title     Memtest86+\n Check system RAM for errors.
kernel /boot/syslinux/memtest
map --unmap=0:0xff

title Super Grub Disk 1\nEasily restore the grub bootloader.
map --mem /boot/sgd/sgd.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

title Super Grub Disk 2\nEasily restore the grub bootloader.
map --mem /boot/sgd/sgd2.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

title Hardware Detection Tool (HDT)\nAn interactive hardware analyzer by Erwan Velu.
map --mem /boot/syslinux/hdt.gz (fd0)
map --hook
root (fd0)
chainloader (fd0)+1

==================== sde: Location of files loaded by Grub: ====================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2


```

I guess I just need to register grub to the partition or something?!

First you should realize that Lucid is in alpha stage and should not be used as your main OS. You may expect some breakage of packages or maybe even the whole system. It is for testing only.

But if you wish to continue do this: Boot the lucid Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```This will mount your ubuntu / partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB 2 on MBR of sdb.

Reboot without the CD and go into BIOS. Set sdb (80 GB) disk as first hard disk to boot in the hard disk boot order. Save changes to CMOS and continue booting. Choose Ubuntu from the GRUB menu. When the desktop loads open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```Hit enter at the windows until you reach the window where you can choose where to install GRUB. Use the arrow keys to maneuver and the space bar to select/deselect. make sure all disks except sdb are deselected. Make sure sdb is selected. Hit Tab to go to OK & then hit enter. This will insure any grub-pc updates go to sdb rather than your other disks. You should be good to go. If by chance your windows is not in the GRUB menu when you boot - boot into ubuntu and run in terminal ```
sudo update-grub
```

---

### Post by Dunge on 2010-03-07
Thanks for the guide. I wonder why the default installation don't handle that though. Of course it's alpha state, but installing the bootloader is not something you just forget to include when packaging the version.

---

### Post by the_one(2) on 2010-03-07
My guess is that grub was installed to the wrong drive (sda maybe?) and was then erased or something?

---

### Post by presence1960 on 2010-03-07
> **the_one(2) said:**
> My guess is that grub was installed to the wrong drive (sda maybe?) and was then erased or something?

Don't guess- if you look at the very top of the boot info script results the OP posted you will see that GRUB is not installed either on MBR of his disks nor to a partition. And you will see a lot more info about his setup & boot process. Learn to use the boot info script by running it on your machine and studying it's output so you can help rather than guess when people have boot problems.

---

