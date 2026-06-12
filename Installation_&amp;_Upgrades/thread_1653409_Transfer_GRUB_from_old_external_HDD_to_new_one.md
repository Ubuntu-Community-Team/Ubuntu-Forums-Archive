---
title: "Transfer GRUB from old external HDD to new one"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by kingsrook14 on 2010-12-26
Hello fellow ubuntu users and gurus,
 
I have a small issue. I would appreciate some help or pointers which will save somee time for me.
I have a laptop with dual boot Windowz 7 64 bit and Ubuntu 10.04 LTS 64 bit using windows MBR and EasyBCD. I have no issues booting into either.
I also have a 500 GB external HDD which has a NTFS partition for backup data and Linux root and swap partitions at the end. I have GRUB installed on the external HDD MBR and can boot into Ubuntu on the external HDD via bios options.
I recently bought a larger external HDD 1TB. Now so far I have made same partitions as old external HDD namely NTFS for bakup followed by Linux root and swap partitions. Linux partitions were cloned using disk cloning while on NTFS partition I only copied data.
MY QUESTION is HOW do I copy the GRUB from old external HDD to new one so that I can boot into my linux on the new external HDD ? 
BTW the new HDD is Western Digital Passport Essential SE, which also has some factory installed image at the start of drive.
Any help or advice is greatly appreciated.
 
Thanks a bunch for reading

---

### Post by presence1960 on 2010-12-26
You need to plug in the new external HD and install GRUB to the MBR of that new external HD. See[ here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") Use the simplest method by Booting from the Ubuntu Live CD/USB.

If you need more detailed instructions or are unsure do this with the new external plugged in:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by garvinrick4 on 2010-12-26
Drive has an mbr (master boot record) grub must be installed in: If you cloned a linux install 
into a partition and it is a good install you must put grub into mbr and have it look
in that install for the boot files. Can be done with a few lines of code. You are better off
giving post #2 the bootscript only takes a few seconds to make sure you have viable boot
files in the cloned Operating System.

---

### Post by kingsrook14 on 2010-12-27
Below is the RESULTS.txt file

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 629356544.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda6 and looks 
                       at sector 804540224 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 146. But according to the info from fdisk, 
                       sda8 starts at sector 859252736. According to the info 
                       in the boot sector, sda8 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782   7 HPFS/NTFS
/dev/sda2             208,901   629,354,495   629,145,595   7 HPFS/NTFS
/dev/sda3         629,354,496   976,768,064   347,413,569   f W95 Ext d (LBA)
/dev/sda5         629,356,544   791,091,199   161,734,656   7 HPFS/NTFS
/dev/sda6         791,093,249   850,720,767    59,627,519  83 Linux
/dev/sda7         850,722,138   859,252,589     8,530,452  82 Linux swap / Solaris
/dev/sda8         859,252,736   859,314,175        61,440   4 FAT16 <32M
/dev/sda9         859,316,224   976,766,975   117,450,752   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           7,616,512 1,892,012,031 1,884,395,520   7 HPFS/NTFS
/dev/sdb2       1,892,012,032 1,953,456,127    61,444,096   f W95 Ext d (LBA)
/dev/sdb5       1,892,014,080 1,949,544,447    57,530,368  83 Linux
/dev/sdb6       1,949,546,496 1,953,456,127     3,909,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C42E74F62E74E33A                       ntfs       System Reserved               
/dev/sda2        229887D69887A6BF                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda5        B0E24A234642384A                       ntfs       UserData                      
/dev/sda6        4ae355fd-304b-432f-bd5b-9de0e32e32e9   ext3                                     
/dev/sda7                                               swap                                     
/dev/sda8        C221-BB65                              vfat       HP_TOOLS                      
/dev/sda9        BC3012323011F45C                       ntfs       RecoveryArea                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08129CF6129CE9C8                       ntfs       WD_1TB                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb   ext3                                     
/dev/sdb6        91e99862-cf2b-4809-bee0-695da84d7884   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sdb5        /media/17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/Ubuntu 9.04 i386  iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/WD_1TB            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/menu.lst: ===========================

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
default         0

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
# kopt=root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4ae355fd-304b-432f-bd5b-9de0e32e32e9

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

title        Chainload into GRUB 2
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04.1 LTS, kernel 2.6.35-kingsrook
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35 root=/dev/sda5 ro quiet splash
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.35-kingsrook (recovery)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35 root=/dev/sda5 ro single

title        Ubuntu 10.04.1 LTS, kernel 2.6.34.2-candela
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.34.2-candela root=/dev/sda5 ro quiet splash
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.34.2-candela (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.34.2-candela root=/dev/sda5 ro single

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro quiet splash
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro quiet splash
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        4ae355fd-304b-432f-bd5b-9de0e32e32e9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
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
search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
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
menuentry 'Ubuntu, with Linux 2.6.35-candela' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux    /boot/vmlinuz-2.6.35-candela root=/dev/sda6 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-candela (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    echo    'Loading Linux 2.6.35-candela ...'
    linux    /boot/vmlinuz-2.6.35-candela root=/dev/sda6 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux    /boot/vmlinuz-2.6.34-020634-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.34-020634-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    echo    'Loading Linux 2.6.34-020634-generic ...'
    linux    /boot/vmlinuz-2.6.34-020634-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.34-020634-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4ae355fd-304b-432f-bd5b-9de0e32e32e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c42e74f62e74e33a
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
proc            /proc           proc    nodev,noexec,nosuid 0       0


UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9    /    ext4    errors=remount-ro    0    1
UUID=ddeda346-31b6-4e65-ac65-5656832794fa    none    swap    sw    0    0
UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9    /    ext3    errors=remount-ro    0    1
UUID=ddeda346-31b6-4e65-ac65-5656832794fa    none    swap    sw    0    0
UUID=4ae355fd-304b-432f-bd5b-9de0e32e32e9    /    ext3    errors=remount-ro    0    1
UUID=ddeda346-31b6-4e65-ac65-5656832794fa    none    swap    sw    0    0

=================== sda6: Location of files loaded by Grub: ===================


 412.0GB: boot/grub/core.img
 409.9GB: boot/grub/grub.cfg
 412.3GB: boot/grub/menu.lst
 409.9GB: boot/initrd.img-2.6.32-24-generic
 409.9GB: boot/initrd.img-2.6.32-26-generic
 412.3GB: boot/initrd.img-2.6.34-020634-generic
 418.7GB: boot/vmlinuz-2.6.32-24-generic
 418.7GB: boot/vmlinuz-2.6.32-26-generic
 411.9GB: boot/vmlinuz-2.6.34-020634-generic
 412.0GB: boot/vmlinuz-2.6.35-candela
 409.9GB: initrd.img
 412.3GB: initrd.img.old
 418.7GB: vmlinuz
 411.9GB: vmlinuz.old

=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=17a754dc-bf72-4d5f-a9d3-feb5cce9a9cb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=91e99862-cf2b-4809-bee0-695da84d7884 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 984.7GB: boot/grub/menu.lst
 984.6GB: boot/grub/stage2
 984.6GB: boot/initrd.img-2.6.28-11-generic
 984.7GB: boot/vmlinuz-2.6.28-11-generic
 984.6GB: initrd.img
 984.7GB: vmlinuz

```

---

### Post by kingsrook14 on 2010-12-27
As far as I understand 
  1.  if I boot from /dev/sda5 (my laptop install of Ubuntu) 
  2. then mount /dev/sdb5 (cloned linux partition on new external hdd) to a suitable /mnt/NewHDD point
  3.  run     [FONT=monospace][/FONT]sudo grub-install --root-directory=/mnt/NewHDD /dev/sdb
This will install GRUB on new HDD MBR ?
Then I can boot into new HDD GRUB and sudo update-grub to include /dev/sdb5 into grub menu and any kernel it finds on /dev/sdb5 ?  

Will this keep my laptop install and MBR untouched?
BTW I didn't use live cd but used laptop install of Ubuntu to run the boot info script

Thanks again
Ketan Rane

---

### Post by presence1960 on 2010-12-27
Your external disk ubuntu is Jaunty 9.04 with Legacy Grub. I am not sure but I believe the newer Ubuntu Live CDs do not support legacy grub. I would boot the Jaunty Live CD/USB with the external disk plugged in. Choose "Try ubuntu without any changes". When the desktop loads open a terminal and do this:


1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd1,4)", or whatever your hard disk + boot partition    numbers are for Ubuntu.
4. Type "setup (hd1)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Note: When you run #2 above it may say your legacy grub is located at hd(0,4). If that is the case then substitute "0" for the "1" in #3 & #4 above.

---

### Post by kingsrook14 on 2011-01-02
Hello everyone,
  Thanks for the help so far.
I did some changes to the orignal problem and would like some more help.
 
When I realized that the cloned partition on external HDD was Jaunty 9.04 with Legacy Grub I deleted it. 
Then I cloned the linux partition from my laptop HDD which is Ubuntu 10.04.1 LTS (/dev/sda6) onto my new external HDD.
I hope this removes the need for legacy Grub. I am going to do BOOT INFO SCRIPT again and post results here.
 
thanks

---

