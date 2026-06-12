---
title: "Misplaced GRUB, Dual-boot fails, Windows wont load."
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by donSchoe on 2011-02-12
Hello,

I have Windows 7 (x64) on my machine and installed Ubuntu 10.10 Desktop edition using a live CD.

My disk looks like this:

```
/dev/sda1 NTFS Windows 7 system partition  (~100MB)
/dev/sda2 NTFS Windows 7 main partition    (~100GB)
/dev/sda3 SWAP                             (~  4GB)
/dev/sda4 EXT4 Ubuntu 10.10 main partition (~ 50GB)
```After  installing Ubuntu 10.10 using the live CD I can still select Windows 7  in GRUB menu but after selecting it, it wont boot and I'll get back to  the GRUB menu after a few seconds.

I think I've accidently placed the GRUB loader at the Windows 7 loader location.

I've run the boot script which I've found in various threads, here are my results.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 543338 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 280373920 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,802,047   204,595,200   7 HPFS/NTFS
/dev/sda3         204,802,048   212,971,519     8,169,472  82 Linux swap / Solaris
/dev/sda4         212,971,520   312,580,095    99,608,576  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
222 heads, 30 sectors/track, 146662 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FA706AB6706A7971                       ntfs       System-reserviert             
/dev/sda2        DED87704D876D9EB                       ntfs                                     
/dev/sda3        c465b75c-b0ef-492d-9437-d7097c834bfb   swap                                     
/dev/sda4        bbe1fbaf-f46c-47af-abca-e8f21bde9b45   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FC36BADE36BA995A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3E785D97785D4EB1                       ntfs       Afri 931GB                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/UDF Volume        udf         (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdc1        /media/Afri 931GB        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa706ab6706a7971
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 143.5GB: boot/grub/core.img
 139.3GB: boot/grub/grub.cfg
 139.8GB: boot/initrd.img-2.6.35-25-generic-pae
 143.5GB: boot/vmlinuz-2.6.35-25-generic-pae
 139.8GB: initrd.img
 143.5GB: vmlinuz
```I just tried spending some time to understand the log above:
 
 ```
sda2: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
 [COLOR=Red]    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr[/COLOR]
 
```[COLOR=Red]
[COLOR=Black]This looks like I screwed up something. How should  it look like? How can I fix this? Note: I had a WUBI (Ubuntu inside  Windows) installation first but removed it and installed a "real"  Ubuntu. Not sure why it points to a WUBI directory....[/COLOR][/COLOR]

I've tried using the Windows 7 recovery disk but it just tells me "Everything is fine with your system."

Any help is appreciated.
Thanks :smile:[COLOR=Red]
[/COLOR]

---

### Post by oldfred on 2011-02-12
Win7 has a hidden (in windows) 100MB boot partition. That is the one that boots as windows boots from the MBR to the partition with the boot flag.

But windows NTFS partitions have to have a NTFS type partition boot sector. You installed grub to sda1 and that is the problem. Windows fixboot also should have worked.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Does booting from sdc the 1000GB work? The boot script or grub do not identify same drive correctly and since it says partition 4, it must be booting sda.

---

### Post by donSchoe on 2011-02-12
thanks oldfred, this was exactly what i was looking for.
it's working now... :popcorn:

---

