---
title: "Multi HDD dual boot, Vista + Lucid Lynx... GRUB probs"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by MrShades on 2010-04-27
I've got a machine that I'd got 9.10 on, that I've now upgraded to Lucid Lynx - and I'm having the same problem with dual boot (or lack thereof) that I was having previously.

Rough scenario is:

(Original Vista machine had)

C: Windows Vista OS + Windows software, etc.: 500GB - single NTFS partition -  SATA drive

D: General dumping ground for data. 500GB SATA drive. Was single NTFS partition, now shrunk to install Ubuntu. So is now:
    - NTFS partition (containing general rubbish)
    - Ubuntu / partition
    - Ubuntu swap partition

... and then 3 x 1TB SATA drives making up an (Intel ICH9R) FakeRaid RAID5 array - that Windows can happily 'see' and use, but I don't care about Ubuntu having access to it or even seeing it.

Lucid Lynx is installed to /dev/sde6 (IIRC) - but when I boot the machine just boots straight into Vista.

I've done what I can to try and get GRUB correctly installed - to the point that right now I probably have it splattered just about anywhere and everywhere.

So - now - the machine boots and simply presents me with "GRUB Hard Disk Error" and stops...

I can fix this by running the Vista repair, with a fixmbr etc. and putting the MBR back to 'normal' on the first boot disk (/dev/sdd in this case). The machine then just boots straight into Vista.

...or I can boot into Ubuntu (or Vista) by booting off a Super Grub Disk (CD) and selecting "Boot Linux" (or whatever it is) - and it correctly boots Lucid Lynx from /dev/sde6

Ideally I want a proper GRUB dual boot menu - but I just seem to be getting into more and more of a mess!

So - HELP! Please....

Hopefully the bootlog below will show what sort of mess I'm in:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 898063412 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sde and looks for 
    (UUID=92bec2b3-83bc-4e0c-b581-952c8223a794)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #5 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/mapper/isw_cghdjbcid_Volume0 and 
    looks at sector 898063412 of the same hard drive for core.img, core.img is 
    at this location on /dev/sde and looks for 
    (UUID=92bec2b3-83bc-4e0c-b581-952c8223a794)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

isw_cghdjbcid_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cghdjbcid_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34       262,177       262,144 Microsoft Windows
/dev/sda2         264,192 3,907,033,087 3,906,768,896 Linux or Data

/dev/sda2 ends after the last sector of /dev/sda
Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   976,771,055   976,769,008   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   872,785,911   872,783,864   6 FAT16
/dev/sde2         872,795,385   976,768,064   103,972,680   5 Extended
/dev/sde5         872,795,448   892,780,244    19,984,797  82 Linux swap / Solaris
/dev/sde6    *    892,780,308   976,768,064    83,987,757  83 Linux


Drive: isw_cghdjbcid_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_cghdjbcid_Volume0: 2000.4 GB, 2000402251776 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907035648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cghdjbcid_Volume01   *              1 4,294,967,295 4,294,967,295  ee GPT

/dev/mapper/isw_cghdjbcid_Volume01 ends after the last sector of /dev/mapper/isw_cghdjbcid_Volume0

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_cghdjbcid_Volume01             34       262,177       262,144 Microsoft Windows
/dev/mapper/isw_cghdjbcid_Volume02        264,192 3,907,033,087 3,906,768,896 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_cghdjbcid_Volume0: PTTYPE="gpt" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        5698CEB398CE90C3                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        BEA8012DA800E5AD                       ntfs       Data                          
/dev/sde2: PTTYPE="dos" 
/dev/sde5        7c3445af-62f9-4185-9821-f5df7365ef37   swap                                     
/dev/sde6        92bec2b3-83bc-4e0c-b581-952c8223a794   ext4                                     
/dev/sde: PTTYPE="dos" 
error: /dev/mapper/isw_cghdjbcid_Volume01: No such file or directory
error: /dev/mapper/isw_cghdjbcid_Volume02: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cghdjbcid_Volume0

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde6        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=shades)


=========================== sde6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=92bec2b3-83bc-4e0c-b581-952c8223a794

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        92bec2b3-83bc-4e0c-b581-952c8223a794
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sde6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd4,6)
search --no-floppy --fs-uuid --set 92bec2b3-83bc-4e0c-b581-952c8223a794
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd4,6)
    search --no-floppy --fs-uuid --set 92bec2b3-83bc-4e0c-b581-952c8223a794
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd4,6)
    search --no-floppy --fs-uuid --set 92bec2b3-83bc-4e0c-b581-952c8223a794
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdd1)" {
    insmod ntfs
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 5698ceb398ce90c3
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde6 during installation
UUID=92bec2b3-83bc-4e0c-b581-952c8223a794 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=7c3445af-62f9-4185-9821-f5df7365ef37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sde6: Location of files loaded by Grub: ===================


 459.8GB: boot/grub/core.img
 459.8GB: boot/grub/grub.cfg
 458.2GB: boot/grub/menu.lst
 457.6GB: boot/grub/stage2
 458.1GB: boot/initrd.img-2.6.31-14-generic
 462.3GB: boot/initrd.img-2.6.32-21-generic
 459.5GB: boot/vmlinuz-2.6.31-14-generic
 458.8GB: boot/vmlinuz-2.6.32-21-generic
 462.3GB: initrd.img
 458.1GB: initrd.img.old
 458.8GB: vmlinuz
 459.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on isw_cghdjbcid_Volume01


Unknown BootLoader  on isw_cghdjbcid_Volume02



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/mapper/isw_cghdjbcid_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cghdjbcid_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cghdjbcid_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cghdjbcid_Volume02: No such file or directory


```Any and all help very much appreciated...

Thanks

Shades

---

### Post by oldfred on 2010-04-27
I see two boot flags but linux does not use them only windows and some BIOS (that think the only boot windows). Boot flag should only be on primary partition.

I would install grub to sde and set BIOS to boot sde. Leave windows installed where it works and if you ever need to boot it directly you will be able to. I am not sure if grub will automatically find the windows install if it is inside the raid, but others have made it work. I do not have raid but did help a couple of others and they managed to get it to work.

If your supergrub gets you into your system you can reinstall grub from working system.

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

If it complains about a device map (since you have do many drives you may want to check this anyway. /boot/grub/device.map
sudo grub-mkdevicemap
sudo update-grub

I have also seen where some have to run this to make sure grub reinstalls to the correct drive.
sudo dpkg-reconfigure grub-pc

---

### Post by MrShades on 2010-04-28
Thanks very much for that.

I've cleaned up various boot flags, etc. but I think the KEY part of your help was in installing grub on /dev/sde and setting the BIOS to boot from that drive first.

Doing this means that the BIOS sees the drive OK, and starts up GRUB - which then gives me the various Ubuntu boot options. But no option to boot Vista as it doesn't know about it... yet.

Adding an option into menu.lst to boot Vista (once I'd deduced which drive it thought it was - hd1,0) and we're all running very happily.

By default I now have it booting directly (via hidden grub) into Vista - and if I want Ubuntu I 'catch' the grub screen, hit Esc and boot into Ubuntu through the grub menu.

All very nice - and working very well... Thanks again.

Shades

---

