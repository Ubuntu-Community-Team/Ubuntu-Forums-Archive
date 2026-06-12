---
title: "Ubuntu 10.04 LTS upgrade clobbers Windows XP"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by pking123 on 2010-06-04
I decided to upgrade to Lucid Lynx, and now when I reboot, grub both detects the Windows XP partition and gives it to me as a menu option, but when I boot into it, I get a blinking cursor and no other response whatsoever. CTRL+ALT_+DEL still reboots. Can anyone tell me what I can do to boot into XP? This has only been a problem since the upgrade.

---

### Post by oldfred on 2010-06-05
Welcome to the forum.

So we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


Also look at this, if you installed grub to all the partitions, not just the drives:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by pking123 on 2010-06-05
> **oldfred said:**
> Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Here are the contents of RESULTS.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1018777473 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   974,454,704   974,454,642   7 HPFS/NTFS
/dev/sda2         974,454,705 1,169,772,974   195,318,270  83 Linux
/dev/sda3       1,169,772,975 1,316,253,644   146,480,670  83 Linux
/dev/sda4       1,316,253,645 1,953,520,064   637,266,420   5 Extended
/dev/sda5       1,316,253,708 1,511,571,914   195,318,207  83 Linux
/dev/sda6       1,511,571,978 1,706,890,184   195,318,207  83 Linux
/dev/sda7       1,706,890,248 1,853,370,854   146,480,607  83 Linux
/dev/sda8       1,853,370,918 1,941,262,469    87,891,552  83 Linux
/dev/sda9       1,941,262,533 1,953,520,064    12,257,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        44A451F6A451EB46                       ntfs                                     
/dev/sda2        bc399e2b-ec46-476c-bc58-3cbb9f1ab84e   reiserfs                                 
/dev/sda3        63b9c1c9-13f1-42ee-a156-c167613d1d97   reiserfs                                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        78a837f5-5d7a-46c5-afd9-6a5ed449a8a9   reiserfs                                 
/dev/sda6        316318d2-4b86-47b5-bd43-7df3948f3ebd   reiserfs                                 
/dev/sda7        22af0b6a-8452-4ff6-9c34-c790e57aaf8e   reiserfs                                 
/dev/sda8        004a5633-5f4b-4481-b8b8-95ca87659e8e   reiserfs                                 
/dev/sda9        495dadbc-5304-47bc-8af1-f9493b0a77fe   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        reiserfs   (rw,notail)
/dev/sda3        /home                    reiserfs   (rw)
/dev/sda5        /usr                     reiserfs   (rw)
/dev/sda6        /usr/local               reiserfs   (rw)
/dev/sda7        /var                     reiserfs   (rw)
/dev/sda8        /tmp                     reiserfs   (rw)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

=========================== sda2/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 78a837f5-5d7a-46c5-afd9-6a5ed449a8a9
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod reiserfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=bc399e2b-ec46-476c-bc58-3cbb9f1ab84e ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        echo    'Loading Linux 2.6.32-22-generic ...'
        linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=bc399e2b-ec46-476c-bc58-3cbb9f1ab84e ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        linux   /boot/vmlinuz-2.6.31-21-generic root=UUID=bc399e2b-ec46-476c-bc58-3cbb9f1ab84e ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        echo    'Loading Linux 2.6.31-21-generic ...'
        linux   /boot/vmlinuz-2.6.31-21-generic root=UUID=bc399e2b-ec46-476c-bc58-3cbb9f1ab84e ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod reiserfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set bc399e2b-ec46-476c-bc58-3cbb9f1ab84e
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 44a451f6a451eb46
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=bc399e2b-ec46-476c-bc58-3cbb9f1ab84e /               reiserfs notail          0       1
# /home was on /dev/sda3 during installation
UUID=63b9c1c9-13f1-42ee-a156-c167613d1d97 /home           reiserfs defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=004a5633-5f4b-4481-b8b8-95ca87659e8e /tmp            reiserfs defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=78a837f5-5d7a-46c5-afd9-6a5ed449a8a9 /usr            reiserfs defaults        0       2
# /usr/local was on /dev/sda6 during installation
UUID=316318d2-4b86-47b5-bd43-7df3948f3ebd /usr/local      reiserfs defaults        0       2
# /var was on /dev/sda7 during installation
UUID=22af0b6a-8452-4ff6-9c34-c790e57aaf8e /var            reiserfs defaults        0       2
# swap was on /dev/sda9 during installation
UUID=495dadbc-5304-47bc-8af1-f9493b0a77fe none            swap    sw    
# /var was on /dev/sda7 during installation
UUID=22af0b6a-8452-4ff6-9c34-c790e57aaf8e /var            reiserfs defaults        0       2
# swap was on /dev/sda9 during installation
UUID=495dadbc-5304-47bc-8af1-f9493b0a77fe none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.1.1/public$  /media/acorn    cifs   rw,exec,user=admin,pass=dwersa  3

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.31-21-generic
    ??GB: boot/initrd.img-2.6.32-22-generic
    ??GB: boot/vmlinuz-2.6.31-21-generic
    ??GB: boot/vmlinuz-2.6.32-22-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old


```

---

### Post by darkod on 2010-06-05
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 1018777473 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

You have installed grub2 on the windows partition, /dev/sda1. Use this fix to repair it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #1 on disk /dev/sda. It should be fine after that.

---

### Post by pking123 on 2010-06-05
The problem is resolved ... Using testdisk repaired the boot sectors with a backup. I can now boot into Windows. Thanks!

---

