---
title: "Just installed ubuntu 10.4 now can't open windows or ubuntu"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by andyjimfrank on 2011-07-18
Hey, completely new to ubuntu.  Just installed 10.4 to my netbook.  The first time I booted up after installation it seemed to work fine when I entered into ubuntu.  However, when I restarted my computer and tried to go back into windows it took me to a recovery center.  I didn't want that and just restarted the computer.

Now I can't use either OS.  Every time I turn on the computer, it seems to be on a loop.  It starts, then restarts over and over again.  What did I do wrong?  Did I just ruin my computer?

---

### Post by lmarmisa on 2011-07-18
> **andyjimfrank said:**
> Hey, completely new to ubuntu.  Just installed 10.4 to my netbook.  The first time I booted up after installation it seemed to work fine when I entered into ubuntu.  However, when I restarted my computer and tried to go back into windows it took me to a recovery center.  I didn't want that and just restarted the computer.

Now I can't use either OS.  Every time I turn on the computer, it seems to be on a loop.  It starts, then restarts over and over again.  What did I do wrong?  Did I just ruin my computer?

Welcome to the forums.

Boot into an Ubuntu Live CD / USB, Try Ubuntu, open Firefox and go to the web page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then follow the instructions of that page in order to download and run the boot info script.

Finally post the results in this thread.

Best regards,

Luis

---

### Post by andyjimfrank on 2011-07-18
Hey there, did as you said (or at least I hope I followed the directions correctly) and I now have this:

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 129472 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   204,944,403   173,280,276   7 NTFS / exFAT / HPFS
/dev/sda4         204,945,406   312,580,095   107,634,690   5 Extended
/dev/sda5         204,945,408   308,090,879   103,145,472  83 Linux
/dev/sda6         308,092,928   312,580,095     4,487,168  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000 MB, 2000683008 bytes
16 heads, 32 sectors/track, 7632 cylinders, total 3907584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     3,907,583     3,899,520   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        169E0F619E0F392F                       ntfs       RECOVERY
/dev/sda2        68C010B4C0108B08                       ntfs       SYSTEM
/dev/sda3        D85A12C35A129DF6                       ntfs       
/dev/sda5        d47bd047-f772-466c-894b-6beec418730c   ext4       
/dev/sda6        4da7e5ce-acad-4408-9f8d-305b58d5530e   swap       
/dev/sdb1        EFB1-CB71                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d47bd047-f772-466c-894b-6beec418730c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d47bd047-f772-466c-894b-6beec418730c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 169e0f619e0f392f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 68c010b4c0108b08
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d47bd047-f772-466c-894b-6beec418730c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4da7e5ce-acad-4408-9f8d-305b58d5530e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 105.869209290 = 113.676197888  boot/grub/core.img                             1
 123.877006531 = 133.011922944  boot/grub/grub.cfg                             1
 105.876632690 = 113.684168704  boot/initrd.img-2.6.32-28-generic              1
 105.867809296 = 113.674694656  boot/vmlinuz-2.6.32-28-generic                 1
 105.876632690 = 113.684168704  initrd.img                                     1
 105.867809296 = 113.674694656  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  6a 31 e1 90 73 99 a1 80  02 a4 40 4e 86 9f 0e ef  |j1..s.....@N....|
00000010  98 10 12 3e 94 0e ab 90  28 39 31 05 1c 38 87 e1  |...>....(91..8..|
00000020  92 04 91 92 47 99 b6 6e  c2 bb d4 76 b6 32 da 3a  |....G..n...v.2.:|
00000030  92 88 85 e9 2c bb e8 22  73 b8 cb 30 b9 93 a6 ed  |....,.."s..0....|
00000040  38 8f 75 5a 07 de 65 a4  c2 98 74 1f 2d ee 74 b3  |8.uZ..e...t.-.t.|
00000050  99 7d 2f 9e 70 48 78 7a  0d 87 03 aa 60 91 36 ff  |.}/.pHxz....`.6.|
00000060  ff fe 66 76 e2 27 f7 47  3d 7a 30 c1 df 12 83 04  |..fv.'.G=z0.....|
00000070  82 20 d8 91 71 11 05 85  c4 25 0e 51 9a cc d9 9e  |. ..q....%.Q....|
00000080  7f a4 e7 ae 65 e3 9e 21  7e 9a 87 3d c4 bc 43 88  |....e..!~..=..C.|
00000090  4f 51 ff ff ff ff ff fb  16 a0 82 c3 99 45 20 29  |OQ...........E )|
000000a0  41 0f 45 5b 2e a3 4c a0  78 91 91 36 48 58 e9 8d  |A.E[..L.x..6HX..|
000000b0  01 02 22 20 5b 78 a0 39  ae 80 72 54 29 d7 6f 69  |.." [x.9..rT).oi|
000000c0  ed 3e 91 1b d6 61 9b bc  97 e5 67 97 a6 e7 2f d4  |.>...a....g.../.|
000000d0  d7 31 97 58 f9 63 73 72  a1 d7 1a 9e 48 ed c4 d9  |.1.X.csr....H...|
000000e0  cc 69 ca 81 e9 7f 3b 33  99 7d 2f 93 38 70 64 52  |.i....;3.}/.8pdR|
000000f0  23 0e 8a 44 e4 02 06 ff  fa aa 9e f4 af 53 0f 26  |#..D.........S.&|
00000100  6e 61 8d cf 34 4c 28 18  1d 30 a9 71 68 d4 34 23  |na..4L(..0.qh.4#|
00000110  8d 8d 14 98 71 ce 5a 87  1e bd 8c ed 55 3d 2b 44  |....q.Z.....U=+D|
00000120  6d 8e 66 57 49 e8 87 89  8f ff ff ff a0 f9 a0 4f  |m.fWI..........O|
00000130  42 a6 23 16 d4 ca ac 3f  6c 93 5c b7 40 a8 e0 21  |B.#....?l.\.@..!|
00000140  e9 dc 60 0e cb 0d 0a 54  d8 82 21 25 53 97 92 91  |..`....T..!%S...|
00000150  26 68 61 13 f8 26 74 a3  b2 3b f6 60 ed 3d 12 9b  |&ha..&t..;.`.=..|
00000160  75 6b ea a4 63 9d a3 ab  62 14 f2 47 5a 43 d5 7a  |uk..c...b..GZC.z|
00000170  4e f3 b3 a6 5a f3 53 47  65 32 18 fe 34 94 f5 f0  |N...Z.SGe2..4...|
00000180  b3 a0 84 84 40 e3 c3 e1  0c 4c 91 5f ff ff ff cb  |....@....L._....|
00000190  0f e1 23 8d 50 7b a8 84  43 dc 7e 68 a0 a1 58 35  |..#.P{..C.~h..X5|
000001a0  34 80 80 d1 1c 9b 52 c5  b8 6e 9b 99 eb 7c a9 8f  |4.....R..n...|..|
000001b0  bf d9 25 65 5e f4 a6 8b  da 31 b1 4e bf ff 00 fe  |..%e^....1.N....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 25 06 00 fe  |............%...|
000001d0  ff ff 05 fe ff ff 02 e0  25 06 00 80 44 00 00 00  |........%...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by andyjimfrank on 2011-07-18
Here it is.  Any idea on what I should do next?

```

```Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 129472 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   204,944,403   173,280,276   7 NTFS / exFAT / HPFS
/dev/sda4         204,945,406   312,580,095   107,634,690   5 Extended
/dev/sda5         204,945,408   308,090,879   103,145,472  83 Linux
/dev/sda6         308,092,928   312,580,095     4,487,168  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000 MB, 2000683008 bytes
16 heads, 32 sectors/track, 7632 cylinders, total 3907584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     3,907,583     3,899,520   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        169E0F619E0F392F                       ntfs       RECOVERY
/dev/sda2        68C010B4C0108B08                       ntfs       SYSTEM
/dev/sda3        D85A12C35A129DF6                       ntfs       
/dev/sda5        d47bd047-f772-466c-894b-6beec418730c   ext4       
/dev/sda6        4da7e5ce-acad-4408-9f8d-305b58d5530e   swap       
/dev/sdb1        EFB1-CB71                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d47bd047-f772-466c-894b-6beec418730c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d47bd047-f772-466c-894b-6beec418730c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d47bd047-f772-466c-894b-6beec418730c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 169e0f619e0f392f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 68c010b4c0108b08
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d47bd047-f772-466c-894b-6beec418730c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4da7e5ce-acad-4408-9f8d-305b58d5530e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 105.869209290 = 113.676197888  boot/grub/core.img                             1
 123.877006531 = 133.011922944  boot/grub/grub.cfg                             1
 105.876632690 = 113.684168704  boot/initrd.img-2.6.32-28-generic              1
 105.867809296 = 113.674694656  boot/vmlinuz-2.6.32-28-generic                 1
 105.876632690 = 113.684168704  initrd.img                                     1
 105.867809296 = 113.674694656  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  6a 31 e1 90 73 99 a1 80  02 a4 40 4e 86 9f 0e ef  |j1..s.....@N....|
00000010  98 10 12 3e 94 0e ab 90  28 39 31 05 1c 38 87 e1  |...>....(91..8..|
00000020  92 04 91 92 47 99 b6 6e  c2 bb d4 76 b6 32 da 3a  |....G..n...v.2.:|
00000030  92 88 85 e9 2c bb e8 22  73 b8 cb 30 b9 93 a6 ed  |....,.."s..0....|
00000040  38 8f 75 5a 07 de 65 a4  c2 98 74 1f 2d ee 74 b3  |8.uZ..e...t.-.t.|
00000050  99 7d 2f 9e 70 48 78 7a  0d 87 03 aa 60 91 36 ff  |.}/.pHxz....`.6.|
00000060  ff fe 66 76 e2 27 f7 47  3d 7a 30 c1 df 12 83 04  |..fv.'.G=z0.....|
00000070  82 20 d8 91 71 11 05 85  c4 25 0e 51 9a cc d9 9e  |. ..q....%.Q....|
00000080  7f a4 e7 ae 65 e3 9e 21  7e 9a 87 3d c4 bc 43 88  |....e..!~..=..C.|
00000090  4f 51 ff ff ff ff ff fb  16 a0 82 c3 99 45 20 29  |OQ...........E )|
000000a0  41 0f 45 5b 2e a3 4c a0  78 91 91 36 48 58 e9 8d  |A.E[..L.x..6HX..|
000000b0  01 02 22 20 5b 78 a0 39  ae 80 72 54 29 d7 6f 69  |.." [x.9..rT).oi|
000000c0  ed 3e 91 1b d6 61 9b bc  97 e5 67 97 a6 e7 2f d4  |.>...a....g.../.|
000000d0  d7 31 97 58 f9 63 73 72  a1 d7 1a 9e 48 ed c4 d9  |.1.X.csr....H...|
000000e0  cc 69 ca 81 e9 7f 3b 33  99 7d 2f 93 38 70 64 52  |.i....;3.}/.8pdR|
000000f0  23 0e 8a 44 e4 02 06 ff  fa aa 9e f4 af 53 0f 26  |#..D.........S.&|
00000100  6e 61 8d cf 34 4c 28 18  1d 30 a9 71 68 d4 34 23  |na..4L(..0.qh.4#|
00000110  8d 8d 14 98 71 ce 5a 87  1e bd 8c ed 55 3d 2b 44  |....q.Z.....U=+D|
00000120  6d 8e 66 57 49 e8 87 89  8f ff ff ff a0 f9 a0 4f  |m.fWI..........O|
00000130  42 a6 23 16 d4 ca ac 3f  6c 93 5c b7 40 a8 e0 21  |B.#....?l.\.@..!|
00000140  e9 dc 60 0e cb 0d 0a 54  d8 82 21 25 53 97 92 91  |..`....T..!%S...|
00000150  26 68 61 13 f8 26 74 a3  b2 3b f6 60 ed 3d 12 9b  |&ha..&t..;.`.=..|
00000160  75 6b ea a4 63 9d a3 ab  62 14 f2 47 5a 43 d5 7a  |uk..c...b..GZC.z|
00000170  4e f3 b3 a6 5a f3 53 47  65 32 18 fe 34 94 f5 f0  |N...Z.SGe2..4...|
00000180  b3 a0 84 84 40 e3 c3 e1  0c 4c 91 5f ff ff ff cb  |....@....L._....|
00000190  0f e1 23 8d 50 7b a8 84  43 dc 7e 68 a0 a1 58 35  |..#.P{..C.~h..X5|
000001a0  34 80 80 d1 1c 9b 52 c5  b8 6e 9b 99 eb 7c a9 8f  |4.....R..n...|..|
000001b0  bf d9 25 65 5e f4 a6 8b  da 31 b1 4e bf ff 00 fe  |..%e^....1.N....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 25 06 00 fe  |............%...|
000001d0  ff ff 05 fe ff ff 02 e0  25 06 00 80 44 00 00 00  |........%...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by lmarmisa on 2011-07-18
The results seem not too bad. :D

I recommend to reinstall grub following this procedure:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Boot into an Ubuntu Live CD / USB, open a terminal and type:

```

sudo mount /dev/sda5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/usr
sudo umount /mnt
sudo reboot

```

Remove the Ubuntu Live CD / USB before the reboot.

---

### Post by andyjimfrank on 2011-07-18
Luis you have saved my life.  Things are working again.  Thank you thank you thank you!!!

---

### Post by lmarmisa on 2011-07-18
> **andyjimfrank said:**
> Luis you have saved my life.  Things are working again.  Thank you thank you thank you!!!

You are very welcome. :D

It has been a pleasure to help you.

Best regards,

Luis

---

