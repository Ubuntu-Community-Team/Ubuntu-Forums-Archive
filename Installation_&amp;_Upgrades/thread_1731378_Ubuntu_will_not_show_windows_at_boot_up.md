---
title: "Ubuntu will not show windows at boot up"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by charlesbw on 2011-04-17
I installed windows 7 and then installed ubuntu and I chose the option to install along side other operating systems, but I don't see an option to load into windows when ever I start up my system.  Anyone know how I can correct this?  Both are on two separate hard drives, I just want to be able to load into windows for my iphone to back it up into itunes.  Any help is greatly appreciated.

---

### Post by coffeecat on 2011-04-17
Did you use the 10.10 install CD? The "install alongside" option has a nasty design flaw that can mislead the user into inadvertently telling the installer to overwrite the Windows partition. Let's hope not in your case. 

So that we can see exactly what is on your system, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file. Please be sure to enclose the text between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by charlesbw on 2011-04-17
that site is down, it can't overwrite a partition thats not on the same hard drive can it?

---

### Post by thecamelcoder on 2011-04-17
Hey mate, 

what you can do is boot into the LiveCd and capture the output from ```
sudo fdisk -l >partitions.txt
```

Partitions.txt will contain a list of all drives and their paritions. 

From here we should be able to help further. 

The option is that you could rebuild the MBR - Master Boot Record for Windows which should allow you to get back into your Win7 system. 

Link is here if your interested: [http://www.linux-geek.co.nz/2011/04/17/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.linux-geek.co.nz/2011/04/17/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Let me know if I can help anymore. 
):P

---

### Post by charlesbw on 2011-04-17
Here it is, as you can see the second drive is my windows
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fcf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119371   958845952   83  Linux
/dev/sda2          119372      121602    17913857    5  Extended
/dev/sda5          119372      121602    17913856   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79847984

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x676d3178

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS
```

---

### Post by coffeecat on 2011-04-17
> **charlesbw said:**
> that site is down

It's working for me. Try again. We need the output from the boot script to see what is in the boot sector of your Windows partition(s), among other things. fdisk doesn't give this.

---

### Post by charlesbw on 2011-04-17
It worked, here it is.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,917,693,951 1,917,691,904  83 Linux
/dev/sda2       1,917,695,998 1,953,523,711    35,827,714   5 Extended
/dev/sda5       1,917,696,000 1,953,523,711    35,827,712  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7dd765f2-ecc0-4d0a-923f-753d5140ce30   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        26ca3f2c-5266-4c33-afc7-a620a5b2f8d6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EC3881A338816D80                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B8A4A211A4A1D1E4                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/B8A4A211A4A1D1E4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7dd765f2-ecc0-4d0a-923f-753d5140ce30 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7dd765f2-ecc0-4d0a-923f-753d5140ce30 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7dd765f2-ecc0-4d0a-923f-753d5140ce30
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=26ca3f2c-5266-4c33-afc7-a620a5b2f8d6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 244.9GB: boot/grub/core.img
 223.4GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
 244.9GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
 244.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c2 77 a5 88 59 40 64 44  d6 07 91 80 1c 68 16 8a  |.w..Y@dD.....h..|
00000010  06 a8 b0 75 30 b8 82 ee  80 e1 1d 88 ba 98 2f 59  |...u0........./Y|
00000020  62 ae 02 98 95 62 d0 a5  30 15 4b a2 c1 5a 75 a5  |b....b..0.K..Zu.|
00000030  79 c1 14 d6 06 e3 5c 11  8a 18 1a e3 00 34 29 cf  |y.....\......4).|
00000040  bc e1 60 5f 8c e9 67 39  a0 a5 5c 18 52 cc 5d a0  |..`_..g9..\.R.].|
00000050  2c 62 83 8b 46 c4 b8 42  79 0a d6 0c 0f 88 2c 05  |,b..F..By.....,.|
00000060  cd d7 d6 9c 14 b6 0f 2f  ff d8 d7 a8 b6 32 d9 b1  |......./.....2..|
00000070  59 bc 91 c2 3c 25 01 4c  22 15 3b b9 48 42 87 71  |Y...<%.L".;.HB.q|
00000080  38 85 46 f8 64 9d 73 62  70 a7 7c 10 7a 81 c9 12  |8.F.d.sbp.|.z...|
00000090  36 d9 02 5c cd 6f a1 82  62 7e d5 cd f0 d8 52 5a  |6..\.o..b~....RZ|
000000a0  60 61 7a e8 c8 59 a1 31  09 10 9f 04 fa 5b 7a d9  |`az..Y.1.....[z.|
000000b0  c2 56 33 37 4e b6 c1 0c  4d 9f 7a 76 7b 0f 6f 60  |.V37N...M.zv{.o`|
000000c0  d1 a3 82 1d 04 8b 13 a7  6c 50 03 11 58 8e 0c 1d  |........lP..X...|
000000d0  9a 23 3c 9d 8d c0 99 39  d8 09 e1 28 89 a2 5c 98  |.#<....9...(..\.|
000000e0  90 57 75 e2 e9 c2 5d 60  79 18 01 c8 41 11 b2 66  |.Wu...]`y...A..f|
000000f0  cc 27 c6 6e 8d 46 c6 50  a3 22 16 8c f4 29 48 02  |.'.n.F.P."...)H.|
00000100  36 c6 18 6d e2 3a d1 b8  0e 6f 01 83 08 9c 62 94  |6..m.:...o....b.|
00000110  2c d6 88 04 7e b4 39 4a  69 2b c9 96 0f 4d 1e 19  |,...~.9Ji+...M..|
00000120  ec 85 e8 81 86 fc 30 15  e8 18 01 f5 e2 f7 ab 49  |......0........I|
00000130  91 6e 03 0b d0 33 ab 20  27 11 d6 88 89 1b 11 06  |.n...3. '.......|
00000140  92 41 d2 72 c4 44 da 54  e0 58 74 e2 4c 9c 6e 04  |.A.r.D.T.Xt.L.n.|
00000150  dc b8 7e b6 8a 97 c1 d7  05 d4 0c b2 32 11 e1 d0  |..~.........2...|
00000160  3e 1c 00 e1 20 74 d0 d3  83 ad 10 86 95 80 cc 47  |>... t.........G|
00000170  69 c2 78 90 41 4e 4c b0  27 27 0f 92 93 b8 47 c2  |i.x.ANL.''....G.|
00000180  a0 55 21 36 90 ad 10 d7  8c e8 b0 13 8f 08 fa 5a  |.U!6...........Z|
00000190  b6 8b ba d8 82 04 89 35  00 6e 60 72 c3 23 52 61  |.......5.n`r.#Ra|
000001a0  07 b8 88 f2 bf a2 aa 3d  af a7 d2 f3 ad 13 ba 80  |.......=........|
000001b0  b4 5a 7a 16 bb 1b ac 0d  dc 9f ac 09 90 87 00 fe  |.Zz.............|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 22 02 00 00  |............"...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by coffeecat on 2011-04-17
This:

```

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

```You are missing some Windows boot files in your Windows sdb1 partition. Compare with mine:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM
```Ignore the /ntldr and /NTDETECT.COM - mine was an upgrade from XP and those are unused residual files from XP. The important Win7 files/folders missing from yours are  /bootmgr and /Boot/BCD. Did you originally have a separate small (about 100MB) partition on sda1? If you did, this might have been a separate Windows 7 boot partition with those files. Win7 doesn't need a separate boot partition but will create one on installation if you let it. Whatever, grub (through os-prober) is probably failing to detect the presence of Windows because of those missing files.

Also - the boot flag is not set on sdb1.

You need a Windows 7 repair disc or the Microsoft installation DVD. If you have neither, you can download the repair disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Once you've booted up with a repair disc, you can choose "Startup repair" as seen in the first screenshot here:

[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

Be careful with that option. It *might* repair the mbr on sda as well which will mean you won't be able to boot into Ubuntu until you re-install grub.

Alternatively, choose "Command Prompt" and have a look at this page for using bootrec:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

'bootrec /FixBoot' would be the one I would choose in this situation. Again, don't use 'bootrec /FixMbr' for the reason I explained above.

Once you have - hopefully - repaired the Windows partition boot sector, boot into Ubuntu and run:

```
sudo update-grub
```If that doesn’t work, run the boot script again and we'll take it from there.

---

### Post by charlesbw on 2011-04-18
Thanks yall its fixed, I tried your suggestions and it kept telling me that nothing that even resembled a window mbr is available.  I figured that no matter what route I went, windows will always create its boot partition in the same hard drive am installing ubuntu. So I cleaned both hd's and and unplugged the ubuntu hd before I installed windows, so windows had to do everything on the hd i gave it.  After that I plugged the ubuntu hd back in and installed ubuntu.  Am going to check the windows install and see if its stable.  Hopefully it being listed during boot means that all my troubles are over.  Thanks for all the suggestions.

---

