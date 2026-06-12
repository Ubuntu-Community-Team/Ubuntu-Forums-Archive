---
title: "grub2 is confusing me"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by poljpocket on 2011-02-15
Hey all the experts,

I'm an computer scientist and I am using several computers with a dual boot system. Mainly I use Ubuntu 10.10 these days and i have to keep Windows 7 for some project specific things that won't work in Linux.

Today, I ran into a confusing problem.

At home, I have 2 computers. One desktop and one netbook.

The desktop uses Windows 7 Professional x64 and Ubuntu 10.10 Desktop x64. On this one, I don't got any problems. This computer has a RAID0 installed with 2 harddrives. This was also no problem for Ubuntu to recognize and work properly. I installed grub2 on the /dev/sda1 partition, which is the Windows 7 Loader partition (100MB of size). It works perfectly for both systems. Directly installing grub2 on /dev/sda failed and screwed up my whole MBR and I had to repair it with some foolish Windows command line.

Today I tried the same with the netbook, which is running Windows 7 Starter x86 and Ubuntu 10.10 Netbook x86. Windows 7 is installed cleanly from a USB disk which is a copy of an original Windows 7 disc I own. I did everything the exact same way, meaning installed the grub2 on the /dev/sda1 partition, which is again the Windows 7 Loader and again 100MB of size.

But somehow, this doesn't work, because Windows won't boot anymore. The screens just pops back to the grub2 menu after about 2 seconds. I ran into a forum post here stating that you souldn't install grub2 on the boot partition of Windows but install it directly to the /dev/sda.

I'm now looking for a way to fix this, but that's not the point now.

My question is now, why is there a difference? Why does /dev/sda1 work on the desktop but not on the netbook and /dev/sda works on the netbook but not on the desktop?

My first intention was the RAID0 could cause this?!?

Thanks in advance, polj

---

### Post by oldfred on 2011-02-15
To really know how things are configured, you would have to run this on both computers:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by poljpocket on 2011-02-16
Hello and thank you for the advice,

I ran this script on my Netbook, the one for the Desktop is following soon:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 477268520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   258,756,607   258,549,760   7 HPFS/NTFS
/dev/sda3         258,756,608   482,531,998   223,775,391  83 Linux
/dev/sda4         482,533,374   488,394,751     5,861,378   5 Extended
/dev/sda5         482,533,376   488,394,751     5,861,376  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F8164037163FF4EA                       ntfs       System Reserved               
/dev/sda2        10FC4871FC485360                       ntfs       Windows                       
/dev/sda3        9b46e6f8-d4f7-4fb2-8159-05d4a3faf0d9   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7f13c75c-86eb-4443-8208-c03ca0b3d6dd   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=600)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="1"
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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9b46e6f8-d4f7-4fb2-8159-05d4a3faf0d9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9b46e6f8-d4f7-4fb2-8159-05d4a3faf0d9
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 9b46e6f8-d4f7-4fb2-8159-05d4a3faf0d9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9b46e6f8-d4f7-4fb2-8159-05d4a3faf0d9 ro  splash vga=771  quiet splash acpi_backlight=vendor
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f8164037163ff4ea
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7f13c75c-86eb-4443-8208-c03ca0b3d6dd none            swap    sw              0       0
/dev/sda3 / ext4 errors=remount-ro,user_xattr 0 1

=================== sda3: Location of files loaded by Grub: ===================


 244.3GB: boot/grub/core.img
 167.2GB: boot/grub/grub.cfg
 133.5GB: boot/initrd.img-2.6.35-22-generic
 133.4GB: boot/vmlinuz-2.6.35-22-generic
 133.5GB: initrd.img
 133.4GB: vmlinuz

```I can see here clearly, that the MBR here is on /dev/sda and that grub2 belongs there too. So that would definitely solve my problem of Windows not starting anymore.

Thanks for looking at it!

---

### Post by poljpocket on 2011-02-16
And here is the one from my Desktop:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/isw_eiibchca_Volume0 and 
    looks on the same drive in partition #3 for (,msdos3)/boot/grub.

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

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_eiibchca_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_eiibchca_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_eiibchca_Volume03: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_eiibchca_Volume04: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_eiibchca_Volume05: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,740,539,903 1,740,333,056   7 HPFS/NTFS
/dev/sda3       1,740,539,904 1,945,339,903   204,800,000  83 Linux
/dev/sda4       1,945,341,950 1,953,533,951     8,192,002   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ? 1,945,341,950 1,945,341,949                   Unknown
/dev/sda6     ? 1,945,341,950 1,945,341,949                   Unknown

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4

Drive: isw_eiibchca_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_eiibchca_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_eiibchca_Volume01   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_eiibchca_Volume02            206,848 1,740,539,903 1,740,333,056   7 HPFS/NTFS
/dev/mapper/isw_eiibchca_Volume03      1,740,539,904 1,945,339,903   204,800,000  83 Linux
/dev/mapper/isw_eiibchca_Volume04      1,945,341,950 1,953,533,951     8,192,002   f W95 Ext d (LBA)
/dev/mapper/isw_eiibchca_Volume05      1,945,341,952 1,953,533,951     8,192,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_eiibchca_Volume01 CA4286844286754B                       ntfs       System Reserved               
/dev/mapper/isw_eiibchca_Volume02 1298883B98881F7B                       ntfs       Windows                       
/dev/mapper/isw_eiibchca_Volume03 891c4004-2a82-4655-99fb-21329de6882c   ext4                                     
/dev/mapper/isw_eiibchca_Volume05 8e30661a-1a8b-41e6-8c69-6eec7f8d29ec   swap                                     
/dev/mapper/isw_eiibchca_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_eiibchca_Volume04: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_eiibchca_Volume0
isw_eiibchca_Volume01
isw_eiibchca_Volume02
isw_eiibchca_Volume03
isw_eiibchca_Volume05

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/isw_eiibchca_Volume03 /                        ext4       (rw,errors=remount-ro,commit=0)


================== isw_eiibchca_Volume03/boot/grub/grub.cfg: ==================

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
set default="3"
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
set root='(/dev/mapper/isw_eiibchca_Volume0,msdos3)'
search --no-floppy --fs-uuid --set 891c4004-2a82-4655-99fb-21329de6882c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_eiibchca_Volume0,msdos3)'
search --no-floppy --fs-uuid --set 891c4004-2a82-4655-99fb-21329de6882c
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_eiibchca_Volume0,msdos3)'
    search --no-floppy --fs-uuid --set 891c4004-2a82-4655-99fb-21329de6882c
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=891c4004-2a82-4655-99fb-21329de6882c ro  splash vga=773  
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_eiibchca_Volume0,msdos3)'
    search --no-floppy --fs-uuid --set 891c4004-2a82-4655-99fb-21329de6882c
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=891c4004-2a82-4655-99fb-21329de6882c ro  splash vga=773  
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_eiibchca_Volume0,msdos3)'
    search --no-floppy --fs-uuid --set 891c4004-2a82-4655-99fb-21329de6882c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=891c4004-2a82-4655-99fb-21329de6882c ro  splash vga=773  
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_eiibchca_Volume01)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_eiibchca_Volume0,msdos1)'
    search --no-floppy --fs-uuid --set ca4286844286754b
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

======================= isw_eiibchca_Volume03/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_eiibchca_Volume03 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_eiibchca_Volume05 none            swap    sw              0       0

=========== isw_eiibchca_Volume03: Location of files loaded by Grub: ===========


 932.1GB: boot/grub/core.img
 962.2GB: boot/grub/grub.cfg
 892.4GB: boot/initrd.img-2.6.35-22-generic
 962.4GB: boot/initrd.img-2.6.35-24-generic
 971.3GB: boot/initrd.img-2.6.35-25-generic
 932.1GB: boot/vmlinuz-2.6.35-22-generic
 932.0GB: boot/vmlinuz-2.6.35-24-generic
 932.1GB: boot/vmlinuz-2.6.35-25-generic
 971.3GB: initrd.img
 962.4GB: initrd.img.old
 932.1GB: vmlinuz
 932.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on isw_eiibchca_Volume04



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/isw_eiibchca_Volume04: No such file or directory
hexdump: /dev/mapper/isw_eiibchca_Volume04: No such file or directory

```I see, it's really different. This script searches for /dev/sd* but the RAID controller only gets /dev/mapper/volume* and grub2 is really installed on the MBR of the whole disk isw_eiibchca_Volume0 which I assume is the same as /dev/sda would be.

Thanks again!

---

### Post by oldfred on 2011-02-16
You did not install grub2 to the partition of your desktop but to the MBR. Not sure if you have not installed this on desktop which script  needs to parse RAID?

> #   Is able to search Linux Software Raid partitions (MD Raids) if
#       the "mdadm" package is installed.
#   If dmraid is installed, searches all raid drives, detected by dmraid.


Windows in NTFS partitions has to have a NTFS boot signature in the partition boot sector:

```
sda1: ________________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1 and [/COLOR]
                       looks at sector 477268520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD



```
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Your RAID does not look correct, but I do not know RAID

error: /dev/mapper/isw_eiibchca_Volume04:

---

