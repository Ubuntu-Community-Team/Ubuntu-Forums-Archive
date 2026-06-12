---
title: "Windows in grub cannot start after regular update"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by .volatile. on 2011-10-11
I made a normal update within Ubuntu 10.04 and it was not an upgrade.
However, my working Windows is not accessible, it just reboots when I choose its option in Grub.
Can you provide me with a solution please?

---

### Post by oldfred on 2011-10-11
Post this from liveCD or your Ubuntu install so we can see your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by .volatile. on 2011-11-01
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 59649408.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda2          40,965,750    80,292,869    39,327,120   5 Extended
/dev/sda5          40,965,813    56,596,994    15,631,182  83 Linux
/dev/sda6          56,789,838    59,649,344     2,859,507  82 Linux swap / Solaris
/dev/sda7          56,597,058    56,789,774       192,717  83 Linux
/dev/sda8          59,649,408    80,292,869    20,643,462   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6060D78160D75C7A                       ntfs       
/dev/sda5        f63fb857-0a05-4f8a-83cc-6315b1e44fbd   ext4       
/dev/sda6        25b7cd27-141a-4c16-9082-3c4d32bc5a6b   swap       
/dev/sda7        4c06b48e-fcb6-4913-b472-9ff5eb1254ec   ext4       
/dev/sda8        4878-A539                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /boot                    ext4       (rw)
/dev/sr0         /media/SZID 2011         udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar" /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set f63fb857-0a05-4f8a-83cc-6315b1e44fbd
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.32-34-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /vmlinuz-2.6.32-34-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.32-33-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.31-23-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.31-23-generic ...'
    linux    /vmlinuz-2.6.31-23-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional - magyar (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6060D78160D75C7A
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=4c06b48e-fcb6-4913-b472-9ff5eb1254ec /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=463d7c9b-3f48-4a90-9ad0-21b76a3a84e6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  19.549423695 = 20.991033856   boot/grub/core.img                             1
  19.548676968 = 20.990232064   boot/grub/grub.cfg                             1
  19.580076694 = 21.023947264   boot/initrd.img-2.6.31-23-generic              1
  19.570778370 = 21.013963264   boot/initrd.img-2.6.32-33-generic              4
  19.602028370 = 21.047517696   boot/initrd.img-2.6.32-34-generic              3
  19.555236340 = 20.997275136   boot/vmlinuz-2.6.31-23-generic                 1
  19.592716694 = 21.037519360   boot/vmlinuz-2.6.32-33-generic                 1
  19.582707882 = 21.026772480   boot/vmlinuz-2.6.32-34-generic                 2
  19.602028370 = 21.047517696   initrd.img                                     3
  19.570778370 = 21.013963264   initrd.img.old                                 4
  19.582707882 = 21.026772480   vmlinuz                                        2
  19.592716694 = 21.037519360   vmlinuz.old                                    1

============================= sda7/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set f63fb857-0a05-4f8a-83cc-6315b1e44fbd
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.32-34-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /vmlinuz-2.6.32-34-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.32-33-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux    /vmlinuz-2.6.31-23-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro   quiet splash
    initrd    /initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    echo    'Loading Linux 2.6.31-23-generic ...'
    linux    /vmlinuz-2.6.31-23-generic root=UUID=f63fb857-0a05-4f8a-83cc-6315b1e44fbd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 4c06b48e-fcb6-4913-b472-9ff5eb1254ec
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional - magyar (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6060D78160D75C7A
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.002982140 = 28.994231296   grub/core.img                                  1
  27.002235413 = 28.993429504   grub/grub.cfg                                  1
  27.033635139 = 29.027144704   initrd.img-2.6.31-23-generic                   1
  27.024336815 = 29.017160704   initrd.img-2.6.32-33-generic                   4
  27.055586815 = 29.050715136   initrd.img-2.6.32-34-generic                   3
  27.008794785 = 29.000472576   vmlinuz-2.6.31-23-generic                      1
  27.046275139 = 29.040716800   vmlinuz-2.6.32-33-generic                      1
  27.036266327 = 29.029969920   vmlinuz-2.6.32-34-generic                      2


```

---

### Post by oldfred on 2011-11-01
Boot script is not showing any issues that I can see. Boot files, boot.ini boot sector are all reported as correct. Have you run chkdsk recently. Windows does not seem to run it as often as it should. Ubuntu schedules a filecheck every 40 odd reboots.

 Checkdisk ---------------------------
To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

You have a separate /boot, but have boot files & grub in your / (root) partition also? You are booting from the MBR to sda7 the /boot partition.

---

### Post by .volatile. on 2011-11-16
How can I fixboot to C:?


To tell the truth, I have reinstalled windows and Ubuntu 10.04, 
and right after the first update (plus the updates of internet TV), my Windows always reboots after having reached the Windows booting screen with the blue statusbar.

How can I get my Windows alive again?

---

### Post by Mark Phelps on 2011-11-16
You boot from the Windows CD, choose the option to use Command Mode, and enter the commands that oldfred mentioned in his last post.

---

### Post by darkod on 2011-11-16
If you have your XP cd, boot with it and at the first screen press R for Recovery Mode.
Then it might ask you which partition you want to enter, but probably it will be only one C:. It also might ask you to enter the administrator password you specified when installing XP.

After that when the command prompt loads just execute:

chkdsk c: /r

Depending of the size of the partition be prepared to wait long time until it finishes, this is normal. Also you might see percentage progress but many times it will reach 100% and again start over, this is normal how windows does it, don't get panicked and don't interrupt it.

It is strange that it seems you have separate /boot partition and still have grub files on / too but it seems it should boot just fine anyway.

---

