---
title: "upgraded now can't boot windows from grub"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by howardc2 on 2010-05-20
Help. I upgraded to 10.04 but now i can't boot windows 7 from the grub. what can i do?

---

### Post by wilee-nilee on 2010-05-20
Post this script in code tags. To get the code tags set paste the script output into the reply highlight it then click on the # in the reply window. **Please post in the tags it is almost impossible to read otherwise.**
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by howardc2 on 2010-05-20
I don't really understand. I'm not good with these things...

---

### Post by StonedRaider on 2010-05-20
I had the same problem. What I did was:

open up terminal and type

sudo gedit /boot/grub/menu.lst

but first make a back up:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup


then once you open using the gedit command go to the bottom and with a space in between add the following 

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows 7/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1




then save it and reboot and windows 7 should be there :)

Tobin

---

### Post by wilee-nilee on 2010-05-20
> **howardc2 said:**
> I don't really understand. I'm not good with these things...

Boot with a live Ubuntu cd download the script put it on your desktop run this command from the terminal```
 bash ~/Desktop/boot_info_script*.sh
```

This will put the read out on the desktop then come back to your thread with the live cd paste the readout into a reply highlight it click on the # in the reply panel and hit submit reply.

Just so you know if you try to fix this without the information from the script, you are likely to make things worse, if no un-fixable. There are instruction on the link just go slow and maybe print this set of instructions or open 2 browser windows to read it.

I have faith that you can do it. ;)

---

### Post by wilee-nilee on 2010-05-20
> **StonedRaider said:**
> I had the same problem. What I did was:

open up terminal and type

sudo gedit /boot/grub/menu.lst

but first make a back up:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup


then once you open using the gedit command go to the bottom and with a space in between add the following 

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows 7/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1




then save it and reboot and windows 7 should be there :)

Tobin

First of all he has grub2 so your instructions are useless, lets see the boot script it is likely that grub was put in the windows partition. ;)

Might I add as well that advising somebody when their operating system is in danger of being lost, is a okay if you know what your doing, lets be sure to protect the operating system.

---

### Post by howardc2 on 2010-05-20
i'm not really sure about the particians. all i know is 7 is in 1, ubuntu in another and then a third was set up as shared storage between the two.

---

### Post by howardc2 on 2010-05-20
oh and the grub is 1.98

---

### Post by wilee-nilee on 2010-05-20
You will have to post the script if you want any qualified help.

---

### Post by howardc2 on 2010-05-21
Hope this is what you asked for...


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 103203085 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 103203085 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 103203085 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 103203085 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,901,759   102,694,912   7 HPFS/NTFS
/dev/sda3         102,912,390   166,385,204    63,472,815   5 Extended
/dev/sda5         102,912,453   166,385,204    63,472,752  83 Linux
/dev/sda4         166,387,712   625,139,711   458,752,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        88A8777FA8776B18                       ntfs       System Reserved               
/dev/sda2        E40EA9860EA9527A                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        02E60E96E60E8A5D                       ntfs                                     
/dev/sda5        a33779ca-21b8-4072-924d-ffea4e855b6d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
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
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a33779ca-21b8-4072-924d-ffea4e855b6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a33779ca-21b8-4072-924d-ffea4e855b6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a33779ca-21b8-4072-924d-ffea4e855b6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a33779ca-21b8-4072-924d-ffea4e855b6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a33779ca-21b8-4072-924d-ffea4e855b6d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 88a8777fa8776b18
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win 7 to GRUB Bootloader" >&2
cat << EOF
menuentry "Windows 7" {
set root=(hd0,2)
chainloader +1
}
EOF
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
UUID=a33779ca-21b8-4072-924d-ffea4e855b6d /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  52.8GB: boot/grub/core.img
  53.5GB: boot/grub/grub.cfg
  57.0GB: boot/initrd.img-2.6.31-21-generic
  58.9GB: boot/initrd.img-2.6.32-22-generic
  55.7GB: boot/vmlinuz-2.6.31-21-generic
  57.0GB: boot/vmlinuz-2.6.32-22-generic
  58.9GB: initrd.img
  57.0GB: initrd.img.old
  57.0GB: vmlinuz
  55.7GB: vmlinuz.old

---

### Post by darkod on 2010-05-21
Use this fix to remove grub2 from the partition /dev/sda1. So, you want to use it on partition #1 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Also, the custom win7 entry you made in 40_custom is wrong, it points to /dev/sda2. Your win7 boot files are on /dev/sda1 even thoughthe win7 system partition is indeed /dev/sda2.

But when you do the above mentioned fix, you will be able to boot win7 correctly. You can delete the entry in 40_custom.

---

### Post by newbie1969 on 2010-05-21
Hi There,

I also upgraded to 10.4 from 9.10 and now can't use guub to load windows vista

What have I done wrong? in simple terms please

Thanks

---

### Post by wilee-nilee on 2010-05-21
> **newbie1969 said:**
> Hi There,

I also upgraded to 10.4 from 9.10 and now can't use guub to load windows vista

What have I done wrong? in simple terms please

Thanks

Welcome to the forums, what you want to do to get a definitive answer is to start a thread of your own and post the boot script to start with. Post it in code tags by highlighting the text in the thread start then clicking on the # in the posting gui, this puts the very long script readout in a scrolling window and makes it easier to read. Every bodies boot problems are a little different and the script will show these problems.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have any problems with figuring this out PM me and I will be glad to help you get set up with it being posted. You don't want to do anything really without posting the script so that no mistakes are made that make things worse.

I will guess that when you upgraded that yop had grub install in a partition rather then the  mbr, but this is just a guess.

---

### Post by howardc2 on 2010-05-23
Its back. Thanks guys. Really saved my *** for these exams

---

