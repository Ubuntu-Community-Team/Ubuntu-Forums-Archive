---
title: "GRUB2 - Win7 dual boot conflict"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by BlackMaxPhoto on 2010-04-21
I recently upgraded from 9.10 to 10.04 and am no longer able to boot into Win7.

Win7 would show up in GRUB2 but selecting it only resulted in the machine going to a blank screen.

Attempting to restore the mbr only resulted in nothing booting ... noe running from the 9.10 live cd


How do I get Win7 to run again?

BC

---

### Post by Jake007g on 2010-04-21
If you REALLY need to boot windows you could always boot from your windows installation disk, load up the recovery console and use the 'fixmbr' command.

Doing this will completely remove grub though.

My advice is to do that, backup anything from windows you need, and re-install grub.

---

### Post by BlackMaxPhoto on 2010-04-21
I already did that ... it only resulted in NOTHING BOOTING, which is what got me here, running the 9.10 live cd.

If memory serves there's an issue with drive numbering in GRUB2 that I need deal with to get back to Kansas

BC

---

### Post by BlackMaxPhoto on 2010-04-21
...meantime, still no Windowz.

Anybody know how to solve this issue?

BC

---

### Post by Mark Phelps on 2010-04-21
> **Jake007g said:**
> If you REALLY need to boot windows you could always boot from your windows installation disk, load up the recovery console and use the 'fixmbr' command.

There is no Recovery Console in MS Windows anymore.  That got removed with the transition to Vista years ago.  That's only seen if you boot from a Windows XP CD -- and that can NOT repair the Vista/Win7 boot loader.

So, if you DID see a recovery console prompt, you're using the wrong Windows "disk".  Instead, boot from your Win7 DVD and run Startup Repair repeatedly until you can boot into Win7 again.

IF you don't have a Win7 DVD, go to the link below, download the proper Win7 image, burn it to CD, and boot from it.  It's a Win7 Repair CD and is used to repair boot problems:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by BlackMaxPhoto on 2010-04-21
There IS a boot repair utility, it didn't work

From what I saw earlier there is an issue with GRUB2 renumbering the drive partitions, that's the most likely solution to the problem.



What I need is a command line solution 

BC

:popcorn:

---

### Post by presence1960 on 2010-04-21
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

### Post by BlackMaxPhoto on 2010-04-22
=> Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 541002193 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 541650769 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 541204921 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 541117489 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   519,011,954   519,011,892   7 HPFS/NTFS
/dev/sda2         519,011,955   538,530,929    19,518,975  12 Compaq diagnostics
/dev/sda3         538,530,930   661,347,854   122,816,925   c W95 FAT32 (LBA)
/dev/sda4         661,347,855   703,282,606    41,934,752   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca6aa3da

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   540,715,769   540,713,722   7 HPFS/NTFS
/dev/sdb2         540,715,770   703,277,504   162,561,735   5 Extended
/dev/sdb5         540,715,833   623,659,364    82,943,532  83 Linux
/dev/sdb6         696,562,398   703,277,504     6,715,107  82 Linux swap / Solaris
/dev/sdb7         623,659,428   693,477,854    69,818,427  83 Linux
/dev/sdb8         693,477,918   696,562,334     3,084,417  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     7,935,999     7,927,936   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A2365C62365C398D                       ntfs                                     
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda3: ambivalent result (probably more filesystems on the device)
/dev/sda4        01C9B12D0AD2C680                       ntfs                                     
/dev/sdb1        5E3C431E3C42F097                       ntfs       NEW_VOLUME                    
/dev/sdb5        ca6f569d-d000-43e0-b950-927904b23643   ext4                                     
/dev/sdb6        e76da3f1-1063-410c-acb2-3429d86c403b   swap                                     
/dev/sdb7        d0852c87-0a37-4e94-b785-badc01f59ebf   ext4                                     
/dev/sdb8        03cfcddd-e96d-4bb9-8186-b4c1ca8eea71   swap                                     
/dev/sdc1        63CA-14B1                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-20-generic ...'
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-19-generic ...'
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-18-generic ...'
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-17-generic ...'
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a2365c62365c398d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 949ca48c9ca46a86
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=ca6f569d-d000-43e0-b950-927904b23643 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e76da3f1-1063-410c-acb2-3429d86c403b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 277.0GB: boot/grub/core.img
 277.8GB: boot/grub/grub.cfg
 277.5GB: boot/initrd.img-2.6.32-17-generic
 277.9GB: boot/initrd.img-2.6.32-18-generic
 293.0GB: boot/initrd.img-2.6.32-19-generic
 293.8GB: boot/initrd.img-2.6.32-20-generic
 294.9GB: boot/initrd.img-2.6.32-21-generic
 279.6GB: boot/vmlinuz-2.6.32-17-generic
 277.6GB: boot/vmlinuz-2.6.32-18-generic
 277.3GB: boot/vmlinuz-2.6.32-19-generic
 288.7GB: boot/vmlinuz-2.6.32-20-generic
 288.3GB: boot/vmlinuz-2.6.32-21-generic
 294.9GB: initrd.img
 293.8GB: initrd.img.old
 288.3GB: vmlinuz
 288.7GB: vmlinuz.old

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root=(hd1,7)
search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2365c62365c398d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 949ca48c9ca46a86
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=d0852c87-0a37-4e94-b785-badc01f59ebf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=03cfcddd-e96d-4bb9-8186-b4c1ca8eea71 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 321.8GB: boot/grub/core.img
 325.6GB: boot/grub/grub.cfg
 319.9GB: boot/initrd.img-2.6.31-14-generic
 319.6GB: boot/initrd.img-2.6.31-20-generic
 319.9GB: boot/vmlinuz-2.6.31-14-generic
 319.9GB: boot/vmlinuz-2.6.31-20-generic
 319.6GB: initrd.img
 319.9GB: initrd.img.old
 319.9GB: vmlinuz
 319.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by presence1960 on 2010-04-22
why is GRUB installed on the boot sectors of the ntfs partitions? That is most likely the cause of your woes in trying to boot windows. The fix is fairly simple. First go into BIOS and set the sda disk as first hard disk to boot in the hard disk boot order. Save changes to CMOS and boot the windows 7 install DVD. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for windows 7. When completed reboot without the windows DVD and make sure windows boots. if windows boots fine reboot and go into BIOS again and set the sdb disk as first hard disk to boot in the hard disk boot order. Save changes to CMOS and continue booting. This will bring up the GRUB menu. Boot windows from GRUB menu and see what happens.

P.S. If you don't have a windows DVD you can download a repair CD/DVD from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and use that to fix windows boot after downloading the iso and burning as an image to CD/DVD.

---

### Post by BlackMaxPhoto on 2010-04-22
I followed the instructions on the link you provided, they are the steps that originally got me here. Doing them again resulted in no change, still no Windows.

I changed the boot sequence for this session to the secondary hd and am now running 10.04 via GRUB, still no Windows from there either.

BC
:(

---

### Post by oldfred on 2010-04-22
There is another way to try to recover the boot sector using testdisk:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

When you installed Lucid beta did you check all the boxes on where to install grub? You are only supposed to check one MBR box not all the PBR (boot sector in window terms) as that overwrites the windows second part of the boot in the boot sector.

---

### Post by oldfred on 2010-04-22
You also have a separate issue in sda3.
"ambivalent result (probably more filesystems on the device)"

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by BlackMaxPhoto on 2010-04-22
After 'testdisk':

```

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 541002193 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 541650769 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 541204921 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 541117489 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   519,011,954   519,011,892   7 HPFS/NTFS
/dev/sda2         519,011,955   538,530,929    19,518,975  12 Compaq diagnostics
/dev/sda3         538,530,930   661,347,854   122,816,925   c W95 FAT32 (LBA)
/dev/sda4         661,347,855   703,282,606    41,934,752   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   540,715,769   540,713,722   7 HPFS/NTFS
/dev/sdb2         540,715,770   703,277,504   162,561,735   5 Extended
/dev/sdb5         540,715,833   623,659,364    82,943,532  83 Linux
/dev/sdb6         696,562,398   703,277,504     6,715,107  82 Linux swap / Solaris
/dev/sdb7         623,659,428   693,477,854    69,818,427  83 Linux
/dev/sdb8         693,477,918   696,562,334     3,084,417  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A2365C62365C398D                       ntfs                                     
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda3: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda4        01C9B12D0AD2C680                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5E3C431E3C42F097                       ntfs       NEW_VOLUME                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ca6f569d-d000-43e0-b950-927904b23643   ext4                                     
/dev/sdb6        e76da3f1-1063-410c-acb2-3429d86c403b   swap                                     
/dev/sdb7        d0852c87-0a37-4e94-b785-badc01f59ebf   ext4                                     
/dev/sdb8        03cfcddd-e96d-4bb9-8186-b4c1ca8eea71   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-20-generic ...'
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-19-generic ...'
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-18-generic ...'
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	echo	'Loading Linux 2.6.32-17-generic ...'
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a2365c62365c398d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 949ca48c9ca46a86
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=ca6f569d-d000-43e0-b950-927904b23643 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e76da3f1-1063-410c-acb2-3429d86c403b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 277.0GB: boot/grub/core.img
 292.1GB: boot/grub/grub.cfg
 277.5GB: boot/initrd.img-2.6.32-17-generic
 277.9GB: boot/initrd.img-2.6.32-18-generic
 293.0GB: boot/initrd.img-2.6.32-19-generic
 293.8GB: boot/initrd.img-2.6.32-20-generic
 296.2GB: boot/initrd.img-2.6.32-21-generic
 279.6GB: boot/vmlinuz-2.6.32-17-generic
 277.6GB: boot/vmlinuz-2.6.32-18-generic
 277.3GB: boot/vmlinuz-2.6.32-19-generic
 288.7GB: boot/vmlinuz-2.6.32-20-generic
 288.3GB: boot/vmlinuz-2.6.32-21-generic
 296.2GB: initrd.img
 293.8GB: initrd.img.old
 288.3GB: vmlinuz
 288.7GB: vmlinuz.old

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root=(hd1,7)
search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0852c87-0a37-4e94-b785-badc01f59ebf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0852c87-0a37-4e94-b785-badc01f59ebf ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2365c62365c398d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 949ca48c9ca46a86
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-18-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.32-17-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ca6f569d-d000-43e0-b950-927904b23643
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ca6f569d-d000-43e0-b950-927904b23643 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=d0852c87-0a37-4e94-b785-badc01f59ebf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=03cfcddd-e96d-4bb9-8186-b4c1ca8eea71 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 321.8GB: boot/grub/core.img
 325.6GB: boot/grub/grub.cfg
 319.9GB: boot/initrd.img-2.6.31-14-generic
 319.6GB: boot/initrd.img-2.6.31-20-generic
 319.9GB: boot/vmlinuz-2.6.31-14-generic
 319.9GB: boot/vmlinuz-2.6.31-20-generic
 319.6GB: initrd.img
 319.9GB: initrd.img.old
 319.9GB: vmlinuz
 319.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


---------------------

```
Still no Windows


BC
:(

---

### Post by oldfred on 2010-04-22
Could you go back and put code tags around your results.txt. Just highlight with the cursor the entire thing and click on the # in the panel above. It si difficult to scroll thru unless it is in the code box.

When you say no windows is that directly booting with sda as the choice in BIOS or from grub? Grub does not find it unless it works on its own.

---

### Post by BlackMaxPhoto on 2010-04-22
Windows 7 is listed in the GRUB2  menu but does not boot, attempting to boot from the primary hd yields a blank screen.
Attempting to boot Win7 from GBUB2 also yields the same blank screen

BC

---

### Post by oldfred on 2010-04-22
It is still a windows issue.

Did you do a full repair or just reinstall windows to the MBR.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by funicorn on 2010-04-22
Win7 boot loader is very sensitive to any mbr changes, and maybe too sensitive. The good news is you can always recover your mbr using windows7 
installation CD. FIrst boot from the cdrom, choose fix mode, then cmd lines. Under the cmd window you just need to type in following words:

bootsect /nt60 sys /mbr

Then reboot your computer and you should see the win7 loader interface. 
Next you have to make a chain loader manually to start ubuntu. You need grub4dos to do this. Download the newest version of grub4dos, extract the grldr, grub.exe and menu.lst to your c: partition. Then add a line to the bottom of file  boot.ini on c: partition (make a new one if it does not exist): C:\grldr="Start GRUB4DOS" . The last step is to edit the menu.lst file. Add these contents (do NOT include the comments):

title ubuntu
root (hd0,x)        %% x here denotes your ubuntu /boot partition  number,
                          %% count  from 0. 
kernel   /vmlinuz root=/dev/sday %% y=x+1
initrd   /initrd.img              
boot

And you're done. Reboot and press enter on the "Start GRUB4DOS" , you should see the grub4dos startup menu, which loads ubuntu for you. This 
is the  manual chain loader by grub4dos.

If you are not sure about the partition number, just guess one! Please remember the best thing of grub is you can edit the boot entry when it goes wrong. You need to press "e" on some entry to enter the edit mode, then change the partition number x if your guess is not a correct one. 

P.S. the old way of recovering mbr by "fixmbr" or "fdisk /mbr"  does NOT work any more for win7 booting. 

> **BlackMaxPhoto said:**
> I recently upgraded from 9.10 to 10.04 and am no longer able to boot into Win7.

Win7 would show up in GRUB2 but selecting it only resulted in the machine going to a blank screen.

Attempting to restore the mbr only resulted in nothing booting ... noe running from the 9.10 live cd


How do I get Win7 to run again?

BC

---

### Post by BlackMaxPhoto on 2010-04-23
I gave up, reformatted and re-installed Win7.

... the upside is that since this is an HP machine with dual internal HDs I can now simply select the secondary HD and boot 10.04 or 9.10. by default the machine now boots Win7

BC
:popcorn:

---

