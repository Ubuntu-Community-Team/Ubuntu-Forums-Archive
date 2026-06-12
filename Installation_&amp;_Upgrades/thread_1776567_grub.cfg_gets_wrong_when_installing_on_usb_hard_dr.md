---
title: "grub.cfg gets wrong when installing on usb hard drive"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by natlose on 2011-06-06
I have a HP Compaq 6710b notebook with W7 on it. I want to use Ubuntu for hobby activities, but as this is a company notebook, W7 should remain intact. I decided to install Ubuntu to an external drive.
I set BIOS boot order to CD-USB-HDD.
I attached a 2.5" 250GB WD Passport usb hard disk and installed Ubuntu to it from the CD.
As a result, the clean install doesn't boot, I get a mere grub console (normal, not rescue).

Examining the situation I learned, that during Live CD session the inner hdd is hd0 and usb drive is hd1. Grub.cfg gets compiled to use /dev/sdb.
When booting from usb drive, BIOS makes it to be hd0 and inner hdd becomes hd1 so grub tries to load kernel from W7 partition (and can't find it, I wonder why? :))

How to fix problem? Although grub.cfg is supposed not to be edited, may I change every sdb to sda in it?

---

### Post by oldfred on 2011-06-06
Welcome to the forums.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Do you get to grub menu, or grub> prompt? Yes the BIOS/grub sets boot drive as hd0 but that is only in grub. Once in Ubuntu I think you will find sda is internal hard drive. It is that way with my system. Normally even if hdX is wrong the search by UUID will override the entry and boot correctly. But both grub2 & fstab have to use UUIDs. Above script will show all that info so we can see what is where.

---

### Post by natlose on 2011-06-06
So, here are the results. Hope it helps to fix the problem.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   231,184,383   230,977,536   7 NTFS / exFAT / HPFS
/dev/sda3         231,184,384   234,438,655     3,254,272   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   484,220,927   484,218,880  83 Linux
/dev/sdb2         484,222,974   488,396,799     4,173,826   5 Extended
/dev/sdb5         484,222,976   488,396,799     4,173,824  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1A3C94863C945E97                       ntfs       Rendszer számára fenntartott
/dev/sda2        AE2EAED62EAE973D                       ntfs       
/dev/sda3        1A2C2C112C2BE68B                       ntfs       OS_TOOLS
/dev/sdb1        4d7d6869-9200-47d7-88a5-00535e8d9bb6   ext4       
/dev/sdb5        cd2ebf24-fc18-449b-8b49-c78c037ae0f4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4d7d6869-9200-47d7-88a5-00535e8d9bb6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4d7d6869-9200-47d7-88a5-00535e8d9bb6 ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4d7d6869-9200-47d7-88a5-00535e8d9bb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1A3C94863C945E97
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4d7d6869-9200-47d7-88a5-00535e8d9bb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cd2ebf24-fc18-449b-8b49-c78c037ae0f4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 116.133773804 = 124.697690112  boot/grub/core.img                             1
 116.137702942 = 124.701908992  boot/grub/grub.cfg                             1
   1.098854065 = 1.179885568    boot/initrd.img-2.6.38-8-generic               2
 116.133281708 = 124.697161728  boot/vmlinuz-2.6.38-8-generic                  1
   1.098854065 = 1.179885568    initrd.img                                     2
 116.133281708 = 124.697161728  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  d8 63 2a cc d1 16 12 64  38 22 20 44 14 47 3e d7  |.c*....d8" D.G>.|
00000010  66 15 49 fe df 46 49 3f  a6 e7 0f a4 01 b0 33 53  |f.I..FI?......3S|
00000020  68 87 20 93 f9 68 25 06  d7 09 52 1d 32 85 82 f3  |h. ..h%...R.2...|
00000030  6d de d9 89 c2 06 04 b3  7e d6 4a bb b8 58 5c 2d  |m.......~.J..X\-|
00000040  16 4c 86 b6 66 07 dd 41  d8 38 b2 d6 7e f7 a1 9c  |.L..f..A.8..~...|
00000050  d3 ac 5e 55 a0 fb da 63  46 79 32 5f 56 51 18 92  |..^U...cFy2_VQ..|
00000060  7f db 4b 33 6c d2 1f 44  3a 6c c1 d6 5e fc 62 de  |..K3l..D:l..^.b.|
00000070  27 02 87 38 69 f1 61 d5  8e 0a 33 13 4c fb 86 fa  |'..8i.a...3.L...|
00000080  5a 22 71 d8 8e 57 99 ea  de 68 9c 23 f7 fd 9b 71  |Z"q..W...h.#...q|
00000090  a0 55 3f 29 55 6c 96 5d  5b 5d 8d 0d 3b b6 42 dd  |.U?)Ul.][]..;.B.|
000000a0  8e 81 22 d4 2c 48 b6 7a  e3 d0 17 6e 5c 95 f8 b1  |..".,H.z...n\...|
000000b0  39 30 70 f3 4a 24 f6 05  96 f6 ff b1 96 4e 48 0a  |90p.J$.......NH.|
000000c0  a3 eb 23 09 43 e0 43 7f  46 0e 7e 4f 93 f7 d4 bb  |..#.C.C.F.~O....|
000000d0  29 13 53 84 d1 87 43 42  83 d6 de ee a7 6b 07 c8  |).S...CB.....k..|
000000e0  eb b2 64 0b 59 9a 77 58  b6 38 b3 07 13 a4 c6 2f  |..d.Y.wX.8...../|
000000f0  77 4f 8c ac 81 cb 8a 36  d3 1b e5 9c 0e 76 68 ee  |wO.....6.....vh.|
00000100  f9 f7 d4 85 2d ea 30 b2  a5 fa 14 cb bd 68 61 94  |....-.0......ha.|
00000110  fd 21 08 a7 af 68 fd f8  e4 c5 f2 35 17 53 e1 f8  |.!...h.....5.S..|
00000120  33 a5 ba a5 9d ac ce 48  25 7a 82 bb 16 22 ad 9e  |3......H%z..."..|
00000130  68 08 57 e7 4f 12 6d e7  f8 5b bc 36 40 9c 73 b9  |h.W.O.m..[.6@.s.|
00000140  3d 6d ed f1 9f bd 5b 0d  30 a8 fa f6 57 cb bb 6f  |=m....[.0...W..o|
00000150  0b 96 dd 53 d9 0f 21 e6  3b a3 95 56 69 67 27 b7  |...S..!.;..Vig'.|
00000160  b1 96 1d 56 73 ec f0 3f  85 df 08 7a 83 8b 42 f9  |...Vs..?...z..B.|
00000170  f6 30 ee f0 f0 d6 f0 95  06 c9 01 e1 94 68 e5 00  |.0...........h..|
00000180  0f c8 eb a7 88 83 85 c6  73 f4 f1 f9 20 0c 4f 77  |........s... .Ow|
00000190  fc 64 c8 2e 4a ec 0e 13  8b 64 6b f5 43 ff 84 a9  |.d..J....dk.C...|
000001a0  09 4f 61 f3 7a 3b 00 6d  16 65 90 c9 4f e5 6d 09  |.Oa.z;.m.e..O.m.|
000001b0  c3 81 18 ed 7b 5e 25 1d  f8 65 d6 b9 e0 8d 00 fe  |....{^%..e......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
I didn't got grub menu, just the promt. I started a new Live session, logged in as root, edited grub.cfg changing all sdb to sda. In this way I got a grub menu after reboot, but selecting first menuitem I get a 'hd0 out of disk...press any key' message. Pressing a key finally the system starts.
This version of grub.cfg will be recompiled on every upgrade, will not? Then I will be again locked out.

---

### Post by oldfred on 2011-06-06
Yes any change to grub, kernel or manual changes to grub2's configuration files where you run sudo update-grub writes a new grub.cfg.

With grub2 version1.99 it now uses /dev/sda rather than hd0, but the search for  the correct UUID should override the wrong drive. We have seen many cases where drive is wrong but it still boots by UUID.

I have seen where search gives up as it only looks for so many drives and if too many empty drives then it did not find my USB way down the list. Also some with very large  / (root) partitions have had issues like the old systems with BIOS boot limits of 137GB. I think those relate to BIOS settings, but not sure. You could try shrinking your root partition and checking BIOS settings.

Not sure if any of this may apply, I have saved a list of BIOS related issues. RAID & Large are two common issues. RAID even if only one drive as BIOS setting may have caused hidden meta data to be written to drive.
Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

---

