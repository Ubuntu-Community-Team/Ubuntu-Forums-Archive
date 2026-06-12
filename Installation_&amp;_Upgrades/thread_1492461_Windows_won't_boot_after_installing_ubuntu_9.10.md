---
title: "Windows won't boot after installing ubuntu 9.10"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Trevor Burton on 2010-05-24
I had a perfect working dual-boot with Windows XP (installed first) and 9.10 installed alongside.

However, I had a business need for encryption, so I (foolishly) reinstalled 9.10.  I manually deleted all the 9.10 partitions and created a swap, a / and a /home partition of sensible sizes.  Then, when asked, I chose "use my password to login and decrypt my home folder"

Now ubuntu boots up fine, but although Windows appears in the grub menu, if I select it, the whole machine does a hard reset and grub appears again.

I found some other threads and one suggested using the script boot_info_script*.sh, so I downloaded that and ran it.  The RESULTS.txt is below.

I've got some programming skills and I can use a terminal, but I'm a GRUB novice.

I've reinstalled several times, i've tried sudo update-grub and I'm out of ideas now.

I would really like my windows installation back.  I have some (Windows) backups, but they would probably kill the MBR now that I've reinstalled ubuntu?

Thanks, in advance for any help you can provide.

Trevor

Here's the boot_info_script output - sorry if this is an incorrect way to post - I'm new here.

my windows partition is sda2
sda5 is /
sda6 is /home
sda7 is a swap area

Oh, sdb is just an auxiliary disc - it has no version of any OS installed on it, so I'm a bit confused why it says below "Windows is installed in the MBR of /dev/sdb".
 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 397263670 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 397276122 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc810ac3c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  1b Hidden W95 FAT32
/dev/sda2    *     16,370,235   387,471,734   371,101,500   7 HPFS/NTFS
/dev/sda3         387,471,735   625,137,344   237,665,610   5 Extended
/dev/sda5         387,471,798   428,485,679    41,013,882  83 Linux
/dev/sda6         428,485,743   619,273,619   190,787,877  83 Linux
/dev/sda7         619,273,683   625,137,344     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x565ad2e8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        44D7-70B8                              vfat       BACKUP                        
/dev/sda2        4A38F4AD38F498E1                       ntfs       HDD                           
/dev/sda5        ee0e6cff-7dc9-4379-88ce-7965f273fda2   ext4                                     
/dev/sda6        7387ae1c-ee8b-42e7-ba4a-5d06050037f7   ext4                                     
/dev/sda7        e9ac70ad-427d-4eeb-b25b-dd0af2f8eec7   swap                                     
/dev/sdb1        6EDEDBBFDEDB7E31                       ntfs       Elrond                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 44d7-70b8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 4a38f4ad38f498e1
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
UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=7387ae1c-ee8b-42e7-ba4a-5d06050037f7 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=e9ac70ad-427d-4eeb-b25b-dd0af2f8eec7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 200.1GB: boot/grub/core.img
 200.1GB: boot/grub/grub.cfg
 200.0GB: boot/initrd.img-2.6.31-14-generic
 199.9GB: boot/vmlinuz-2.6.31-14-generic
 200.0GB: initrd.img
 199.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by darkod on 2010-05-24
No need to reinstall anything. This is your pain:

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda2[/COLOR] and 
                       looks at sector 397276122 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

From ubuntu, use this fix on /dev/sda2:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to fix partition #2 on disk /dev/sda. After that it should work fine.

---

### Post by Trevor Burton on 2010-05-24
Thank you so much! That worked a treat.

Ubuntu is pretty friendly, but grub seems more of a black art.

I am very grateful for your help, and so fast.

Many thanks,

Trevor Burton

> **darkod said:**
> No need to reinstall anything. This is your pain:

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda2[/COLOR] and 
                       looks at sector 397276122 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

From ubuntu, use this fix on /dev/sda2:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to fix partition #2 on disk /dev/sda. After that it should work fine.

---

