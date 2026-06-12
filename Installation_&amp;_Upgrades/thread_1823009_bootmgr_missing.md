---
title: "bootmgr missing"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by MisterLopez on 2011-08-11
Hi,

I previously had one hard disk (250GB), with both windows xp and Ubuntu 10 running fine.
I bought a new hard disk (1000GB) and without deleting anything from the previous one, and having both connected, I installed in the new hard disk: windows xp and ubuntu 11, in the following order:

1) Installed windows xp in a new 120GB partition
2) Installed Ubuntu 11 using the rest of the hard disk (using 3 partitions: swap, /, /home)
3)Formated the old hard disk to ntfs.

My problem:
After formatting the 250GB disk, the Windows option in the grub stopped working, and after trying to solve the problem by updating the grub, the option just dissapeared (looks like Ubuntu doesn't know that the first partition in the 1TB disk is an OS. So I added a new line in the startup menu list from the grub following the instructions in someones post:

```

{
menuentry "Windows XP" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd1,msdos1)'
drivemap -s (hd1) ${root}
chainloader +1
}  

```

and when I select it during the start up it says: BOOTMGR missing.

What can I do?

I'm attaching here the results given by "Boot Info Script", hope it helps:

```

    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   488,396,799   488,394,752   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   245,762,369   245,762,307   7 NTFS / exFAT / HPFS
/dev/sdb2         245,764,096   253,575,167     7,811,072  82 Linux swap / Solaris
/dev/sdb3    *    253,575,168   292,636,671    39,061,504  83 Linux
/dev/sdb4         292,636,672 1,953,523,711 1,660,887,040  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        596C3F6F7C24DBCA                       ntfs       Esclavo
/dev/sdb1        649844F19844C372                       ntfs       
/dev/sdb2        afe8c572-bcfb-4e28-a8f7-9128c5f21398   swap       
/dev/sdb3        fddc0743-3020-4c36-9c2a-ac99a29c26f3   ext4       
/dev/sdb4        82231d2b-d8ad-4c87-849f-2d257fe44d95   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb4        /home                    ext4       (rw,commit=0)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
set locale_dir=($root)/boot/grub/locale
set lang=es_ES
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
menuentry 'Ubuntu, con Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=fddc0743-3020-4c36-9c2a-ac99a29c26f3 ro  vga=792  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-10-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=fddc0743-3020-4c36-9c2a-ac99a29c26f3 ro single  vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fddc0743-3020-4c36-9c2a-ac99a29c26f3 ro  vga=792  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fddc0743-3020-4c36-9c2a-ac99a29c26f3 ro single  vga=792
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
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root fddc0743-3020-4c36-9c2a-ac99a29c26f3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
{
menuentry "Windows XP" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd1,msdos1)'
drivemap -s (hd1) ${root}
chainloader +1
} 
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=fddc0743-3020-4c36-9c2a-ac99a29c26f3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=82231d2b-d8ad-4c87-849f-2d257fe44d95 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=5c957866-9122-4380-8f1f-a5183bd9f08e none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=afe8c572-bcfb-4e28-a8f7-9128c5f21398 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 129.231910706 = 138.761707520  boot/grub/core.img                             1
 137.378967285 = 147.509542912  boot/grub/grub.cfg                             1
 137.444316864 = 147.579711488  boot/initrd.img-2.6.38-10-generic              2
 122.250000000 = 131.264937984  boot/initrd.img-2.6.38-8-generic               2
 122.387027740 = 131.412070400  boot/vmlinuz-2.6.38-10-generic                 2
 129.230773926 = 138.760486912  boot/vmlinuz-2.6.38-8-generic                  1
 137.444316864 = 147.579711488  initrd.img                                     2
 122.250000000 = 131.264937984  initrd.img.old                                 2
 122.387027740 = 131.412070400  vmlinuz                                        2
 129.230773926 = 138.760486912  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by oldfred on 2011-08-12
When you installed windows to your new drive, you still had the old install connected. Windows is only capable of booting from one active partition (boot flag) and even when two drives are involved it litterally copies the boot files from the second install into the first install to boot from. So you deleted the boot files when you reformated the old drive. You can repair by adding the missing files back.

If you want to know a little about how windows works (and MBR systems in general, but grub does not use PBR). 
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Windows only sees the active partition for repairs also. Grub does not use boot flag, so you have to move boot flag to NTFS primary partition with your windows install for repairs to work. you can use gparted, Disk Utility, or command line to move flag:

set boot flag on for sdb1 (off for others)
sudo sfdisk -A1 /dev/sdb

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by MisterLopez on 2011-08-14
Thank you very much for your help!

Unfortunately it just looked to complicated for me to do, so I ended up reintalling both systems again. This time with just one hard disk connected when installing Windows, and then both when installing Ubuntu. Everything works fine now. Thanks again for your help. :)

---

