---
title: "Ubuntu as alternate OS on 2nd HD on Dell"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by mick_ub_v11 on 2011-06-30
I have a Dell 4600 with WinXP Pro SP3 on the 30GB C: drive.

I have a second 160 GB D: drive that I would like to put Ubuntu on as an alternative OS.

I have done the "Try" of Ubuntu booting from the CD and most everything seems to work ok.

I next want to install Ubuntu 11.04 on D:


At system startup, I get the F2, F12 option.
I hit F12 and get this:

Boot Device Menu:
1. Normal
2. Primary Master Drive
3. Diskette Drive
4. Hard Disk Drive C:
5. IDE CD-ROM Device
etc.

***

I choose 5 to boot Ubuntu from the CD.

What drive do I select in the future if I want to boot from the D: drive after installing Ubuntu on it?  I don't see the D: drive in the Boot Device Menu.

***

Dell Dimension 4600 Series
Pentium 4, 2.4 GHz
Level 2 Cache, 512 KB Integrated
BIOS Version A06

***

Under Drive Configuration I have:

Diskette Drive A:
SATA Primary Drive :  Off
SATA Secondary drive : Off
Primary Master Drive:  Hard Drive
Primary Slave Drive:  Off
Secondary Master Drive:  CD-ROM Device
Secondary Slave Drive:  CD-ROM Device

IDE Drive UDMA:  On

***

Hard Disk Drive Sequence:
1. System BIOS Boot Devices
2. USB Device (not installed)

***

Boot Sequence:
1. Diskette Drive
2. Hard Disk Drive C:
3. IDE CD-ROM Drive

***

Fast Boot:  On
OS Install Mode:  Off

***

Memory:  512 MB DDR SDRAM
Memory speed:  333 MHz
System Memory Channel Mode:  Dual
AGP Aperture:  128 MB

***

In summary:
For the time being, I want to retain WinXP on C:
I want to boot Ubuntu from D: with the choice made at system startup (F12)

Question:  If D: gets formatted to a file format used by Linux/Ubuntu, is there something I have to do in WinXP to let it know not to look any longer for the D: drive?

Otherwise, are there settings I need to change in order to begin my install of Ubuntu on D:  Which drive choice do I make at the F12 Boot Device Menu in order to load Ubuntu from D:  I suspect that I need to change a setting so that the D: drive is an additional choice on the Boot Device Menu, unless choice "2. Primary Master Drive" is my choice, but that doesn't make sense (yet).

I apologize if this is all too rudimentary and redundant, but I want to get into this ASAP.

Thanks,

Mick

---

### Post by oldfred on 2011-06-30
Welcome to the forums.

If I remember correctly I was trying to help another user with Dell and had a BIOS like yours. I assumed since it boots SATA you have a drive choice. But we never found it. (Ended up with grub in the MBR of the windows drive). From what I see you do have some settings to turn drive on or off which may change the boot settings. But you often have to have a bootable drive plugged in when booting for BIOS to then offer a second boot choice.

Old IDE drives would would only boot from a primary master which was set with jumpers on the drive. BIOS was just smart enough to know to jump to primary master to continue booting.
Newer drives with SATA have to let you choose drive as SATA drives have no jumpers. But some early BIOS that were still primarily IDE did not always have a SATA option it seems.

You can still install Ubuntu to the new 160GB drive. I would be sure to create a smaller system partition that is fully inside the first 137GB BIOS boot limit that some older computers have. Just create a 20GB / (root) partition and make the rest of the drive /home and swap or even split into /home and a shared NTFS for any data you want to share with windows. If you use manual install you will get a choice to install grub2's boot loader to the MBR of sdb, otherwise it defaults to sda. But then I am not sure if you will be able to boot or will have to install grub's bootloader to sda also.

---

### Post by mick_ub_v11 on 2011-07-04
OK, I got this far:

I loaded Ubuntu 11.04 on the second 160 GB D: drive (I believe!) having allocated 90GB to Ubuntu and leaving 60GB for WinXP (NTFS).  The original C: drive is 30GB with WinXP and (I presume) some newly installed instructions to offer a choice at boot to continue with a WinXP boot or alternatively boot to Ubuntu.

HOWEVER!!!!!

After install, which seemed to go smoothly enough, I reboot the PC, and after the BIOS boot, the PC makes a funny noise like a HDD is having a mild heart attack, and stops dead with this error message:

Error:  No Such Device:
dd691809-e29e-466b-9392-c978c2f9134b.
Grub Rescue>_

***********************

I re-installed Ubuntu from the CD again.  This time a lot faster, of course, because the D: drive was already partitioned and formatted for Ubuntu from the first install.  

On the next reboot, I get the same error message, but only with different hex values.

It appears all the WinXP (NTFS) contents are intact as per the info I obtained next...

***********************

I poked around and obtained enough info to make this determination:

IDE Hard Drive Diagnostics

Primary SATA
Drive 0:  No Device

Secondary SATA
Drive 0:  No Device

Primary IDE
Drive 0:  MAXTOR 6E030L0 - Pass
Drive 1:  No Device

Secondary IDE
Drive 0:  GCR-8481B - Diagnostics Not Supported
Drive 1:  NEC DVD+RW ND-1100A - Diagnostics not supported.

***

Unknown MBR on /dev/sdb

Unknown bootloader on sda1

Unknown bootloader on sdb2

Std Err Messages:
UNLZMA:  Decoder Error

*******

sda1:  vfat
win95

**

sda2:  ntfs
winXP
Bootfiles:  /boot.ini /ntldr ntdetect.com

**

sdb1:  ntfs
WinXP

**

sdb2:  extended partition

**

sdb5:  swap

**

sdb6:  ext4
Ubuntu 11.04
bootfiles:  /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

**

sdb7:  swap

****************************

I know vaguely what this all means, but only enough to be dangerous.

Thanks if you can point me in a more positive direction!

 - Mick

---

### Post by oldfred on 2011-07-04
I do not understand why BIOS does not even see second drive but your seem to see sdb. I think the issue with some of these Dell's was they only booted from the IDE drive as sda.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by smurphy_it on 2011-07-04
Looks like you BIOS is having some issues with one of the HDD's.  Suggest you grab some HDD testing utilities.  (Hiren's Boot CD, comes to mind).  Validate that both drives are good.

If they are, you'd have to move on to seeing if you can update your BIOS with a newer revision, or seeing if a newer BIOS exists for your Hard Drive(s).

If you don't have luck with the BIOS (or don't want to risk it), then look around for a "Bootloader" for your bios.  If you have an old system, it could be having some issues with the drive layout.

Alternatively, you should validate that the Physical drive attributes were detected properly and that is what the BIOS is using.  Note that if you change the disk attributes (in the BIOS) it will most likely erase your drive, so make sure you know which drive you are dealing with and back it up first.

---

### Post by mick_ub_v11 on 2011-07-04
As per request from oldfred.
Thanks,  Mick_ub_v11



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 59280e83-eabd-436b-a104-2d691f57b446 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.8 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    60,034,904    59,970,645   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   122,197,163   122,197,101   7 NTFS / exFAT / HPFS
/dev/sdb2         122,198,014   312,580,095   190,382,082   5 Extended
/dev/sdb5         311,537,664   312,580,095     1,042,432  82 Linux swap / Solaris
/dev/sdb6         122,198,016   310,491,135   188,293,120  83 Linux
/dev/sdb7         310,493,184   311,531,519     1,038,336  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        07D3-0609                              vfat       DellUtility
/dev/sda2        94407A124079FB76                       ntfs       
/dev/sdb1        D2C020DAC020C717                       ntfs       DISK2_VOL1
/dev/sdb5        bc219906-1c58-4d67-bcb9-6d79a3a7fdb3   swap       
/dev/sdb6        59280e83-eabd-436b-a104-2d691f57b446   ext4       
/dev/sdb7        f4791cde-2f11-4e05-a4b9-cc0ffa26bf03   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
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
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59280e83-eabd-436b-a104-2d691f57b446 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59280e83-eabd-436b-a104-2d691f57b446 ro single 
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
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 59280e83-eabd-436b-a104-2d691f57b446
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 94407A124079FB76
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=f4791cde-2f11-4e05-a4b9-cc0ffa26bf03 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  92.482200623 = 99.302006784   boot/grub/core.img                             1
  82.981052399 = 89.100226560   boot/grub/grub.cfg                             1
  59.659042358 = 64.058408960   boot/initrd.img-2.6.38-8-generic               2
  92.480487823 = 99.300167680   boot/vmlinuz-2.6.38-8-generic                  1
  59.659042358 = 64.058408960   initrd.img                                     2
  92.480487823 = 99.300167680   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  b0 7b 70 1e 00 00 00 01  |.........{p.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 6d 94 48 07 00 fe  |......?...m.H...|
000001d0  ff ff 05 fe ff ff fe 97  48 07 02 00 59 0b 00 00  |........H...Y...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 09  06 d3 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 00 55 aa  |    SYS.......U.|
00000200

Unknown BootLoader on sdb2

00000000  cb 95 ba 91 6d ae 84 7f  24 60 12 41 1e c2 b6 55  |....m...$`.A...U|
00000010  2c cd 0d 3d 02 da ef c3  51 bc ae b1 dc 48 83 2a  |,..=....Q....H.*|
00000020  d1 a9 f9 be b5 eb 96 b0  5b eb ba 24 73 22 18 6e  |........[..$s".n|
00000030  d9 73 24 67 a8 f7 1f 4a  53 7c ce e8 b4 b4 b1 8e  |.s$g...JS|......|
00000040  64 5b e5 fb 26 49 b6 53  f3 b0 5c 90 7e 95 c5 dc  |d[..&I.S..\.~...|
00000050  6a 49 a4 6b 20 c0 09 31  9e b9 c6 ea 50 7a d8 cd  |jI.k ..1....Pz..|
00000060  bb 1d f0 96 6d 4f 4a 92  e6 18 3c c8 9b 87 40 7a  |....mOJ...<...@z|
00000070  fa d7 87 cb e1 e7 6d 65  a3 08 16 d7 18 31 91 d0  |......me.....1..|
00000080  d1 29 59 b1 cb b9 d3 6a  ff 00 0a df c7 5a 95 b5  |.)Y....j.....Z..|
00000090  f4 80 79 1a 55 a9 45 c7  20 37 50 3d 8f f8 d7 91  |..y.U.E. 7P=....|
000000a0  78 47 c0 52 ea 16 5a de  bb 7d b6 2b bb 4b 77 74  |xG.R..Z..}.+.Kwt|
000000b0  89 c7 50 3a 11 57 1c 4f  2c 6c cd 60 ec ae 47 f0  |..P:.W.O,l.`..G.|
000000c0  83 e0 f2 7c 47 d1 e0 d6  af 64 16 cd 22 87 e3 3d  |...|G....d.."..=|
000000d0  7d 3e b5 f5 16 bb f0 e3  c2 de 29 b3 b6 d3 75 3d  |}>........)...u=|
000000e0  22 06 6b 55 fd dd ec 69  82 0f a9 f5 3e f5 8e 26  |".kU...i....>..&|
000000f0  ac de b1 d2 c1 b7 bc cf  48 f0 e7 c3 4d 3f c3 9a  |........H...M?..|
00000100  41 5d 3e e6 39 d1 17 28  3a 12 2b 86 bc 96 7f 12  |A]>.9..(:.+.....|
00000110  97 85 e4 31 48 ae 54 95  1b 71 83 5e 65 3f de 4d  |...1H.T..q.^e?.M|
00000120  b7 b9 4d e8 79 a6 a5 60  be 1f 95 c4 6f e7 4c 4f  |..M.y..`....o.LO|
00000130  2a f2 f3 5d 64 ba a6 a3  a5 68 51 4c 37 88 e4 5c  |*..]d....hQL7..\|
00000140  26 46 46 7e b5 bf 2f 33  5c c6 2e a7 2b b2 3e 76  |&FF~../3\...+.>v|
00000150  7f 17 eb 3a 57 8c 65 bb  9a d1 6e a7 8d 82 c6 f1  |...:W.e...n.....|
00000160  1f 2d 80 1c e4 1f 5e 7b  d7 1b e2 0f 86 10 fc 45  |.-....^{.......E|
00000170  d5 ae 6f 74 8b b3 63 a8  4c db 9b 4f d4 23 31 06  |..ot..c.L..O.#1.|
00000180  6f f6 5f a1 35 e9 c3 96  83 53 8e c5 27 65 63 37  |o._.5....S..'ec7|
00000190  c2 9e 17 d5 fc 38 ad 67  a8 d9 4b 68 c8 c4 10 57  |.....8.g..Kh...W|
000001a0  23 fe fa e9 5f 66 fc 13  f0 d5 9e b9 e1 dd 55 1d  |#..._f........U.|
000001b0  a3 37 2c 76 c2 92 1c 64  e3 b1 ae 3c 4d 65 00 fe  |.7,v...d...<Me..|
000001c0  ff ff 82 fe ff ff 02 18  49 0b 00 e8 0f 00 00 fe  |........I.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 20 39 0b 00 00  |........... 9...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by mick_ub_v11 on 2011-07-04
As per [smurphy_it]("http://ubuntuforums.org/member.php?u=288150") request:

I burned a Hiren's Boot CD.

Now what?

Or, which utility(ies) do I use to determine the status of my two hard drives?

Thanks,

 - Mick

---

### Post by YesWeCan on 2011-07-04
The bootinfo looks reasonable to me. Although I get suspicious when Grub uses an embeded config file; that may be incidental. Getting to "grub rescue>" is something positive. It means the Grub pre-booting code is working fine on sda. So it was unable to search sdb and load files from /boot that it needs (it looks for the UUID of the partition and this is the long hex number you see). It may be a problem with the disk or it may be a problem with how Dell's bios works.

It would be informative to know what partitions Grub can see. If the next time it is at the  rescue> prompt would you type 'ls', that will list all the partitions it can see.

---

### Post by mick_ub_v11 on 2011-07-04
Response to request of YesWeCan:

"It would be informative to know what partitions Grub can see. If the next time it is at the rescue> prompt would you type 'ls', that will list all the partitions it can see."

grub rescue>ls

(hd0) (hdo,msdos2) (hd0, msdos1) (fd0)


Thanks,
Mick

---

### Post by mick_ub_v11 on 2011-07-04
Sorry, slight typo just previous on the "o" and "0":


grub rescue>ls

(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)


Where:  0 = zero  (hd0)
Where:  o = oh    (msdos)

 - Mick

---

### Post by oldfred on 2011-07-04
It is not seeing any partitions on your second drive, but boot script shows sdb??

How is sdb plugged in. Is it SATA or IDE. Is it on the same IDE channel as your CD drive?

---

### Post by smurphy_it on 2011-07-05
```
As per smurphy_it request:
I burned a Hiren's Boot CD.
Now what?
Or, which utility(ies) do I use to determine the status of my two hard drives?

```

I need to download that tool to test out a crappy windows system for a friend of mine.  I'll be checking it out shortly, however, from their web page it looks like you'll be doing a hdd check from the "Hard Disk Tools menu".  You'll need to know what kind of hard drive it is for starters.  If not, one of the tools in there should be able to determine that.  Watch out for the "low level formatting" tools.  It will totally wipe your drive, and its not easily recovered (as it's a low level format as opposed to an O/S format, which is a high level format).

---

### Post by mick_ub_v11 on 2011-07-05
On the Hiren's Boot CD were a couple of utilities I recognized, so I ran these:  Seagate Disk Wizard (which was used to install the second HDD (ST3160023A where ST is Seagate Technologies) and Seagate SeaTools.

**************************

Disk Wizard returned this:

Disc 1:  28.64 GB Maxtor 6E030L0  IDE (0) Primary Master

Disc 2:  149.1 GB ST3160023A IDE (0) Primary Slave

****************

more detail:

Disc 1:  28.64 GB  (Partitions)

**

FS:Fat16 Partition: 0XDE
(EISA configuration)
31.35 MB
PRIMARY

**

C:
28.64 GB NTFS
PRIMARY

**

Unallocated 7.844MB
UNALLOCATED


*******

Disc 2: 149.1 GB  (partitions)

**

Disc2_Vol1 (D: )
58.27 GB NTFS
PRIMARY

**

E:
89.79 GB EXT3
LOGICAL

**

Linux Swap 507 MB
LOGICAL

**

Unallocated 480 KB
UNALLOCATED

**

Linux Swap 509 MB
LOGICAL

***********************************

SeaTools returned the following:

Maxtor 6E030L0, s/n xxx, rev. NAR61590
Device 0 = ATA Device Maxtor 6E030L0 on generic PCI ATA
Max Native address:  60058655
Device is 28 bit addressed
number of LBAs 60058655  (30.750 GB)
This drive supports security features
SMART is supported and enabled
SMART has not been tripped
DST is supported
Logging feature set is not supported
POH 22218

*****

Seagate ST3160023A, s/n xxx, rev. 8.01
Device 1 = ATA Device Seagate ST3160023A on generic PCI ATA
Max Native address:  312581807
Device is 48 bit addressed
number of LBAs 312581807  (160.042 GB)
This drive supports security features
SMART is supported and enabled
SMART has not been tripped
DST is supported
Logging feature set is supported
POH 15457  Current Temp 36

**********************************

Thanks,
 - Mick

---

### Post by smurphy_it on 2011-07-05
Bios getting confused ?  This is what I see in this thread:

```
Secondary IDE
Drive 0: GCR-8481B - Diagnostics Not Supported
Drive 1: NEC DVD+RW ND-1100A - Diagnostics not supported.

```

Yet, when you run the HDD tools from the Hirens Boot CD, you get this:
```
Disc 2: 149.1 GB ST3160023A IDE (0) Primary Slave
```

Very peculiar.  Have you tried enabling the "Primary Slave" as a boot device in the BIOS.

```
BIOS Version A06
Under Drive Configuration I have:
Diskette Drive A:
SATA Primary Drive : Off
SATA Secondary drive : Off
Primary Master Drive: Hard Drive
Primary Slave Drive: Off  <--- Can you change this --> ?
Secondary Master Drive: CD-ROM Device
Secondary Slave Drive: CD-ROM Device

```

If you are "technical" I'd suggest you verify the jumper settings for the two hard drives, and indicate what IDE channel they are on.  As sometimes the drive is showing up as a secondary slave, and other times as a primary slave. If they are both on the same IDE cable (Primary), you can try forcing one to master, and other to slave... Or set them both to Cable select.  Could try unhooking the CD-ROMs to take that out of the picture.

---

### Post by smurphy_it on 2011-07-05
You have this configuration:

Primary Master = 30GB Maxtor HDD
Primary Slave = 160GB Seagate HDD
Secondary Master = GCC CD-ROM/DVD-X
Secondary Slave = NEC DVD RW

I'd validate jumper settings on the two hard drives.  Verify they are master and slave.  Some drives have a jumper on them that indicate they are the "only drive in the chain".  Verify this isn't the case with your maxtor drive too!

---

### Post by YesWeCan on 2011-07-05
It is curious that when Ubuntu is run from CD the 149GB drive is accessible. Presumably, it was also accessible using Windows (although Windows cannot be booted now). But Grub's loader cannot access it. Perhaps the bios is in a different mode, or something is not yet enabled in the bios. I don't think it is a boot device selection issue because the 149GB is not being booted by the bios.

Two possible work-arounds:
1) Install Grub to the 149GB drive's MBR and restore the standard MBR to the Windows disk. Then add Grub to the Windows boot-loader menu: boot Ubuntu using Windows.

2) Install Grub to the MBR of the 149GB disk and swap it with the Windows disk so it becomes the primary master. This may create a problem with Windows updates, tho.

---

### Post by mick_ub_v11 on 2011-07-05
I booted via the Hiren's Boot CD and am able to load WinXP fairly normally.  Everything seems to work.  Perhaps a bit slower.  The D: drive shows in "My Computer" as having the approx. 60GB now allocated after designating the balance of the 160GB D: drive (90GB) to Ubuntu.

Just can't get anywhere without a boot CD.

All in the name of doing without 100% Microsoft!

 - Mick

---

### Post by smurphy_it on 2011-07-06
I would suspect this is your problem:

```
FS:Fat16 Partition: 0XDE
(EISA configuration)
31.35 MB
PRIMARY
```

Perhaps you can backup that partition, then delete it to see if it fixes your problem.  If not, restore the partition.  Clonezilla should be able to do this for you (in case Hiren's boot CD can't) which is available at [http://clonezilla.org](http://clonezilla.org)

---

### Post by mick_ub_v11 on 2011-07-06
Also:

I am thinking that if I give up in exasperation and wipe both drives in order to make the entire machine (both drives) Ubuntu, the BIOS will continue to have the very same issue, i.e., it cannot see the second drive.  Yes?
No?

If the easy way out is to make it an Ubuntu-only machine, that is tempting, but that is also giving up, which I tend not to do.

What tool is it, and/or what command(s) is it, that I can edit the BIOS/MBR line that enables Drive 1  / Primary-Slave (D: drive) to also be visible to the BOOT sequence?

Thanks,


 - Mick

---

### Post by oldfred on 2011-07-06
Did you follow smurphy_it's earlier suggestion. 

If misjumpered  or 40 wire cable with cable select setting, maybe somehow it works and BIOS do not see it. It is normal that it will not be seen if BIOS does not see it.


with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by mick_ub_v11 on 2011-07-06
it is an 80 pin ribbon cable and the blue with mother, black with master, and gray with slave.  all good there.

 - Mick

---

### Post by mick_ub_v11 on 2011-07-06
Again, when I use the Hiren's Boot CD, I can load WinXP and it loads normally with all my customizations (desktop, etc.).  I can see the D: drive with the 60GB allocated (formerly 160GB before I partitioned off 90GB for the Ubuntu install).

 - Mick

---

### Post by mick_ub_v11 on 2011-07-07
Hmmm....

Now the Dell will boot to WinXP without any Boot CD intervention.  It seems to run a bit oddly and slowly, but otherwise it all works.  I don't know what changed.  No more "Error: No Such Device / Grub Rescue>_"

The only thing I can fathom is that when I went to make a determination that I had the 80 pin ribbon cable attached properly, I detached the gray (Slave) plug from the D: Drive 1 (Seagate 160GB) in order to be able to see anything, and re-attached it.  I had power un-plugged, both at the back of the PC and at the drive.  I don't think that should have changed anything.


When I go to the utilities in WinXP, I can see the partitions of the drives, all correct.


However there is still no boot option to go to Ubuntu.

 - Mick

---

### Post by oldfred on 2011-07-07
To boot windows directly you have to have the windows boot loader in the MBR of the primary master which it is booting. Did some setting change to make a different drive primary master. Either jumpers on drive or BIOS setting.

Are drives set to cable select and not master nor slave?

---

### Post by mick_ub_v11 on 2011-07-08
To All:

Previously smurphy_it asked the following ("Can you change this?"

BIOS Version A06
Under Drive Configuration I have:
Diskette Drive A:
SATA Primary Drive : Off
SATA Secondary drive : Off
Primary Master Drive: Hard Drive
Primary Slave Drive: Off  <--- Can you change this --> ?
Secondary Master Drive: CD-ROM Device
Secondary Slave Drive: CD-ROM Device


I went into Hard Drive Configuration in the F2 during BIOS boot and set Primary Slave from "OFF" to "AUTO".  Next time I rebooted and checked it now identified the drive as the Seagate 160GB.  Under my F12 at BIOS boot , now I had the Primary Slave listed as a boot disc choice, where it had not been listed before.  I rebooted once again from the CD drive and un-installed/re-installed Ubuntu 11.04.

VOILA!!!  At reboot, the system goes to an Ubuntu screen offering 4 choices, first being Ubuntu, fourth being WinXP.

So far, it's all working.

As I am just now (finally) getting started with Ubuntu from the D: drive (hd1), I still have some housekeeping things to check.  Next I will see if I can print to my wireless printer.

After that, my next project will be a 1997 Sony Vaio Pentium 1 with 32MB RAM, Win98 SE, 8GB hard drive.  I understand that I should be going with an Ubuntu-LITE for this application.  Can you suggest which one?

Thanks, and I'll keep you posted on any further progress on either machine.

 - Mick

---

### Post by smurphy_it on 2011-07-11
```
I went into Hard Drive Configuration in the F2 during BIOS boot and set Primary Slave from "OFF" to "AUTO". Next time I rebooted and checked it now identified the drive as the Seagate 160GB. Under my F12 at BIOS boot , now I had the Primary Slave listed as a boot disc choice, where it had not been listed before. I rebooted once again from the CD drive and un-installed/re-installed Ubuntu 11.04.
```

Sounds like the ribbon cable wasn't in properly.  Now that it is inserted properly, it is being read properly, and as you've already done, can be booted from.

Sounds solved to me (thread tools, Mark as Solved).

Addtionally:  32MB Ram on old laptop... WoW.  I'd go really light for something old like that.  Perhaps puppylinux or DSL for starters.

---

### Post by mick_ub_v11 on 2011-07-11
Yes, 32 MB is on a desktop Sony Vaio, NOT a laptop.  So far I've tried PuppyLinux on it (hangs) and DSL (so-so).

Thanks for input to solve Ubuntu loading problem on Dell 512MB Pentium 4.

I'll figure out next how to mark thread SOLVED.

Thanks!!!

 - Mick

---

