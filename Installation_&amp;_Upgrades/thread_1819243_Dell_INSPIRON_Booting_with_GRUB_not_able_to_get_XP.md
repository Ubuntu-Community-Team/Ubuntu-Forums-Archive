---
title: "Dell INSPIRON Booting with GRUB not able to get XP  running"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by Karthik6 on 2011-08-05
Please Help

I have got Windows XP Pro installed in my Laptop. It had 2 partitions. In C drive i have got Windows XP. Installed UBUNTU in E Drive. It did partiion E drive futher to install it. Had the GRUB RESCUE prompt initially. But after running the following got into the next problem.

Grub reinstall fix:
Boot Ubuntu live CD. Then run
[COLOR=Navy]sudo mount /dev/sdf5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

and 

[/COLOR]If you want Grub in the MBR (which is normal) do this:
Boot from live 10.04 CD/USB
[COLOR=Navy]sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

Now i get a Grub prompt. Not able to get the windows loaded.Please help

Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.681640625 = 151.055761408  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```
[COLOR=Navy]
[/COLOR]

---

### Post by YesWeCan on 2011-08-05
Hi. You have used the wrong partition in your grub istall command. You need
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

This will get Ubuntu to boot. But you have installed grub to your XP partition. This has broken your XP boot. So you will have to repair your XP boot sector. Have you got an XP install CD?

---

### Post by oldfred on 2011-08-06
You also need to the the grub files you installed to winodws:

Boot files:        /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

And since your windows install in sda5 is to a logical partition I am not sure if the windows XP disk will fix it. Windows first install has to be to a primary NTFS partition with the boot flag. It prefers that other installs are to a primary but will let you install to a logical as long as you boot thru the primary. But I do not know if the fixBoot command will find the sda5 partition or just work on sda1 only. 

I might try testdisk on the sda5 partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Since the install is not directly booting from sda5 perhaps it does not matter.

---

### Post by Karthik6 on 2011-08-06
> **YesWeCan said:**
> Hi. You have used the wrong partition in your grub istall command. You need
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

This will get Ubuntu to boot. But you have installed grub to your XP partition. This has broken your XP boot. So you will have to repair your XP boot sector. Have you got an XP install CD?


Hi

I tried with windows CD Repair option but no luck.  :( .After running the scrit you mentioned gone back to the previous issue 'GRUB RESCUE prompt'

---

### Post by justinjthomas on 2011-08-06
Always Install Linux after Windows; if you're going for DUAL BOOT.

And try 11.04 Natty Its Awesome.

---

### Post by Karthik6 on 2011-08-06
> **justinjthomas said:**
> Always Install Linux after Windows; if you're going for DUAL BOOT.

And try 11.04 Natty Its Awesome.


Windows was installed 1st. then ubuntu was installed

---

### Post by Karthik6 on 2011-08-06
> **oldfred said:**
> You also need to the the grub files you installed to winodws:

Boot files:        /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

And since your windows install in sda5 is to a logical partition I am not sure if the windows XP disk will fix it. Windows first install has to be to a primary NTFS partition with the boot flag. It prefers that other installs are to a primary but will let you install to a logical as long as you boot thru the primary. But I do not know if the fixBoot command will find the sda5 partition or just work on sda1 only. 

I might try testdisk on the sda5 partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Since the install is not directly booting from sda5 perhaps it does not matter.

Running the script you mentioned, Shows Boot: Command not Found

Got the New Boot Script Result after running the above said scripts

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by oldfred on 2011-08-06
Did you run the commands YesWeCan suggested?

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Those should work but with Natty they also suggest this, minor change from root to boot:

sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda

If you get any errors running commands post entire set of commands as you have run them from liveCD.

---

### Post by Karthik6 on 2011-08-06
> **oldfred said:**
> Did you run the commands YesWeCan suggested?

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Those should work but with Natty they also suggest this, minor change from root to boot:

sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda

If you get any errors running commands post entire set of commands as you have run them from liveCD.


Yes i Did run the 1st command that when i posted the new result file.

Now i have run the command  you have suggested and the result file follows

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/9CBC3981BC3956CC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 2457: cd: /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
/mnt/: No such file or directory
```

---

### Post by YesWeCan on 2011-08-06
Would you mind putting code tags around the bootinfoscript output? It makes it a little easier to read and gives it tidy scroll bars.

Something changed between post #7 and post #9 because sda6 is different. The Grub install should not have caused this.

---

### Post by oldfred on 2011-08-06
I agree with YesWeCan. 

It looks like you deleted all the boot files or the /boot folder in sda6, so now it has nothing to boot with. You were only supposed to delete the /boot/grub folder in sda1 which was your windows install.

If that is what you did, it may be easier to just reinstall if you have nothing to recover in the way of saved data. You can also do a full chroot into your system from a liveCD and in effect reinstall from inside your system, but it requires a lot of copy & pasting or typing.

---

### Post by Karthik6 on 2011-08-06
> **oldfred said:**
> I agree with YesWeCan. 

It looks like you deleted all the boot files or the /boot folder in sda6, so now it has nothing to boot with. You were only supposed to delete the /boot/grub folder in sda1 which was your windows install.

If that is what you did, it may be easier to just reinstall if you have nothing to recover in the way of saved data. You can also do a full chroot into your system from a liveCD and in effect reinstall from inside your system, but it requires a lot of copy & pasting or typing.

Hi

I just Need to get my XP rup and running, it's ok to drop off ubuntu

this is the new result 
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by oldfred on 2011-08-06
It looks like Ubuntu should boot, does it?

You still have this in sda1 which confused grub/windows.
```

sda1: ____________________________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files: /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

```

Please use code tags.
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you go back and edit you previous posts and "go advanced", you get the full edit panel at the top which gives you the # or code tag icon.

---

### Post by Karthik6 on 2011-08-06
> **oldfred said:**
> It looks like Ubuntu should boot, does it?

You still have this in sda1 which confused grub/windows.
```

sda1: ____________________________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files: /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

```Please use code tags.
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you go back and edit you previous posts and "go advanced", you get the full edit panel at the top which gives you the # or code tag icon.

Hi

I have update the previous Quote as requested.

No Ubuntu does not boot up I'm using live CD.

Please let me know is there a way to get my XP up and running

---

### Post by oldfred on 2011-08-06
You have many /boot/grub/core.img. Did you delete the one from Windows?

If you just want windows we can reinstall a windows boot loader, but that will not boot Ubuntu.

Because you have several core.img in sda6, I think you need to chroot into your system and uninstall and reinstall grub2 completely to clean it up. Other alternative is a reinstall being sure to install grub to sda, not to any partition like sda1 or sda5.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YesWeCan on 2011-08-06
Ditto oldfred's instructions.

To remove the linux boot directory from the sda1 partition:

sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/boot

Don't go and remove /mnt/boot.ini tho!

Try the lilo MBR. This is an MBR very much like the original Windows one and will cause your XP to boot if the XP boot sector and boot-loader are ok.

---

### Post by Karthik6 on 2011-08-06
> **YesWeCan said:**
> Ditto oldfred's instructions.

To remove the linux boot directory from the sda1 partition:

sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/boot

Don't go and remove /mnt/boot.ini tho!

Try the lilo MBR. This is an MBR very much like the original Windows one and will cause your XP to boot if the XP boot sector and boot-loader are ok.

So Shall i just run the above command ?

sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/boot

---

### Post by Karthik6 on 2011-08-06
> **oldfred said:**
> You have many /boot/grub/core.img. Did you delete the one from Windows?

If you just want windows we can reinstall a windows boot loader, but that will not boot Ubuntu.

Because you have several core.img in sda6, I think you need to chroot into your system and uninstall and reinstall grub2 completely to clean it up. Other alternative is a reinstall being sure to install grub to sda, not to any partition like sda1 or sda5.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I'm not sure which commands i should use from **[COLOR=DarkRed][SIZE=4]Chroot[/SIZE][/COLOR]** do i have a separate boot partition ?


Hi I have done all this 

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box  against the Universe repo in the Ubuntu Software tab. Close that window  and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Except 

chroot & grub uninstall & reinstall -drs305 Should i do this or just run the command in the next post

---

### Post by YesWeCan on 2011-08-06
> **Karthik6 said:**
> Hi I have done all this 

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box  against the Universe repo in the Ubuntu Software tab. Close that window  and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Except 

chroot & grub uninstall & reinstall -drs305 Should i do this or just run the command in the next post
You did the lilo stuff, good. Don't worry about chroot just yet - that's for getting Ubuntu to boot. First you need to get XP back. Do those commands to delete the boot directory in sda1 (post #17) and then try and boot.
If it won't boot then post a fresh bootinfoscript output.

---

### Post by Karthik6 on 2011-08-06
> **YesWeCan said:**
> You did the lilo stuff, good. Don't worry about chroot just yet - that's for getting Ubuntu to boot. First you need to get XP back. Do those commands to delete the boot directory in sda1 (post #17) and then try and boot.
If it won't boot then post a fresh bootinfoscript output.

Excellent thank you very much got my XP back. Is there any way i can get ubuntu working? 

I'm pasting the new results from Boot info script 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1


```

---

### Post by YesWeCan on 2011-08-06
Ok that's a good start. :)

The easy methods to restore Grub did not work earlier. So it is best to purge and reinstall Grub in your Ubuntu installation. 

Follow the link oldfred provided in post #15:
> chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Be careful.

---

### Post by Karthik6 on 2011-08-06
> **YesWeCan said:**
> Ok that's a good start. :)

The easy methods to restore Grub did not work earlier. So it is best to purge and reinstall Grub in your Ubuntu installation. 

Follow the link oldfred provided in post #15:


Be careful.

Sorry im not very sure how to do that

I'm not sure which commands i should use from **[COLOR=DarkRed][SIZE=4]Chroot[/SIZE][/COLOR]** do i have a separate boot partition ?

If you don't mind will you be able to help me with the commands

---

### Post by Hakunka-Matata on 2011-08-06
I trust you will wait on YesWeCan to reply, I hope you do.  I'm not trying to take over here!  The Grub2 hyperlink below is where you will go to follow the instructions, UNLESS he wanted you to use the new GUI tool.  I thought you may want to study this a bit whilst waiting on confirmation from YesWeCan. 

[Grub2]("https://help.ubuntu.com/community/Grub2#Purge%20&%20Reinstall")  Slide up to the top of the page, and see Contents, section 12.1...............

[QUOTE
12. [Reinstalling GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
[LIST=1]
[*][Methods of Reinstalling]("https://help.ubuntu.com/community/Grub2#Methods%20of%20Reinstalling")
[LIST=1]
[*][Use Boot-Repair Graphical Tool]("https://help.ubuntu.com/community/Grub2#Use%20Boot-Repair%20Graphical%20Tool")
[*][Copy LiveCD Files]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files")
[*][Copy Partition Files]("https://help.ubuntu.com/community/Grub2#Copy%20Partition%20Files")
[*][ChRoot]("https://help.ubuntu.com/community/Grub2#ChRoot")
[*][Purge & Reinstall]("https://help.ubuntu.com/community/Grub2#Purge%20&%20Reinstall")
[/LIST]
 
[/LIST]
[/QUOTE]

---

### Post by garvinrick4 on 2011-08-06
Hi, Karthik6,
 I got your message where are you now? Are you able to boot Windows and want
to boot your Ubuntu also?

---

### Post by garvinrick4 on 2011-08-06
#Given you have installed lilo and Windows is booting and you want to boot both:
This is the same as the links you have there are more than one way to get into
chroot. This is just one of them. Copy and paste one at a time. Make sure the
internet is working on the Live CD.

```
sudo mount /dev/sda6 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo mount cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
apt-get purge grub grub-common grub-pc
apt-get install grub-common grub-pc
***Use Tab to toggle with to install grub to sda, not code to copy and paste**
grub-install /dev/sda
update-grub
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```grub-install /dev/sda (is redundant just want to make sure it is in sda)

---

### Post by YesWeCan on 2011-08-07
> If you don't mind will you be able to help me with the commands
No problem. I just read that site and it is quite complicated to follow because it caters for lots of scenarios at once. Here are the commands you should run from a terminal. Just cut and past each on in turn:

```

sudo mount /dev/sda6 /mnt

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt

apt-get purge grub grub-pc grub-common

apt-get install grub-common grub-pc

update-grub 

grub-install /dev/sda

exit
```
Then reboot.
As garvinrick4 mentions, choose to install Grub to /dev/sda.

---

### Post by Karthik6 on 2011-08-12
> **garvinrick4 said:**
> #Given you have installed lilo and Windows is booting and you want to boot both:
This is the same as the links you have there are more than one way to get into
chroot. This is just one of them. Copy and paste one at a time. Make sure the
internet is working on the Live CD.

```
sudo mount /dev/sda6 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo mount cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
apt-get purge grub grub-common grub-pc
apt-get install grub-common grub-pc
***Use Tab to toggle with to install grub to sda, not code to copy and paste**
grub-install /dev/sda
update-grub
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```grub-install /dev/sda (is redundant just want to make sure it is in sda)

Hi

I get the following error message
```
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package grub-common
E: Package 'grub-pc' has no installation candidate

```
```
root@ubuntu:/# grub-install /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>

```

---

### Post by Karthik6 on 2011-08-12
> **YesWeCan said:**
> No problem. I just read that site and it is quite complicated to follow because it caters for lots of scenarios at once. Here are the commands you should run from a terminal. Just cut and past each on in turn:

```

sudo mount /dev/sda6 /mnt

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt

apt-get purge grub grub-pc grub-common

apt-get install grub-common grub-pc

update-grub 

exit
```Then reboot.
As garvinrick4 mentions, choose to install Grub to /dev/sda.

New Boot info result
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1


```

---

### Post by oldfred on 2011-08-12
I think when you deleted the /boot in sda6 you deleted the kernel & all related files.

chroot into your system again like you did. And run all these commands.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
#Some of these may not work as you have already deleted grub and may not even have /boot/grub.
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

Then exit chroot & reboot.

---

### Post by Karthik6 on 2011-08-12
> **oldfred said:**
> I think when you deleted the /boot in sda6 you deleted the kernel & all related files.

chroot into your system again like you did. And run all these commands.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
#Some of these may not work as you have already deleted grub and may not even have /boot/grub.
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

Then exit chroot & reboot.
Looks like it has not worked
```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# dpkg --configure -a
root@ubuntu:/# reinstall kernel:
reinstall: command not found
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Ign http://extras.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease
Err http://security.ubuntu.com natty-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com natty Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com natty-security Release
Ign http://extras.ubuntu.com natty Release
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex
Ign http://extras.ubuntu.com natty/main TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex
Ign http://gb.archive.ubuntu.com natty InRelease
Ign http://gb.archive.ubuntu.com natty-updates InRelease
Ign http://security.ubuntu.com natty-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Err http://gb.archive.ubuntu.com natty Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Err http://gb.archive.ubuntu.com natty-updates Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://gb.archive.ubuntu.com natty Release
Err http://extras.ubuntu.com natty/main Sources
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://gb.archive.ubuntu.com natty-updates Release
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex
Err http://extras.ubuntu.com natty/main i386 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com natty/main Translation-en_US
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com natty/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/universe TranslationIndex
Err http://security.ubuntu.com natty-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com natty-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/main Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/multiverse Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/restricted Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/universe Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/main Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/restricted Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/universe Translation-en_US
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com natty-updates/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# sudo apt-get install linux-image
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-2.6.38-8-generic' instead of 'linux-image'
linux-image-2.6.38-8-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'grub' can't be removed
Virtual packages like 'grub-pc' can't be removed
E: Unable to locate package grub-common
root@ubuntu:/# mv /boot/grub /boot/grub_backup
mv: cannot stat `/boot/grub': No such file or directory
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get install grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'grub-pc' has no installation candidate
E: Unable to locate package grub-common
root@ubuntu:/# grub-install /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# grub-install /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# grub-install --recheck /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# exit
exit

```

---

### Post by oldfred on 2011-08-12
Either your Internet is not working or your sources list has errors. I do not know how to fix from command line. You might post this to see if anyone sees the problem.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Then open & post the copy. 
sudo nano ~/sources.list.backup

---

### Post by Karthik6 on 2011-08-12
> **oldfred said:**
> Either your Internet is not working or your sources list has errors. I do not know how to fix from command line. You might post this to see if anyone sees the problem.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Then open & post the copy. 
sudo nano ~/sources.list.backup
Hi Oldfred, as requested
```
eb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty mai$
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu natty universe
# deb-src http://archive.ubuntu.com/ubuntu natty universe
# deb http://archive.ubuntu.com/ubuntu natty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu natty-updates universe
# deb http://security.ubuntu.com/ubuntu natty-security universe
# deb-src http://security.ubuntu.com/ubuntu natty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu natty multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty multiverse
# deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse
# deb http://security.ubuntu.com/ubuntu natty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

```

---

### Post by Karthik6 on 2011-08-12
> **Karthik6 said:**
> Hi Oldfred, as requested
```
eb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty mai$
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu natty universe
# deb-src http://archive.ubuntu.com/ubuntu natty universe
# deb http://archive.ubuntu.com/ubuntu natty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu natty-updates universe
# deb http://security.ubuntu.com/ubuntu natty-security universe
# deb-src http://security.ubuntu.com/ubuntu natty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu natty multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty multiverse
# deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse
# deb http://security.ubuntu.com/ubuntu natty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

```

Hi Please help 

Have reinstalled Ubuntu and now have gone back to the Grub problem here is my boot info script result some one help pls
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.688179016 = 151.062781952  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Karthik6 on 2011-08-12
> **Karthik6 said:**
> Hi Please help 

Have reinstalled Ubuntu and now have gone back to the Grub problem here is my boot info script result some one help pls
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.688179016 = 151.062781952  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

After running the 1st set of Code
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sda

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.688179016 = 151.062781952  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.649990082 = 151.021776896  grub/core.img                                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Karthik6 on 2011-08-12
> **Karthik6 said:**
> Excellent thank you very much got my XP back. Is there any way i can get ubuntu working? 

I'm pasting the new results from Boot info script 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1


```

Boot info result after running 2nd set of commands
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.688179016 = 151.062781952  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.649990082 = 151.021776896  grub/core.img                                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1


```

---

### Post by oldfred on 2011-08-12
The grub install is not quite correct in the MBR.
Yours says this:

(,msdos6)/grub

And it should say this:

(,msdos6) /boot/grub

Try this, I understood that this should not matter, but have seen it as you have done it and with this extra / after mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=[COLOR=Red]/mnt/ [/COLOR]/dev/sda

The first line of sources does not look correct. Did you not copy correctly or does it have missing characters, both a missing d at the beginning & missing end of the line?

---

### Post by YesWeCan on 2011-08-13
I'm tempted to suggest reinstalling Ubuntu from scratch. BUT I have another couple of suggestions first.

Based on your bootinfoscript in post #35 I think there is a problem because you have both /grub/core.img and /boot/grub/core.img in sda6 and --boot-directory will look at /grub/core.img which is probably the wrong one.

So. Try this from live CD:

sudo mount /dev/sda6 /mnt
sudo rm -r /mnt/grub
sudo grub-install --root-directory=/mnt /dev/sda

Then try booting. If it doesn't boot, please post another bootinfoscript. :)

@oldfred: I think the --boot-directory first assumes /mnt is the actual boot directory /boot and looks for a grub directory. I think only if it fails to find one it looks for a boot/grub directory. I think the legacy --root-directory always looks for boot/grub first. I'm speculating but this is what I reckon is going on.
Presumably, [COLOR="Navy"]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR] would have worked.

---

### Post by Karthik6 on 2011-08-13
> **YesWeCan said:**
> I'm tempted to suggest reinstalling Ubuntu from scratch. BUT I have another couple of suggestions first.

Based on your bootinfoscript in post #35 I think there is a problem because you have both /grub/core.img and /boot/grub/core.img in sda6 and --boot-directory will look at /grub/core.img which is probably the wrong one.

So. Try this from live CD:

sudo mount /dev/sda6 /mnt
sudo rm -r /mnt/grub
sudo grub-install --root-directory=/mnt /dev/sda

Then try booting. If it doesn't boot, please post another bootinfoscript. :)

@oldfred: I think the --boot-directory first assumes /mnt is the actual boot directory /boot and looks for a grub directory. I think only if it fails to find one it looks for a boot/grub directory. I think the legacy --root-directory always looks for boot/grub first. I'm speculating but this is what I reckon is going on.
Presumably, [COLOR=Navy]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR] would have worked.

Boot info script after running the above command. Has taken be back to GRUB rescue prompt
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.649318695 = 151.021056000  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by YesWeCan on 2011-08-13
Drat. Either resinstall ubuntu or try these commands at the grub rescue> prompt:
```
rescue> set prefix=(hd0,6)/boot/grub
rescue> insmod (hd0,6)/boot/grub/linux.mod
rescue> set root=(hd0,6)
rescue> linux /vmlinuz root=/dev/sda6 ro
rescue> initrd /initrd.img
rescue> boot
```

If it boots, run:
[COLOR="Navy"]sudo update-grub
sudo grub-install /dev/sda[/COLOR]

and you'll be back in business.

---

### Post by Karthik6 on 2011-08-13
> **Karthik6 said:**
> Boot info script after running the above command. Has taken be back to GRUB rescue prompt
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.649318695 = 151.021056000  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Boot info result after running 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

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
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
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
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.649318695 = 151.021056000  boot/grub/core.img                             1
 130.683063507 = 140.319870976  boot/grub/grub.cfg                             1
 132.039062500 = 141.775863808  boot/initrd.img-2.6.38-10-generic              2
 130.335937500 = 139.947147264  boot/initrd.img-2.6.38-8-generic               2
 130.457340240 = 140.077502464  boot/vmlinuz-2.6.38-10-generic                 2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 132.039062500 = 141.775863808  initrd.img                                     2
 130.335937500 = 139.947147264  initrd.img.old                                 2
 130.457340240 = 140.077502464  vmlinuz                                        2
 140.679912567 = 151.053905920  vmlinuz.old                                    1


```

---

### Post by YesWeCan on 2011-08-13
Ah you reinstalled lilo. So now you can boot Windows again but not Ubuntu.

So reinstall Grub again:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
reboot

If you get grub rescue> then follow the instructions I gave.

If that doesn't work, I'd reinstall Ubuntu.

---

### Post by Karthik6 on 2011-08-13
> **YesWeCan said:**
> Drat. Either resinstall ubuntu or try these commands at the grub rescue> prompt:
```
rescue> set prefix=(hd0,6)/boot/grub
rescue> insmod (hd0,6)/boot/grub/linux.mod
rescue> set root=(hd0,6)
rescue> linux /vmlinuz root=/dev/sda6 ro
rescue> initrd /initrd.img
rescue> boot
```If it boots, run:
[COLOR=Navy]sudo update-grub
sudo grub-install /dev/sda[/COLOR]

and you'll be back in business.

Ran the above commands it say the following error message

rescue> insmod (hd0,6)/boot/grub/linux.mod  - no such partition

rescue> linux /vmlinuz root=/dev/sda6 ro  - unknow command linux
rescue> initrd /initrd.img  - unknown command initrd
rescue> boot[/CODE]If it boots, run:  - unknown command boot

---

### Post by oldfred on 2011-08-13
Did you type the set prefix line without error?

If so then reinstall is probably the best solution to clean things up totally.

If you use manual install (Something else in Natty) you can select sda6 as / (root) and format as ext4. It will find swap automatically and you can reinstall in less than an hour. Be sure to let it install grub2's boot loader to sda not to any partition like sda1. The MBR, or sda should be the default in the combo box at the bottom of the select partitions screen.

---

### Post by Karthik6 on 2011-08-13
> **oldfred said:**
> Did you type the set prefix line without error?

If so then reinstall is probably the best solution to clean things up totally.

If you use manual install (Something else in Natty) you can select sda6 as / (root) and format as ext4. It will find swap automatically and you can reinstall in less than an hour. Be sure to let it install grub2's boot loader to sda not to any partition like sda1. The MBR, or sda should be the default in the combo box at the bottom of the select partitions screen.

Hi

I have deleted all the partitions except for the windows operating system and repartitioned, one for windows operating system, one for windows data and one septate partition for Ubuntu. Any suggestion before i start installing Ubuntu ?

---

### Post by oldfred on 2011-08-13
I like to have /home separate, so you can reinstall without losing your data and settings. But it depends on what you plan to do and how much space you want to use for each system. With most of your data in a shared NTFS partition the separate /home is not required as the /home folder with the hidden settings and very little data is small and easily backed up.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

