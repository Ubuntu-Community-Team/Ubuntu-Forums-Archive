---
title: "No boot menu after installing ubuntu"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by elticat on 2011-05-02
I have a laptop which I just recently installed Windows 7 on.  Then I got Ubuntu 11.04, ran the installer, resized the disk, and everything looked fine.  But when the installation finishes and I reboot, it loads straight back into windows without any kind of boot menu.  I've never had this problem before, and have previously run Windows 7 and Debian on this same machine.  Any ideas?

---

### Post by wilee-nilee on 2011-05-02
> **elticat said:**
> I have a laptop which I just recently installed Windows 7 on.  Then I got Ubuntu 11.04, ran the installer, resized the disk, and everything looked fine.  But when the installation finishes and I reboot, it loads straight back into windows without any kind of boot menu.  I've never had this problem before, and have previously run Windows 7 and Debian on this same machine.  Any ideas?

Yeah so from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a lot of information.

---

### Post by elticat on 2011-05-02
This is what it says:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   254,673,064   254,466,217   7 HPFS/NTFS
/dev/sda3         254,674,942   488,396,799   233,721,858   5 Extended
/dev/sda5         480,077,824   488,396,799     8,318,976  82 Linux swap / Solaris
/dev/sda6         254,674,944   471,756,799   217,081,856  83 Linux
/dev/sda7         471,758,848   480,069,631     8,310,784  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,913,663     3,913,601   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   FC30-3DA9                              vfat                                     
/dev/sda1        3228B70428B6C5DF                       ntfs       System Reserved               
/dev/sda2        6A5CBA075CB9CDD7                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        08246ef9-0a50-47f2-b5f1-8edfff9466f4   swap                                     
/dev/sda6        b0d4b436-0550-4c11-9486-9f85570e3d82   ext4                                     
/dev/sda7        06f5ab6a-48ad-40d8-b1e1-1a6e33684307   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        82CF-FFC0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/FC30-3DA9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b0d4b436-0550-4c11-9486-9f85570e3d82 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b0d4b436-0550-4c11-9486-9f85570e3d82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b0d4b436-0550-4c11-9486-9f85570e3d82
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3228B70428B6C5DF
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b0d4b436-0550-4c11-9486-9f85570e3d82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=08246ef9-0a50-47f2-b5f1-8edfff9466f4 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=06f5ab6a-48ad-40d8-b1e1-1a6e33684307 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 199.3GB: boot/grub/core.img
 164.9GB: boot/grub/grub.cfg
 131.7GB: boot/initrd.img-2.6.38-8-generic-pae
 131.0GB: boot/vmlinuz-2.6.38-8-generic-pae
 131.7GB: initrd.img
 131.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  36 2e 34 38 20 35 36 37  20 35 35 38 2e 34 38 5d  |6.48 567 558.48]|
00000010  2f 53 75 62 74 79 70 65  2f 4c 69 6e 6b 2f 41 3c  |/Subtype/Link/A<|
00000020  3c 2f 44 28 47 37 2e 31  37 33 37 38 36 34 29 2f  |</D(G7.1737864)/|
00000030  53 2f 47 6f 54 6f 3e 3e  2f 42 6f 72 64 65 72 5b  |S/GoTo>>/Border[|
00000040  30 20 30 20 30 5d 2f 54  79 70 65 2f 41 6e 6e 6f  |0 0 0]/Type/Anno|
00000050  74 3e 3e 0d 65 6e 64 6f  62 6a 0d 31 34 31 36 20  |t>>.endobj.1416 |
00000060  30 20 6f 62 6a 3c 3c 2f  52 65 63 74 5b 34 35 20  |0 obj<</Rect[45 |
00000070  35 33 33 2e 34 36 20 35  36 37 20 35 34 35 2e 34  |533.46 567 545.4|
00000080  36 5d 2f 53 75 62 74 79  70 65 2f 4c 69 6e 6b 2f  |6]/Subtype/Link/|
00000090  41 3c 3c 2f 44 28 47 37  2e 31 37 33 37 38 35 38  |A<</D(G7.1737858|
000000a0  29 2f 53 2f 47 6f 54 6f  3e 3e 2f 42 6f 72 64 65  |)/S/GoTo>>/Borde|
000000b0  72 5b 30 20 30 20 30 5d  2f 54 79 70 65 2f 41 6e  |r[0 0 0]/Type/An|
000000c0  6e 6f 74 3e 3e 0d 65 6e  64 6f 62 6a 0d 31 34 31  |not>>.endobj.141|
000000d0  37 20 30 20 6f 62 6a 3c  3c 2f 52 65 63 74 5b 34  |7 0 obj<</Rect[4|
000000e0  35 20 35 32 30 2e 35 20  35 36 37 20 35 33 32 2e  |5 520.5 567 532.|
000000f0  35 5d 2f 53 75 62 74 79  70 65 2f 4c 69 6e 6b 2f  |5]/Subtype/Link/|
00000100  41 3c 3c 2f 44 28 47 37  2e 31 37 33 37 38 35 32  |A<</D(G7.1737852|
00000110  29 2f 53 2f 47 6f 54 6f  3e 3e 2f 42 6f 72 64 65  |)/S/GoTo>>/Borde|
00000120  72 5b 30 20 30 20 30 5d  2f 54 79 70 65 2f 41 6e  |r[0 0 0]/Type/An|
00000130  6e 6f 74 3e 3e 0d 65 6e  64 6f 62 6a 0d 31 34 31  |not>>.endobj.141|
00000140  38 20 30 20 6f 62 6a 3c  3c 2f 52 65 63 74 5b 34  |8 0 obj<</Rect[4|
00000150  35 20 35 30 37 2e 34 38  20 35 36 37 20 35 31 39  |5 507.48 567 519|
00000160  2e 34 38 5d 2f 53 75 62  74 79 70 65 2f 4c 69 6e  |.48]/Subtype/Lin|
00000170  6b 2f 41 3c 3c 2f 44 28  47 37 2e 31 37 33 37 38  |k/A<</D(G7.17378|
00000180  34 36 29 2f 53 2f 47 6f  54 6f 3e 3e 2f 42 6f 72  |46)/S/GoTo>>/Bor|
00000190  64 65 72 5b 30 20 30 20  30 5d 2f 54 79 70 65 2f  |der[0 0 0]/Type/|
000001a0  41 6e 6e 6f 74 3e 3e 0d  65 6e 64 6f 62 6a 0d 31  |Annot>>.endobj.1|
000001b0  34 31 39 20 30 20 6f 62  6a 3c 3c 2f 52 65 00 fe  |419 0 obj<</Re..|
000001c0  ff ff 82 fe ff ff 02 60  6f 0d 00 f0 7e 00 00 fe  |.......`o...~...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 68 f0 0c 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 34 02  |.X.SYSLINUX...4.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 b7 3b 00 e6 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 ff cf 82 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  20 00 00 66 ba 00 00 00  |..E}.f.. ..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by wilee-nilee on 2011-05-02
Try this reload of grub2 from a cd link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by elticat on 2011-05-02
it works, thanks!

---

### Post by wilee-nilee on 2011-05-02
> **elticat said:**
> it works, thanks!

Cool, no problem.

---

### Post by cpu---777---cpu on 2011-05-03
> **wilee-nilee said:**
> Yeah so from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a lot of information.
(#)
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,848,063    21,846,016  27 Hidden HPFS/NTFS
/dev/sda2    *     22,052,864   144,803,839   122,750,976   7 HPFS/NTFS
/dev/sda3         144,803,840   267,761,663   122,957,824  83 Linux
/dev/sda4         267,761,664   390,719,487   122,957,824  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4CAA971FAA97051C                       ntfs       Recovery                      
/dev/sda2        F8B63DA2B63D6274                       ntfs                                     
/dev/sda3        d5cccf00-3652-4b8b-8625-456df6a3528f   ext4                                     
/dev/sda4        600c09c6-4bd4-44db-9ebe-b76275866ea8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
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
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d5cccf00-3652-4b8b-8625-456df6a3528f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d5cccf00-3652-4b8b-8625-456df6a3528f ro single 
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
    search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d5cccf00-3652-4b8b-8625-456df6a3528f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4CAA971FAA97051C
    drivemap -s (hd0) ${root}
    chainloader +1
}
(#)

---

