---
title: "Cannot Access Windows 7 after upgrade to 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by justinmiller87 on 2010-05-09
Hi all, I seem to be having an issue with my system. I upgraded from 9.10 to 10.04 yesterday and I have to reboot into Windows 7 to do some coursework for school. I just tried to do this, and when I select Windows 7 from the list at the Grub2 splash screen, it goes blank for a bit and jumps me back to the Grub menu. I'm not sure if I did something wrong, like somehow install Grub to /dev/sda1 during the upgrade, but if that's the case, how do I remove it? I tried to do a sudo update-grub but that did not work. It found Windows 7, but on the reboot it still went back to the menu. Is this a Grub or Windows issue?

Thanks for the help.

---

### Post by darkod on 2010-05-09
Look at my post #4 here:
[http://ubuntuforums.org/showthread.php?t=1478386](http://ubuntuforums.org/showthread.php?t=1478386)

and do the same. Post your results and it will show us more.

---

### Post by justinmiller87 on 2010-05-09
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda8 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda8 starts at sector 63.
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
/dev/sda2             206,848    94,373,887    94,167,040   7 HPFS/NTFS
/dev/sda3          94,381,875   133,435,889    39,054,015  83 Linux
/dev/sda4         133,435,890   312,576,704   179,140,815   5 Extended
/dev/sda5         133,435,953   152,970,929    19,534,977  83 Linux
/dev/sda6         306,713,043   312,576,704     5,863,662  82 Linux swap / Solaris
/dev/sda7         300,849,318   306,712,979     5,863,662   7 HPFS/NTFS
/dev/sda8         152,970,993   300,849,254   147,878,262   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A08853048852D7FC                       ntfs       System Reserved               
/dev/sda2        485E5FA85E5F8E16                       ntfs                                     
/dev/sda3        b83a8282-862d-4c38-b059-edffcdae68c3   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        20373c93-467e-4533-b78b-2b76ab452295   ext4                                     
/dev/sda6        86107514-44a0-4c25-a4e1-1b0321edc6ab   swap                                     
/dev/sda7        C43EB38E3EB377CE                       ntfs                                     
/dev/sda8        B2FCEC5AFCEC1A7D                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)
/dev/sda5        /home                    ext4       (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b83a8282-862d-4c38-b059-edffcdae68c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b83a8282-862d-4c38-b059-edffcdae68c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a08853048852d7fc
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b83a8282-862d-4c38-b059-edffcdae68c3 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=20373c93-467e-4533-b78b-2b76ab452295 /home ext4 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=DF39-2991 /shared vfat utf8,umask=007,gid=46 0 1
# Entry for /dev/sda6 :
UUID=86107514-44a0-4c25-a4e1-1b0321edc6ab none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/Shared ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Network entry
//192.168.2.2/media_drive /media/media cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

=================== sda3: Location of files loaded by Grub: ===================


  48.4GB: boot/grub/core.img
  50.6GB: boot/grub/grub.cfg
  57.6GB: boot/initrd.img-2.6.32-22-generic
  56.1GB: boot/vmlinuz-2.6.32-22-generic
  57.6GB: initrd.img
  56.1GB: vmlinuz

```

---

### Post by darkod on 2010-05-09
Wow!. Somehow Grub2 ended up on almost all 8 partitions on your hdd. Strange... It shouldn't be on any of them, just on the MBR of the disk (the top of the results file saying Grub2 is on the MBR of /dev/sda).

Boot with your Win7 install dvd and after the language selection screen select Repair This Computer at bottom. There is automated process and manual as described here in the win7 section:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

However in your case I think the automated is the way to go. I never needed to do this so can't say 100%. Also, you might need to repeat it 3-4 times because it seems to repair only bits at a time.

Don't worry that temporary you won't be able to boot ubuntu. Your pain is to restore normal win7 boot process. Once the computer can boot directly into win7 and it's working fine, boot with your 10.04 cd in Try Ubuntu mode (live mode) and in terminal restore grub2 on /dev/sda with:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

PS. If you don't have win7 install dvd you can download an image of a repair cd here (no need for dvd, small image, only for repair:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by kansasnoob on 2010-05-09
This works just as well as using Windows recovery:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You might also like to add yourself as "effected" at my bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

And maybe even add a comment.

---

### Post by justinmiller87 on 2010-05-09
I haven't had a chance to reboot to verify yet, but after running the restore from Kansas and re-running the bash script, it looks like it repaired itself. I also added myself to the bug report.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda8 and 
                       looks at sector 94669267 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda8 starts at sector 63.
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
/dev/sda2             206,848    94,373,887    94,167,040   7 HPFS/NTFS
/dev/sda3          94,381,875   133,435,889    39,054,015  83 Linux
/dev/sda4         133,435,890   312,576,704   179,140,815   5 Extended
/dev/sda5         133,435,953   152,970,929    19,534,977  83 Linux
/dev/sda6         306,713,043   312,576,704     5,863,662  82 Linux swap / Solaris
/dev/sda7         300,849,318   306,712,979     5,863,662   7 HPFS/NTFS
/dev/sda8         152,970,993   300,849,254   147,878,262   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A08853048852D7FC                       ntfs       System Reserved               
/dev/sda2        485E5FA85E5F8E16                       ntfs                                     
/dev/sda3        b83a8282-862d-4c38-b059-edffcdae68c3   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        20373c93-467e-4533-b78b-2b76ab452295   ext4                                     
/dev/sda6        86107514-44a0-4c25-a4e1-1b0321edc6ab   swap                                     
/dev/sda7        C43EB38E3EB377CE                       ntfs                                     
/dev/sda8        B2FCEC5AFCEC1A7D                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)
/dev/sda5        /home                    ext4       (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b83a8282-862d-4c38-b059-edffcdae68c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b83a8282-862d-4c38-b059-edffcdae68c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b83a8282-862d-4c38-b059-edffcdae68c3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a08853048852d7fc
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b83a8282-862d-4c38-b059-edffcdae68c3 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=20373c93-467e-4533-b78b-2b76ab452295 /home ext4 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=DF39-2991 /shared vfat utf8,umask=007,gid=46 0 1
# Entry for /dev/sda6 :
UUID=86107514-44a0-4c25-a4e1-1b0321edc6ab none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/Shared ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Network entry
//192.168.2.2/media_drive /media/media cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

=================== sda3: Location of files loaded by Grub: ===================


  48.4GB: boot/grub/core.img
  50.7GB: boot/grub/grub.cfg
  57.6GB: boot/initrd.img-2.6.32-22-generic
  56.1GB: boot/vmlinuz-2.6.32-22-generic
  57.6GB: initrd.img
  56.1GB: vmlinuz
```

---

### Post by darkod on 2010-05-09
I'm not so sure. Grub2 is still on /dev/sda1 and that is the main one you need to get rid of, because that's where win7 boot files are (/bootmgr and /boot/bcd).

It seems to be gone from /dev/sda2 true, but it also added /grldr on /dev/sda2 which I can't see a purpose for.

PS. Sorry, /grldr was there in the first results too.

---

### Post by justinmiller87 on 2010-05-09
Yeah, I noticed that once I rebooted that I put it on the wrong one. Take three. :)

---

### Post by justinmiller87 on 2010-05-09
As this reply is coming from Windows 7, it worked. Thanks everyone for your help.

---

