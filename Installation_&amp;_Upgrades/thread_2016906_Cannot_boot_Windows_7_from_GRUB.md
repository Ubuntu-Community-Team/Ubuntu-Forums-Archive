---
title: "Cannot boot Windows 7 from GRUB"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by TheFlanman91 on 2012-07-04
I recently installed Ubuntu 12.04 on top of my Windows 7 32-bit machine. I used the Ubuntu installer to partition my C: drive where my Windows OS is located and installed Ubuntu. Ubuntu loads fine but now my Windows 7 won't boot through GRUB. It is visible, however whenever I try to boot it, the screen goes blank and then GRUB reappears.

I replied to a thread similar to this today but the solution found (reinstalling Windows) is not optimal for me as I have no Windows installation disc.

I think the problem may be that I installed GRUB onto my windows partition and I'm wondering where I go from here. I have already used a Windows 7 32-bit Startup Recovery Disk and used startup repair as well as trying to rebuild my BCD. This seemed to get rid of GRUB but did nothing to fix my boot loader. I then had to recover grub using a Live CD.

I have also used testdisk to try rebuild the boot loader and have got nowhere. 

Here are the results from  Boot Info Script. Hope someone can help me!


                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 456380520 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     25,167,872   422,213,023   397,045,152   7 NTFS / exFAT / HPFS
/dev/sda3         422,213,630   480,964,607    58,750,978   5 Extended
/dev/sda5         422,213,632   474,684,335    52,470,704  83 Linux
/dev/sda6         474,685,440   480,964,607     6,279,168  82 Linux swap / Solaris
/dev/sda4         480,964,608   488,394,751     7,430,144  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52284E96284E794D                       ntfs       PQSERVICE
/dev/sda2        F4CC9000CC8FBAFE                       ntfs       ACER
/dev/sda4        2E4A70284A6FEB53                       ntfs       
/dev/sda5        88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723   ext4       
/dev/sda6        04aefaeb-4be9-41ce-b99a-93f4d60ae9ff   swap       
/dev/sr0                                                udf        Repair disc Windows 7 32-bit

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
set default="5"
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
search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
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
if background_color 75,75,75; then
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
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
    linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
    echo    'Loading Linux 3.2.0-26-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 52284E96284E794D
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root F4CC9000CC8FBAFE
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2E4A70284A6FEB53
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=88d0a7c3-d0dd-4bea-b4ba-b6cfcdf4e723 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=04aefaeb-4be9-41ce-b99a-93f4d60ae9ff none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-26-generic-pae           3
               =                boot/vmlinuz-3.2.0-26-generic-pae              2
               =                initrd.img                                     3
               =                vmlinuz                                        2

================================ sda4/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  de bd d6 96 33 fb c8 4a  05 34 4a 19 15 15 04 11  |....3..J.4J.....|
00000010  f2 be 5f d0 42 55 5a 6e  4d f2 b9 78 b5 b5 0c 3a  |.._.BUZnM..x...:|
00000020  aa d5 38 ab ea 14 aa df  c4 e0 7e 72 fd 34 65 c2  |..8.......~r.4e.|
00000030  5a 8f d0 81 f9 24 fd b7  c3 ff 29 de d8 df bd 58  |Z....$....)....X|
00000040  57 86 27 54 97 fe 33 51  fa c9 e8 a2 a6 99 48 29  |W.'T..3Q......H)|
00000050  6a 51 61 30 14 f4 4d 32  fb ea cb bd bb 54 7f 8b  |jQa0..M2.....T..|
00000060  29 97 b8 b6 e3 95 ab b7  fe 12 26 0e 95 7d 5a bb  |).........&..}Z.|
00000070  2b 5a d5 89 b7 51 b8 44  bc fd 93 14 a4 b7 bb 57  |+Z...Q.D.......W|
00000080  8e e5 bf c1 df e6 8e f9  39 55 f5 1c 8d cc 22 68  |........9U...."h|
00000090  81 b5 ce 82 1e cc b4 a3  bf e7 e9 74 55 b3 7e a2  |...........tU.~.|
000000a0  ef aa 1d 9e 62 c7 81 e9  3d eb fc 1e fb de 2f 53  |....b...=...../S|
000000b0  9b 31 47 bd ff f1 81 e5  3f 2f bd 00 ed db e0 3d  |.1G.....?/.....=|
000000c0  dc 6f 2b 49 2f ac 95 d4  4b f5 b6 45 5f e4 b2 fe  |.o+I/...K..E_...|
000000d0  62 f7 6f ea 2a 42 bc 78  14 cd 4a 25 15 8f b7 37  |b.o.*B.x..J%...7|
000000e0  b0 7a 07 01 51 fd 93 51  5f 58 7e d6 fe aa 50 3e  |.z..Q..Q_X~...P>|
000000f0  25 45 25 cd 54 da 3c 7a  bf ab a5 e5 d1 4d bf 03  |%E%.T.<z.....M..|
00000100  db ff 49 79 e6 bd 93 d5  34 86 a8 eb 28 ef de 1e  |..Iy....4...(...|
00000110  2b 50 a6 c6 3d 76 ce 76  6f f2 2d 8e b8 73 0e 01  |+P..=v.vo.-..s..|
00000120  4d 3e d1 d4 b4 7d 27 e2  bf 97 36 c2 bb 2c 51 3f  |M>...}'...6..,Q?|
00000130  6c 5c 14 a4 4a d5 62 98  0a 3f 48 5d 77 dd 06 6e  |l\..J.b..?H]w..n|
00000140  66 17 97 25 54 c6 e5 23  57 54 4c b4 bb 2f 95 df  |f..%T..#WTL../..|
00000150  fb f3 e3 cd 12 b9 4b b6  33 53 12 0f c4 a1 f0 90  |......K.3S......|
00000160  3f c9 55 0e a8 41 df 7f  32 0f a4 fe f2 4e 0f 3e  |?.U..A..2....N.>|
00000170  c3 fa 77 ee 03 60 bf 2f  c2 ff ee e2 6d 6b cd 33  |..w..`./....mk.3|
00000180  aa 4b 1b 9d bf 9b ce d0  d8 c9 cd 08 5e 4c 96 37  |.K..........^L.7|
00000190  3d f9 bb eb 55 ea af c8  a0 d5 e7 1f 51 5e c1 1f  |=...U.......Q^..|
000001a0  85 eb 08 37 62 6f 40 e3  d2 de cf a0 88 5e 4b 44  |...7bo@......^KD|
000001b0  18 9b 6d 81 e8 fd 9a b8  10 48 81 e2 90 a8 00 fe  |..m......H......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 b0 a3 20 03 00 fe  |............ ...|
000001d0  ff ff 05 fe ff ff b2 a3  20 03 50 d4 5f 00 00 00  |........ .P._...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by oldfred on 2012-07-04
Added code tags to make it easier to review. You highlight the code and then click on the # in the edit panel above your message to auto add code tags.

You still have grub in sda2. All NTFS partitions have to have a NTFS pbr or partition boot sector. 

```
sda2: _____________________________________________

    File system:       ntfs
   Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 456380520 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
   Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

```Even though partition table still says it is NTFS, Windows will often not see the partition to even repair it with grub installed to the PBR.

Did you try testdisk on sda2?

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 

If not you have to use the Windows repairs to fix sda2 also, as that is your main c:.

---

### Post by TheFlanman91 on 2012-07-04
Yeah unfortunately I've been to most of those links and used testdisk on sda2. This is what I get after following the testdisk instructions. It says that my boot sector is ok and not bad? So I'm confused as to what it is reading as "ok"? Any ideas how I can remove GRUB from sda2 while leaving the Windows boot loader there? Or is what I'm saying even possible. I'm a Linux newbie btw, not only that but I haven't done a lot of dabbling in OS's before either. Thanks a mil for the help! :)

[IMG]http://i50.tinypic.com/29dx087.png[/IMG]

---

### Post by oldfred on 2012-07-04
It says it is ok because it is a valid grub boot entry, but it still is not a valid NTFS boot. You can look at the dump which compares current & backup. A Windows PBR has reference to ntldr if XP or bootmgr if Vista/7, most of it is boot related code.

Testdisk also has the Rebuild BS which will recreate a NTFS Partition Boot sector. But it is a XP type. That then let you repair it with a Windows repair CD where as long as it is grub, Window does not like it and repairs  do not seem to work.

---

### Post by TheFlanman91 on 2012-07-05
Ok so I used testdisk on sda2 to RebuildBCD and then wrote the BCD to sda2. I then used a Win7 Startup Recovery Disk and used

```
bootrec.exe /FixMbr
```

from the command prompt and ran startup repair to fix the Windows 7 boot. Now I'm booting Windows 7 but can't boot Ubuntu.. presumably because grub has been deleted or corrupted? Any ideas how to reinstall grub and what partition to install it to?

---

### Post by drs305 on 2012-07-05
Since the Windows *partition* has been repaired, you should be able to install GRUB back to the *drives's* MBR.

From a LiveCD, mount the Ubuntu partition. Do not use the partition number in the second command, only the drive letter.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
When you reboot you should see both Windows and Ubuntu items. If it only boots directly into Ubuntu, run this after it boots:
```
sudo update-grub
```
Watch the terminal output to see if Windows was located.

OR 

Just use Boot Repair > Recommended button. Link in my signature line.

---

### Post by TheFlanman91 on 2012-07-05
Excellent. Installed grub onto my ubuntu partition and everything solved. Used easyBCD to add the Windows 7 boot loader onto the MBR and added my Ubuntu boot to the boot loader. Set the grub timeout to 0 and the default boot to my Ubuntu boot to effectively get rid of having to use two boot loaders! :)

Thanks for the help!

---

### Post by drs305 on 2012-07-05
> **TheFlanman91 said:**
> Excellent. Installed grub onto my ubuntu partition and everything solved. Used easyBCD to add the Windows 7 boot loader onto the MBR and added my Ubuntu boot to the boot loader. Set the grub timeout to 0 and the default boot to my Ubuntu boot to effectively get rid of having to use two boot loaders! :)

Thanks for the help!

Glad it's now working. If you wouldn't mind please mark the therad SOLVED via the 'Thread Tools' link near the top right of the original post.

---

### Post by darkod on 2012-07-05
> **TheFlanman91 said:**
> Excellent. Installed grub onto my ubuntu partition and everything solved. Used easyBCD to add the Windows 7 boot loader onto the MBR and added my Ubuntu boot to the boot loader. Set the grub timeout to 0 and the default boot to my Ubuntu boot to effectively get rid of having to use two boot loaders! :)

Thanks for the help!

Just a note, if you installed grub2 to the MBR you would have one bootloader also. In fact that's the preferred way to use it since grub2 doesn't fit onto a partition, it needs to be installed by forcing it with -f, and it can break during some updates later.

Unless you have a really valid reason to keep windows bootloader on the MBR, this solution is not really preferred.

---

