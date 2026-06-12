---
title: "Dual boot Ubuntu 10.04 / Vista - black screen"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by blackdalek on 2010-06-23
Hi,

My wife's laptop was dual booting fine with Vista (factory installed) and Ubuntu (installed off DVD).
We hadn't even touched Vista for months, so we don't know when the problem first happened.

Now when we select the Vista partition from the grub menu the computer will not boot. We just get a black screen with a blinking cursor in top left of screen. Ubuntu boots fine.

In the grub menu are various Ubuntu kernels and recovery modes for each, mem tests, and at the bottom the Vista partition and Vista Recovery partition.

I've searched the forums for solutions but can't find anything specific to our set of circumstances. All threads I can find on this subject are either about boot configurations which are totally different, use different OSes, different numbers of drives, different drive/parition configurations, the error occurs at a different stage of "bootability", or a completey different boot error, etc... or the solution simply does not work.

Is there any way to fix this or find out where the problem is?
Will running the Vista recovery partition to repair the non-booting Vista destroy grub and lose our Ubuntu install?
Please help.

---

### Post by blackdalek on 2010-06-23
Additional info.

Ok, I forgot we did install a second drive in this laptop. (It's been that long since we put Ubuntu on it).

First drive is 120Gb with the two original NTFS Vista partitions(dev/sda1 and dev/sda2).

Second drive is 200Gb with 50Gb NTFS parition(dev/sdb1), 147Gb ext4 partition (dev/sdb5 - ubuntu is on here) and 2.9Gb swap(dev/sdb6).

I cannot remember which drive or partition grub was installed to.


The grub menu is confgiured as follows -

Ubuntu kernel 2.6.32.22
Ubuntu kernel 2.6.32.22 recovery
Ubuntu kernel 2.6.32.21
Ubuntu kernel 2.6.32.21 recovery
memtest
memtest serial console
vista /dev/sda1 (main Windows Vista partition)
vista /dev/sda2 (Vista Recovery parition)

---

### Post by oldfred on 2010-06-24
To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by blackdalek on 2010-06-24
Here are the results from the boot info script -

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 102228822 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 102228438 of the same hard drive for 
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   220,620,644   220,620,582   7 HPFS/NTFS
/dev/sda2         220,620,645   234,436,544    13,815,900   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    97,659,134    97,657,087   7 HPFS/NTFS
/dev/sdb2          97,659,135   390,716,864   293,057,730   5 Extended
/dev/sdb5          97,659,198   385,094,114   287,434,917  83 Linux
/dev/sdb6         385,094,178   390,716,864     5,622,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2501DF733CF40735                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DC06F3A006F379BA                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        02742d80-f688-4529-aa5f-efbc6863b21e   ext4                                     
/dev/sdb6        1c72f35f-7e5a-49a7-9487-aaaf83918da0   swap                                     
/dev/sdb: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
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
search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=02742d80-f688-4529-aa5f-efbc6863b21e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=02742d80-f688-4529-aa5f-efbc6863b21e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=02742d80-f688-4529-aa5f-efbc6863b21e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=02742d80-f688-4529-aa5f-efbc6863b21e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 02742d80-f688-4529-aa5f-efbc6863b21e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2501df733cf40735
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
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
UUID=02742d80-f688-4529-aa5f-efbc6863b21e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=1c72f35f-7e5a-49a7-9487-aaaf83918da0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  52.3GB: boot/grub/core.img
  53.3GB: boot/grub/grub.cfg
  55.3GB: boot/initrd.img-2.6.31-21-generic
  55.3GB: boot/initrd.img-2.6.32-22-generic
  56.5GB: boot/vmlinuz-2.6.31-21-generic
  55.3GB: boot/vmlinuz-2.6.32-22-generic
  55.3GB: initrd.img
  55.3GB: initrd.img.old
  55.3GB: vmlinuz
  56.5GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-06-24
You have grub in sda1 and sdb1, use this to clean both.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
If used as described it should leave you with both OS booting.
sdb1 looks like a data partition and you can just remove grub from it manually. It wont hurt though if you use the link on both though.

---

### Post by blackdalek on 2010-06-24
Thanks, the testdisk method seems to have fixed it.

---

### Post by wilee-nilee on 2010-06-24
> **blackdalek said:**
> Thanks, the testdisk method seems to have fixed it.

Great I leaned about this by just watching others on the forum, like oldfred, testdisk is a great recovery tool as well if you ever delete a partition.:p

---

### Post by venkat211 on 2012-12-06
Hi ,

      Was working on a ubuntu 12.04 dual boot and everything was working fine till this morning when some updates were done to ubuntu. Now when I log into Windows Vista , I get a black screen.

The following is the content of RESULTS.txt file. Please help. Need windows for running statisical sw.

 >                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    61,442,047    61,440,000   7 NTFS / exFAT / HPFS
/dev/sda2          61,442,048   271,157,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda3         271,157,248   376,014,847   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda4         376,017,390   488,392,064   112,374,675   5 Extended
/dev/sda5         376,017,453   483,717,149   107,699,697  83 Linux
/dev/sda6         483,717,213   488,392,064     4,674,852  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F0C22CDFC22CABB2                       ntfs       
/dev/sda2        5C24B65224B62F40                       ntfs       Software and Data
/dev/sda3        728C34148C33D0F9                       ntfs       Movies and Music
/dev/sda5        fa6ee37d-0718-4aee-87d8-3c46ebb114a9   ext4       
/dev/sda6        3d4a0642-4618-4c29-8d76-f8cd50fe1121   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 75,75,75; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 3.2.0-34-generic ...'
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 3.2.0-32-generic ...'
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 3.2.0-31-generic ...'
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-43-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-2.6.32-43-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.32-43-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 2.6.32-43-generic ...'
    linux    /boot/vmlinuz-2.6.32-43-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-43-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    echo    'Loading Linux 2.6.31-23-generic ...'
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fa6ee37d-0718-4aee-87d8-3c46ebb114a9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F0C22CDFC22CABB2
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=fa6ee37d-0718-4aee-87d8-3c46ebb114a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3d4a0642-4618-4c29-8d76-f8cd50fe1121 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 182.811213017 = 196.292045312  boot/grub/core.img                             1
 205.499868870 = 220.653804032  boot/grub/grub.cfg                             1
 186.067175388 = 199.788108288  boot/initrd.img-2.6.31-23-generic              1
 196.736593723 = 211.244308992  boot/initrd.img-2.6.32-43-generic              2
 198.302568913 = 212.925762048  boot/initrd.img-3.2.0-31-generic               2
 187.812338352 = 201.661962752  boot/initrd.img-3.2.0-32-generic               3
 192.122885227 = 206.290377216  boot/initrd.img-3.2.0-33-generic               2
 191.360132694 = 205.471377920  boot/initrd.img-3.2.0-34-generic               2
 180.816942692 = 194.150713856  boot/vmlinuz-2.6.31-23-generic                 1
 190.435690403 = 204.478765568  boot/vmlinuz-2.6.32-43-generic                 1
 191.174715519 = 205.272287744  boot/vmlinuz-3.2.0-31-generic                  1
 193.991121769 = 208.296380928  boot/vmlinuz-3.2.0-32-generic                  1
 191.284090519 = 205.389728256  boot/vmlinuz-3.2.0-33-generic                  2
 189.604406834 = 203.586181632  boot/vmlinuz-3.2.0-34-generic                  1
 191.360132694 = 205.471377920  initrd.img                                     2
 192.122885227 = 206.290377216  initrd.img.old                                 2
 189.604406834 = 203.586181632  vmlinuz                                        1
 191.284090519 = 205.389728256  vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

---

### Post by lisati on 2012-12-06
If a thread hasn't had a reponse for a year or more, it's sometimes better to start a new thread with a link back to the one with the similar problem.

BTW, "CODE" tags preserve formatting better than "QUOTE" tages when quoting configuration and other files.

Thread closed.

---

