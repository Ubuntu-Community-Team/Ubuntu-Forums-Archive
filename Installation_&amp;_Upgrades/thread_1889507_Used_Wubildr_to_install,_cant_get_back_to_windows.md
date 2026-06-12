---
title: "Used Wubildr to install, cant get back to windows"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by Matt51723 on 2011-12-01
I downloaded wubildr from ubuntu.com , did the installation and all that, then I restarted my computer and it booted Ubuntu, but now I  can't figure out how to go back to windows.

Every time I restart my computer it doesn't give me an option to select  which operating system I want to boot. It just goes straight to Ubuntu. (It doesn't show grub)

How can I get back to Windows?

---

### Post by BC59 on 2011-12-01
Are you sure you installed Ubuntu through wubi?

Can you execute on a terminal those 2 commands and post them to the forum? 

```
sudo parted /dev/sda print
``` 


```
sudo fdisk -l
```

---

### Post by Matt51723 on 2011-12-01
matt@ubuntu:~$ sudo parted /dev/sda print
[sudo] password for matt: 
Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   734GB  734GB   primary  ntfs
 3      734GB   750GB  15.6GB  primary  ntfs
 4      750GB   750GB  108MB   primary  fat32        lba

matt@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1a3f0dfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1434458111   717024256    7  HPFS/NTFS/exFAT
/dev/sda3      1434458112  1464936447    15239168    7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)

---

### Post by BC59 on 2011-12-01
Ok looks like Windows is induct.

Now through Ubuntu go to your Windows C:\ and rename the C:\wubildr file on the root directory. Rename it to something like wubildr2. Then boot and hopefully you will get to Windows.

---

### Post by bcbc on 2011-12-01
No don't do that. Then you won't boot anything.

Are you running XP or Vista/7?

Maybe also post the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by Matt51723 on 2011-12-01
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub4Dos is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600 1,434,458,111 1,434,048,512   7 NTFS / exFAT / HPFS
/dev/sda3       1,434,458,112 1,464,936,447    30,478,336   7 NTFS / exFAT / HPFS
/dev/sda4       1,464,936,448 1,465,147,119       210,672   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       e4635099-89df-4538-8a43-cefac4a53b3b   ext3       
/dev/sda1        A6A6F9F8A6F9C8B7                       ntfs       SYSTEM
/dev/sda2        FCA08950A0891276                       ntfs       
/dev/sda3        6080234D8023294C                       ntfs       RECOVERY
/dev/sda4        48D5-69CF                              vfat       HP_TOOLS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext3       (rw,commit=600,commit=600)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root FCA08950A0891276
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root FCA08950A0891276
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root FCA08950A0891276
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=FCA08950A0891276 loop=/ubuntu/disks/root.disk ro  splash vga=796  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root FCA08950A0891276
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=FCA08950A0891276 loop=/ubuntu/disks/root.disk ro single  splash vga=796
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              71
               =                boot/vmlinuz-3.0.0-12-generic                 20
               =                initrd.img                                    71
               =                vmlinuz                                       20

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 d2 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 51 57  |........?....(QW|
00000020  f0 36 03 00 17 03 00 00  00 00 00 00 02 00 00 00  |.6..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 cf 69 d5 48 4e  4f 20 4e 41 4d 45 20 20  |..).i.HNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by bcbc on 2011-12-01
How did you get grub4dos in your drive MBR? Please explain in detail how you installed Wubi because that's not supposed to happen. If you just ran the normal way by running wubi.exe you should [file a bug]("http://bugs.launchpad.net/wubi/+filebug") and attach the bootinfoscript result to it.

The quickest fix is to reinstall the windows bootloader which you can either do from a Windows 7 repair CD or right from Ubuntu if you don't have a repair CD.

Win7 repair CD:
Boot to a repair prompt and run: ```
bootrec /fixmbr
```

From Ubuntu (ignore the warning after the first command - that's not an issue for using lilo like a windows bootloader):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by bcbc on 2011-12-01
Hold on your boot flag is set on /dev/sda1. I think it probably should be on /dev/sda2.

Maybe just first explain what you've done before replacing the bootloader.

---

### Post by Matt51723 on 2011-12-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libo

It won't locate the package for libo

---

### Post by bcbc on 2011-12-01
See my previous post. More information required first, and then you can try the fix afterwards.

---

### Post by Matt51723 on 2011-12-01
This is what I did:
[http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)

I have the files that wublidr made or whatever on my C: drive and on an external, currently the external is not connected however.

---

### Post by bcbc on 2011-12-01
Okay unfortunately you installed the grub4dos on your laptop's hard drive MBR, not the USB. (No need to file a bug on this one)

So proceed with that fix I mentioned. (It's lilo, not libo). And since Ubuntu is case sensitive it very important that you type the commands carefully or copy and paste (to paste to the terminal use Ctrl+Shift+V).

PS you could always [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") a wubi install to the usb drive as a native install. You just have to create an ext4 partition on the USB first (and a swap partition if you want it).

---

### Post by Matt51723 on 2011-12-01
I did that fix (lilo), now when I reboot it should work?

---

### Post by bcbc on 2011-12-01
Yes. I had a look at some other HP bootinfoscripts and it looks like the boot flag is okay on /dev/sda1. And it's unlikely you changed it with those instructions. So you should be okay.

PS once you reboot into Windows, create a repair CD (always a good idea in case you run into problems more complex than the bootloader).

---

### Post by Matt51723 on 2011-12-01
Awesome it worked, is there a way to dual boot seamlessly from an external hard drive? Because thats what I initially tried doing and kinda screwed up lol.

---

### Post by bcbc on 2011-12-01
Yes, as I said (in post 12) you can migrate the wubi to an external - the script will install the bootloader on the external only - and then when you want Ubuntu, you hit the F12 key at startup (or whatever your BIOS boot options key is) and tell it to boot from the USB.

You can also install fresh to an external, just make sure you tell the Ubuntu installer to install the Grub2 bootloader to the external only.

---

