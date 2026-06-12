---
title: "GRUB problem"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by Wer Bn on 2012-08-22
Hello guys

I installed Ubuntu 12.04 aside with Win XP.

So, I don't know why, the GRUB menu when the system starts didn't showed up and it jumped directly to Ubuntu.
Not a big deal that time, as I wanted to use Linux only.

But a few days I needed to login to Windows and I started searching for ways to repair the GRUB.
I tried many things, one of them led me to this:
[IMG]http://aaron-kelley.net/wp-content/uploads/2011/04/grub.png[/IMG]
WITHOUT the first line.

Now I don't knw what to do. I can't even start Ubuntu.
Need help.
Please.
Thanks in advance.

---

### Post by oldfred on 2012-08-22
If you have two operating systems, you should normally get the grub menu.

From a liveCD download and run the BootInfo and post the link it creates. It may be able to repair also:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Wer Bn on 2012-08-23
How do I download Boot-Info?
And how am I suposed to install boot-repair if it's in a LIVE CD.

Edit:
Ok, I downloaded and ran a script named bootinfoscript.sh
It generated a .txt file.
Here it goes:


>   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   256,991,804   256,991,742   7 NTFS / exFAT / HPFS
/dev/sda2         256,991,866   456,952,859   199,960,994   f W95 Extended (LBA)
/dev/sda5         256,991,868   452,759,894   195,768,027   7 NTFS / exFAT / HPFS
/dev/sda6         452,759,958   456,952,859     4,192,902  82 Linux swap / Solaris
/dev/sda3         456,953,856   488,396,799    31,442,944  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A082B69082B32ED                       ntfs       
/dev/sda3        65f140f2-f716-4746-a2ea-b4acd3fec35d   ext4       
/dev/sda5        6EB0C03DB0C00D91                       ntfs       
/dev/sda6        52b5333f-bec7-467d-83ec-077fef8f7249   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
  set locale_dir=($root)/boot/grub/locale
  set lang=pt_PT
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, com Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, com Linux 3.2.0-29-generic-pae (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    echo    'A carregar Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
    echo    'A carregar ramdisk inicial ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, com Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, com Linux 3.2.0-27-generic-pae (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    echo    'A carregar Linux 3.2.0-27-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
    echo    'A carregar ramdisk inicial ...'
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, com Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, com Linux 3.2.0-23-generic-pae (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    echo    'A carregar Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
    echo    'A carregar ramdisk inicial ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2A082B69082B32ED
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=2A082B69082B32ED    /media/sda1    ntfs-3g    defaults,locale=pt_PT.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=6EB0C03DB0C00D91    /media/sda5    ntfs-3g    defaults,locale=pt_PT.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=52b5333f-bec7-467d-83ec-077fef8f7249    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/stage2                               1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-27-generic-pae           2
               =                boot/initrd.img-3.2.0-29-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-27-generic-pae              1
               =                boot/vmlinuz-3.2.0-29-generic-pae              2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


---

### Post by oldfred on 2012-08-23
Boot-Repair also runs the same bootinfoscript and adds a few things. It can also fix your issue. So from liveCD download Boot-Repair or download full ISO with Boot-Repair.

You still have grub legacy (0.97) in the MBR but with 12.04 it shoudl be grub2 (1.99). Boot-Repair should give you the option to install grub2's boot loader to the MBR of your drive. Link in first post.

You can still install Boot-Repair to liveCD, it just will not be saved when you reboot. If you want to save a copy you have to download the full liveCD with it included. Both are available in links above.

---

### Post by Wer Bn on 2012-08-23
So, please tell me how can I download and un boot repair from a LIVE CD.
The link in your first post sugests to use ppai in command line, and that command doesn't run in LIVE CD.

Will the changes affect my system? Or just "temporary" like LIVE CD is?

---

### Post by YannBuntu on 2012-08-23
You can also use a CD including Boot-Repair. See [https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

> **Wer Bn said:**
> Will the changes affect my system? Or just "temporary" like LIVE CD is?

The "Create BootInfo report" button will just scan your system, it will not modify it. The "Recommended repair" and the "Advanced options" will.

---

### Post by Wer Bn on 2012-08-23
So, i gotta boot the system with that .iso?
Is that a way I can put it into a pen?

---

### Post by YannBuntu on 2012-08-23
yes, you can put it on a CD. Or on a USB key via UnetBootin or MultiSystem for example. (not with the USB creator included in Ubuntu)

---

### Post by Wer Bn on 2012-08-24
Thank you very much guys.
Now I can acess my Ubuntu.
But sometimes it doesn't start, or it is too slow before the PC starts the loading of the OS. Strange.

AND, I still can't acess Win XP, because the GRUB menu doesn't show up at the start.
Here, the report at the end of the BootRepair

> Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 748432 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   256,991,804   256,991,742   7 NTFS / exFAT / HPFS
/dev/sda2         256,991,866   456,952,859   199,960,994   f W95 Extended (LBA)
/dev/sda5         256,991,868   452,759,894   195,768,027   7 NTFS / exFAT / HPFS
/dev/sda6         452,759,958   456,952,859     4,192,902  82 Linux swap / Solaris
/dev/sda3         456,953,856   488,396,799    31,442,944  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,932,159     3,932,097   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A082B69082B32ED                       ntfs       
/dev/sda3        65f140f2-f716-4746-a2ea-b4acd3fec35d   ext4       
/dev/sda5        6EB0C03DB0C00D91                       ntfs       
/dev/sda6        52b5333f-bec7-467d-83ec-077fef8f7249   swap       
/dev/sdb1        8053-668D                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	echo	'Loading Linux 3.2.0-27-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 65f140f2-f716-4746-a2ea-b4acd3fec35d
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2A082B69082B32ED
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=65f140f2-f716-4746-a2ea-b4acd3fec35d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=2A082B69082B32ED	/media/sda1	ntfs-3g	defaults,locale=pt_PT.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=6EB0C03DB0C00D91	/media/sda5	ntfs-3g	defaults,locale=pt_PT.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=52b5333f-bec7-467d-83ec-077fef8f7249	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-23-generic-pae           2
            ?? = ??             boot/initrd.img-3.2.0-27-generic-pae           2
            ?? = ??             boot/initrd.img-3.2.0-29-generic-pae           2
            ?? = ??             boot/vmlinuz-3.2.0-23-generic-pae              1
            ?? = ??             boot/vmlinuz-3.2.0-27-generic-pae              1
            ?? = ??             boot/vmlinuz-3.2.0-29-generic-pae              2
            ?? = ??             vmlinuz                                        2
            ?? = ??             vmlinuz.old                                    1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit boot=live config   quiet

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label 32bits session
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   quiet

label ubnentry2
menu label 64bits session
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   quiet

label ubnentry3
menu label 32bits session (failsafe)
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal

label ubnentry4
menu label 64bits session (failsafe)
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal

label ubnentry5
menu label Memory test
kernel /live/memtest
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[13061]) leaked on lvscan invocation. Parent PID 16297: bash
File descriptor 8 (pipe:[13061]) leaked on lvscan invocation. Parent PID 16297: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-24__12h14 ===================
boot-repair version : 3.18-0ppa49~lucid
boot-sav version : 3.192-0ppa10~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
boot-repair updated
File descriptor 7 (pipe:[13061]) leaked on lvs invocation. Parent PID 5177: /bin/sh
File descriptor 8 (pipe:[13061]) leaked on lvs invocation. Parent PID 5177: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 17.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda3:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="2A082B69082B32ED" TYPE="ntfs"
/dev/sda3: UUID="65f140f2-f716-4746-a2ea-b4acd3fec35d" TYPE="ext4"
/dev/sda5: UUID="6EB0C03DB0C00D91" TYPE="ntfs"
/dev/sda6: UUID="52b5333f-bec7-467d-83ec-077fef8f7249" TYPE="swap"
/dev/sdb1: LABEL="PENDRIVE" UUID="8053-668D" TYPE="vfat"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  7 12:34 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 18:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 17:53 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 07:22 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 18:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 18:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 18:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 18:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 18:16 README




=================== dmesg | grep EFI :
This live-session is not EFI-compatible.




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	not-sepboot,	grubenv-ok	grub2,	no-docgrub,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda3.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda5.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	63 sectors * 512 bytes

=================== parted -l:

Model: ATA ST3250820AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  132GB  132GB   primary   ntfs            boot
2      132GB   234GB  102GB   extended                  lba
5      132GB   232GB  100GB   logical   ntfs
6      232GB   234GB  2147MB  logical   linux-swap(v1)
3      234GB   250GB  16.1GB  primary   ext4


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 2013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  2013MB  2013MB  primary  fat32        boot



                                                                          
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.

                                                                          
Error: /dev/fd0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd fd0 full fuse hidraw0 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sndstat sr0 stderr stdin stdout urandom vga_arbiter xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda1: WINDOWS users user.js Information Volume System RECYCLER Files Program Programas pagefile.sys NVIDIA ntldr NTDETECT.COM MSDOS.SYS Keil IO.SYS hiberfil.sys Settings and Documents Dev-Cpp CONFIG.SYS BTNext boot-sav boot.ini bootfont.bin $AVG AUTOEXEC.BAT

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs   1014M   56M  958M   6% /
tmpfs        tmpfs   1014M     0 1014M   0% /lib/init/rw
udev         tmpfs   1009M  196K 1008M   1% /dev
tmpfs        tmpfs   1014M     0 1014M   0% /dev/shm
/dev/sdb1     vfat    1.9G  358M  1.6G  19% /live/image
tmpfs        tmpfs   1014M   56M  958M   6% /live/cow
tmpfs        tmpfs   1014M     0 1014M   0% /live
tmpfs        tmpfs   1014M  8.0K 1014M   1% /tmp
/dev/sda1  fuseblk    123G   58G   66G  47% /mnt/boot-sav/sda1
/dev/sda3     ext4     15G  4.7G  9.4G  34% /mnt/boot-sav/sda3
/dev/sda5  fuseblk     94G   11G   83G  12% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3de93de9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15997   128495871    7  HPFS/NTFS
/dev/sda2           15998       28444    99980497    f  W95 Ext'd (LBA)
/dev/sda3           28445       30402    15721472   83  Linux
/dev/sda5           15998       28183    97884013+   7  HPFS/NTFS
/dev/sda6           28184       28444     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038d4d

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         245     1966048+   b  W95 FAT32
Partition 1 has different physical/logical endings:
phys=(243, 254, 63) logical=(244, 195, 15)



=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub2 of sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Custom-Repair
This setting will purge (in order to fix packages) and reinstall the grub2 of sda3 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
chroot /mnt/boot-sav/sda3 apt-get -y --force-yes update
Purge the GRUB of sda3
grub-pc available

The following extra packages will be installed:
grub-pc grub2-common
The following packages will be REMOVED:
grub
The following NEW packages will be installed:
grub-gfxpayload-lists grub-pc grub2-common
0 upgraded, 3 newly installed, 1 to remove and 3 not upgraded.

The following extra packages will be installed:
grub-gfxpayload-lists grub2-common
The following packages will be REMOVED:
grub
The following NEW packages will be installed:
grub-gfxpayload-lists grub-pc grub2-common
0 upgraded, 3 newly installed, 1 to remove and 3 not upgraded.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.

The following packages will be REMOVED:
grub
The following NEW packages will be installed:
grub2-common
0 upgraded, 1 newly installed, 1 to remove and 3 not upgraded.
DEBCHECK debOK, grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common

The following extra packages will be installed:
grub-gfxpayload-lists grub2-common
The following packages will be REMOVED:
grub
The following NEW packages will be installed:
grub-gfxpayload-lists grub-pc grub2-common
0 upgraded, 3 newly installed, 1 to remove and 3 not upgraded.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
DEBCHECK debOK, grub-pc grub-common ucf debconf
DEBCHECK debOK
Please type: sudo chroot "/mnt/boot-sav/sda3" apt-get install -fynsudo chroot "/mnt/boot-sav/sda3" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda3" apt-get purge -y --force-yes grub-common
Then type: sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc


=================== sda3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 24 12:23 grub.d
drwxr-xr-x  2 root root    4096 Aug 24 12:22 grub.d.bak
total 52
-rwxr-xr-x 1 root root 6715 May 17 07:22 00_header
-rwxr-xr-x 1 root root 5522 May 17 07:07 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 07:22 10_linux
-rwxr-xr-x 1 root root 6335 May 17 07:22 20_linux_xen
-rwxr-xr-x 1 root root 7603 May 17 07:22 30_os-prober
-rwxr-xr-x 1 root root  214 May 17 07:22 40_custom
-rwxr-xr-x 1 root root   95 May 17 07:22 41_custom
-rw-r--r-- 1 root root  483 May 17 07:22 README




Reinstall the GRUB of sda3 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda3 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found Microsoft Windows XP Professional on /dev/sda1
cp: cannot stat `/var/log/boot-sav/log/2012-08-24__12h14boot-repair44/sources.list': No such file or directory
chroot /mnt/boot-sav/sda3 apt-get -y --force-yes update
Unhide GRUB boot menu in sda3/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

paste.debian ko, using paste.ubuntu

The massage said to send an email if something went wrong.
But now I don't know the email.
What was it?

---

### Post by darkod on 2012-08-24
Is there a specific error it shows when you try to boot XP?

Also, I notice in fstab you are mounting the XP partition /dev/sda1. Do you really access it that often to need an auto mount at boot?

Windows hates other OS touching its system partition so i always try to avoid it. You can mount it temporarily when you need to, but i would avoid the auto mount. Besides, you have another ntfs partition to share data between the OSs, I would even touch sda1 from ubuntu.

Is this a brand new installation? Did you shrink the XP system partition with the ubuntu installer or not?

---

### Post by Wer Bn on 2012-08-24
I need to auto mount the partition.
To share some data.
But, is that a problem?

I didn't shrink it.
Yesterday, with the Grub prompt, before this fix, I acessed Windows Xp.

Just wrote:

root (hd0,0)
chainloader +1
boot

And, BAM, XP running good.

---

### Post by darkod on 2012-08-24
Boot ubuntu, open terminal and try:
sudo update-grub

See if that detects XP on sda1 (if it lists it). Then restart and try to boot it from the grub menu again.

---

### Post by Wer Bn on 2012-08-24
"Found Microsoft Windows XP Professional on /dev/sda1"
Yup, it founds.

Menu doesn't show up though.

---

### Post by darkod on 2012-08-24
> **Wer Bn said:**
> "Found Microsoft Windows XP Professional on /dev/sda1"
Yup, it founds.

Menu doesn't show up though.

What do you mean, it boots straight into ubuntu?

When it finds more than one OS the menu is displayed automatically, unless hidden on purpose.

---

### Post by Wer Bn on 2012-08-24
Boots straight to Ubuntu.
I did nothing to hid the GRUB menu

Curious fact: 
before booting to Ubuntu, it waits in a Monitor Mode, says that my current resolution isn't apropriate.
Maybe thats the moment when the menu should show up.

---

### Post by darkod on 2012-08-24
> **Wer Bn said:**
> Boots straight to Ubuntu.
I did nothing to hid the GRUB menu

Curious fact: 
before booting to Ubuntu, it waits in a Monitor Mode, says that my current resolution isn't apropriate.
Maybe thats the moment when the menu should show up.

Yeap, I was about to ask that next. That's why it doesn't display the menu.

You can set a low resolution for the grub menu only, by booting ubuntu and opening one file for editing. In terminal try:
gksu gedit /etc/default/grub

Find the line #GRUB_GFXMODE=640x480 and remove the # symbol at the start. Save and close the file.

Run again:
sudo update-grub

Restart and see if it worked.

---

### Post by Wer Bn on 2012-08-24
Thanks mate.
I owe you one.

Next time you drop by Braga, Portugal I pay you a beer.
Cheers.

---

### Post by darkod on 2012-08-24
Psst, don't let my GF hear you. She's on my neck about Portugal for months. Well, maybe one day... soon I hope... :)

Glad you got it sorted. Please mark it Solved, you can do that in Thread Tools above the first post.

---

### Post by Wer Bn on 2012-08-24
I got a new problem... *sigh* here I was trying to get my Ubuntu niec and shinny, I installed a few packages for Gnome 3 and tried to get some new themes.

God damnit, never more...

Now, a "Prohibited" sign shows at the top of the screen (near those icons, at the top bar)
It says

"E:Type 'ain' not known in line 3 at font list /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list"

And Ubuntu software center doesn't work
Help, please

I'll change the name of the topic.

Edit: Looks like I'll have to create a new one

---

