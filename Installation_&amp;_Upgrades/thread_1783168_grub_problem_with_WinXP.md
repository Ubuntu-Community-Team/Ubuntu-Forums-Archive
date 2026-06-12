---
title: "grub problem with Win/XP"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by plcMark on 2011-06-15
Question: Where do I go to get help with a problem booting win/XP partitions?

sda has three bootable partitions: 
  sda1/ Win/XP (work version)
  sda3/ ubuntu 11.04
  sda4/ Win/XP (non-work related version)
  (sda2 is an extended partition with swap, and other stuff)

On install grub successfully finds all the OS's and creates menu items. 

When the machine boots I can select the ubuntu partition and it works great. I can select the first Win/xp partition and it works like windoze. When I select the 2nd Win/XP partition I get a msg 'autochk.exe not found ...', then the old BSOD for a few seconds, then the machine reboots.

This is clearly a grub problem. I put the old win/XP MBR boot loader back on the disk and it boots in either win/XP partition without problems. (I use a USB stick boot to crank up parted and change the hidden 'flag' and boot flags on the partitions to test this.)

Back to my question: Where do I go for help on this issue?

Thanks

---

### Post by oldfred on 2011-06-15
Welcome to the forums.

I am surprised you have a second entry for windows. Windows only has boot files in one partition with the boot flag (active partition in windows). Grub normally then only finds that partition to boot windows and then from windows you choose which version of windows you want to boot.

You have to move/copy all boot files from the first install of XP to the second install, reconfigure boot.ini and run fixboot from windows repair/boot CD to make sure windows has the correct boot partition. For fixboot to work you have to move boot flag to the second partition.

To see what you have and how it is configured:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

This explains how windows dual boots. It discusses Vista but applies to all MBR(msdos) systems. If too much explanation, just review pictures:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by plcMark on 2011-06-15
I'm not surprised it shows two Win/XP entries in the menu. I intended the two installs to be very separate. I am surprised by the output of the script. It looks like the ubuntu auto-install created a new swap partition each time I re-ran it. At some point it will be time to delete the two extra swap partitions and reformat the extra ext4 and probably mount it as /usr.

Output from the script follows. Any help would be really appreciated. I haven't played with linux since the old Slackware on floppy days. (Started with Yydragsil(?)  kernel 0.99) Its been a while, and things sure have changed!


```


                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS
/dev/sda2         312,580,155   722,178,047   409,597,893   5 Extended
/dev/sda5         312,580,157   517,382,080   204,801,924   7 NTFS / exFAT / HPFS
/dev/sda6         517,382,144   664,434,687   147,052,544  83 Linux
/dev/sda7         664,436,736   672,819,199     8,382,464  82 Linux swap / Solaris
/dev/sda8         672,821,248   681,203,711     8,382,464  82 Linux swap / Solaris
/dev/sda9         681,220,096   713,983,999    32,763,904   7 NTFS / exFAT / HPFS
/dev/sda10        713,986,048   722,178,047     8,192,000  82 Linux swap / Solaris
/dev/sda3         722,178,048   771,973,119    49,795,072  83 Linux
/dev/sda4         771,973,120   976,773,119   204,800,000  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        080832FA0832E5FA                       ntfs       
/dev/sda3        d966f6df-08bc-4d0d-9292-3e83217782e8   ext4       
/dev/sda4        37578EEB31594CE1                       ntfs       MLB
/dev/sda5        1CC8DCBDC8DC967C                       ntfs       MyDocs
/dev/sda6        9cd34514-e723-4ede-9114-bac28cb60043   ext4       
/dev/sda7        cd288931-a44a-451a-8c79-43c14b2fd5c0   swap       
/dev/sda9        5299D45936A90925                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=600)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=9cd34514-e723-4ede-9114-bac28cb60043 ro  splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=9cd34514-e723-4ede-9114-bac28cb60043 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 080832FA0832E5FA
    drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=9cd34514-e723-4ede-9114-bac28cb60043 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=cd288931-a44a-451a-8c79-43c14b2fd5c0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 282.963855743 = 303.830126592  boot/grub/core.img                             1
 302.915378571 = 325.252911104  boot/grub/grub.cfg                             2
 304.273632050 = 326.711324672  boot/initrd.img-2.6.38-8-generic-pae           1
 303.133239746 = 325.486837760  boot/vmlinuz-2.6.38-8-generic-pae              2
 304.273632050 = 326.711324672  initrd.img                                     1
 303.133239746 = 325.486837760  vmlinuz                                        2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
insmod png
if background_image /usr/share/images/grub/sabily.png; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d966f6df-08bc-4d0d-9292-3e83217782e8 ro  quiet  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d966f6df-08bc-4d0d-9292-3e83217782e8 ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d966f6df-08bc-4d0d-9292-3e83217782e8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 080832FA0832E5FA
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 37578EEB31594CE1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=9cd34514-e723-4ede-9114-bac28cb60043 ro splash quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9cd34514-e723-4ede-9114-bac28cb60043
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=9cd34514-e723-4ede-9114-bac28cb60043 ro single splash
    initrd /boot/initrd.img-2.6.38-8-generic-pae
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d966f6df-08bc-4d0d-9292-3e83217782e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cd288931-a44a-451a-8c79-43c14b2fd5c0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 346.516860962 = 372.069646336  boot/grub/core.img                             1
 360.594650269 = 387.185557504  boot/grub/grub.cfg                             1
 345.617160797 = 371.103600640  boot/initrd.img-2.6.38-8-generic               2
 346.493633270 = 372.044705792  boot/vmlinuz-2.6.38-8-generic                  1
 345.617160797 = 371.103600640  initrd.img                                     2
 346.493633270 = 372.044705792  vmlinuz                                        1

================================ sda4/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error



```

---

### Post by oldfred on 2011-06-16
I do not see anything wrong and as you say you can boot either with your other disk.

With old grub legacy we could hide & unhide and I assume that was how you got windows to install two separate installs. Grub2 does not have an unhide and I do not know if that makes a difference. Normally grub just jumps to the PBR of windows to boot just like a widows boot loader would. The windows boot loader only uses the boot flag (active partition) to know which partition to jump to. But perhaps the hidden flag interferes.

You might try unhiding the second windows. You might only need to rehide if you want to repair from a windows disk. But with XP you can do everything but run chkdsk from Ubuntu. 

I have had my XP boot ok but not be seen at all by gparted. Once I ran chkdsk then gparted saw XP drive. So Linux seems more sensitive to NTFS errors than windows. I might also try chkdsk. But then you will have to unhide & move boot flag to the sda4 partition.

[http://wiki.elchtest.eu/mediawiki/index.php/Grub2_Menu](http://wiki.elchtest.eu/mediawiki/index.php/Grub2_Menu)

---

### Post by plcMark on 2011-06-16
Removing the hidden flag did the trick. Of course, now both WIn/XP installs see the other's root files. 

Now I get to learn where to put that hidden stuff into the grub config files.  Thanks for the help, and for the link.

Mark

---

### Post by oldfred on 2011-06-16
I think you just use a parttool command in the grub boot stanza. I have never seen it done, thats what the link says. 

Why do both windows see the other. The boot.ini only showed one install and unless you updated boot.ini, I would not think one would see the other from a grub2 boot.

Example here (nearer bottom of page):
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

Parttool is in /boot/grub.

---

### Post by plcMark on 2011-06-19
Yes, parttool fixed the problem. It took a while for me to figure out the disk naming. The disk is /sda throughout grub.cfg, but in the parttool command it because hd0.

Each copy of windows was able to see the other's 'system partition' (C: drive). Of course, it would be 'mounted' with a different drive letter since C: was already used by the correct 'system partition'. This was fixed with the proper use of parttool. Now each windows sees only it own C: drive.

Mark

---

