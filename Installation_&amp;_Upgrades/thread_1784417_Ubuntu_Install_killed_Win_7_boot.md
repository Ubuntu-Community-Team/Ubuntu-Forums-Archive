---
title: "Ubuntu Install killed Win 7 boot"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by jmechy on 2011-06-16
I've seen a lot of other people having this problem, but can't quite find a way to fix it on my machine.
I have a Win 7 box and decided to dual boot Ubuntu 11.04.  I installed Ubuntu, letting it repartition my Win 7 drive for me.  Unfortunately I did NOT reboot into Windows after this step, but continued on with the installation.
Now I can boot into Ubuntu through GRUB, but when I click the Win 7 option it just shoots me back to GRUB.  
I have verified that my Win 7 partition is there, has files on it, and is flagged as bootable.
I've tried using a Win 7 DVD to run the recovery tools with no luck.  I ran "startup repair", which attempted repairs and said that the source of the problem was that "the partition table does not have a vaild system partition".  However, it said the partition table repair was successful.  
I also tried bootrec /fixMBR (operation completed succesfully) and bootrec /fixboot (element not found).  I even gave /rebuildBCD a shot, which eventually also reports element not found (though does does detect and allow me to select my win 7 install).

Anyone have any wisdom in this area?

---

### Post by mister_playboy on 2011-06-16
While running Ubuntu, can you mount and access the Win7 partition successfully?

---

### Post by jmechy on 2011-06-16
> **mister_playboy said:**
> While running Ubuntu, can you mount and access the Win7 partition successfully?

Yup, I can see it fine, all my files look ok.

---

### Post by mister_playboy on 2011-06-16
After you ran the Win7 recovery tools, did you try running ```
sudo update-grub
``` from within Ubuntu?

---

### Post by jmechy on 2011-06-16
Same problem, click the Win 7 loader and it just bounces me back into GRUB every time.

---

### Post by oldfred on 2011-06-16
Lets get an idea of what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jmechy on 2011-06-16
When booted into the Win 7 cd and choosing "repair you computer", I don't see any systems listed.  Normally that means drivers need to be loaded, but I'm pretty sure that I don't need any special drivers loaded for windows to read my system drive (straight SATA on the motherboard, no RAID).  
I figure it tries to grab this information from the bootloader, which it apparently can't find.

edit: I'll get that bootinfoscript in a minute.

---

### Post by jmechy on 2011-06-16
Bootinfoscript results:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/pdc_fdghgdce.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb1 has 
                       398282751 sectors, but according to the info from 
                       fdisk, it has 398283416 sectors.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdc1 
                       and looks at sector 1152718432 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

pdc_fdghgdce1: _________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, 
                       pdc_fdghgdce1 has 398282751 sectors, but according to 
                       the info from fdisk, it has 398283416 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   625,139,711   625,137,664   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   398,283,479   398,283,417  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             64 1,131,442,807 1,131,442,744   7 NTFS / exFAT / HPFS
/dev/sdc2       1,131,444,222 1,250,263,039   118,818,818   5 Extended
/dev/sdc5       1,131,444,224 1,241,878,527   110,434,304  83 Linux
/dev/sdc6       1,241,880,576 1,250,263,039     8,382,464  82 Linux swap / Solaris


Drive: pdc_fdghgdce _____________________________________________________________________

Disk /dev/mapper/pdc_fdghgdce: 203.9 GB, 203928043520 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398296960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_fdghgdce1                 63   398,283,479   398,283,417  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 c0e02363-4f59-4e2b-9d36-8fc4f6822d50   swap       
/dev/sda1        425883015882F2C9                       ntfs       Backup
/dev/sdb1        3CD8A149D8A101EE                       ntfs       fatty
/dev/sdc1        4E22B33522B320BF                       ntfs       
/dev/sdc5        90e79d3f-5dc0-470d-a890-aa0301d868d8   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90e79d3f-5dc0-470d-a890-aa0301d868d8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90e79d3f-5dc0-470d-a890-aa0301d868d8 ro single 
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root 90e79d3f-5dc0-470d-a890-aa0301d868d8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 4E22B33522B320BF
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=90e79d3f-5dc0-470d-a890-aa0301d868d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
#UUID=0680ea2a-f22a-410c-8297-fc737b93b762 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 549.659008026 = 590.191865856  boot/grub/core.img                             1
 551.745498657 = 592.432218112  boot/grub/grub.cfg                             1
 540.334960938 = 580.180246528  boot/initrd.img-2.6.38-8-generic               2
 549.657321930 = 590.190055424  boot/vmlinuz-2.6.38-8-generic                  1
 540.334960938 = 580.180246528  initrd.img                                     2
 549.657321930 = 590.190055424  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  e9 da f1 1a b0 08 a0 6f  fd 78 04 5b 41 4e d7 91  |.......o.x.[AN..|
00000010  47 c1 a2 81 be b5 e4 d1  6c 35 79 2d 21 16 48 57  |G.......l5y-!.HW|
00000020  94 c7 b0 35 e5 4e 98 0b  e8 5b 57 4e 57 95 bb d9  |...5.N...[WNW...|
00000030  fa f2 da 08 6e a1 0e 82  5b 48 40 70 63 f8 25 c0  |....n...[H@pc.%.|
00000040  ba 08 6e 21 11 c1 2d d4  43 70 0b f5 11 dc 42 03  |..n!..-.Cp....B.|
00000050  04 b7 d0 10 c1 2d 34 42  2c 8d 70 6d cc 56 9f 37  |.....-4B,.pm.V.7|
00000060  05 36 83 d1 15 e8 cd 80  2d 60 2d 81 fc 6a f4 56  |.6......-`-..j.V|
00000070  c0 36 b0 b6 40 7e 65 7a  3b 60 07 d8 7b 40 7e 95  |.6..@~ez;`..{@~.|
00000080  7a 27 a0 6f a5 7a 37 84  ae 42 77 84 ae 42 0f 84  |z'.o.z7..Bw..B..|
00000090  ae 6c c5 3a 5d af de 1b  f8 3e 42 2f b6 6e bd 97  |.l.:]....>B/.n..|
000000a0  d0 17 a1 97 d0 0f a1 97  d0 1f a1 17 5b c3 de 4b  |............[..K|
000000b0  18 88 d0 4b 18 84 d0 4b  18 8c d0 8b ad 67 ef 85  |...K...K.....g..|
000000c0  d8 0f b9 16 24 8e 6f 55  eb c0 67 ed 32 8e 28 be  |....$.oU..g.2.(.|
000000d0  76 cb dd 2e be 37 fd fe  85 67 15 59 53 74 09 e3  |v....7...g.YSt..|
000000e0  eb 34 58 cb f1 c5 d5 f3  a1 a7 dd 58 98 b8 6d 62  |.4X........X..mb|
000000f0  28 d9 cc e9 8f c7 4f 71  8d 58 2c 12 8b 67 01 39  |(.....Oq.X,..g.9|
00000100  da 22 3d f1 88 1f 3f c6  be 80 f1 23 48 da b3 e5  |."=...?....#H...|
00000110  26 e9 7f 50 8b 7d 7f c3  d3 9b 18 f2 47 8c f9 a3  |&..P.}......G...|
00000120  e9 97 58 18 ea dd cc f1  2c fd a1 be f4 0d f9 27  |..X.....,......'|
00000130  c6 fc d3 fc 55 f3 d3 23  7f 43 4d f3 47 8c f9 1b  |....U..#.CM.G...|
00000140  b0 7e 0e e3 f7 14 b3 a8  7d b5 66 85 57 6e fa 6d  |.~......}.f.Wn.m|
00000150  1b da 97 0f 2d f3 f1 fd  b6 57 a8 a3 f0 3f 46 bc  |....-....W...?F.|
00000160  72 e7 f1 b4 20 93 2c 73  c8 b9 c6 f3 12 1f cf 6d  |r... .,s.......m|
00000170  45 f4 7a 67 7c f4 ad 64  36 16 29 fc 67 7b 78 bd  |E.zg|..d6.).g{x.|
00000180  33 be f6 8d 36 a4 58 9c  87 8c ba f3 89 89 7e 6f  |3...6.X.......~o|
00000190  ad 33 54 7f c6 43 9e 7d  e5 ab bf 81 2b ee 64 29  |.3T..C.}....+.d)|
000001a0  7c 9d e8 c8 78 9b a7 2b  99 8c f4 17 d7 f8 38 31  ||...x..+......81|
000001b0  74 5b 30 f1 2e e7 f9 1c  ae 3a 77 ba 93 22 00 fe  |t[0......:w.."..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 18 95 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 18  95 06 00 f0 7f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-06-17
I do not know about LVM or RAID.
So I am not sure what this is:
Windows is installed in the MBR of /dev/mapper/pdc_fdghgdce.

Did the script just not be able to see the mapper because you do not have these installed?
Install these before running script if you have LVM or RAID:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)
sudo apt-get install mawk

You do have grub installed to a windows boot sector sdc1. Windows has to have its boot code in the partition boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by jmechy on 2011-06-17
I installed LVM2 and already had mawk installed, the script results were the same.

I am not running any kind of RAID, just a SATA disk plugged directly into the onboard SATA controller.

Tried running testdisk and following the directions above, but same results when I try to run Win7 from GRUB (even after updating GRUB again).

---

### Post by jmechy on 2011-06-17
Running out of ideas now.
I was thinking maybe I could repartition the drive back to how it was (one large NTFS partition, wiping out the Ubuntu install), then run the windows repair tools from the disc again.  I knew I shouldn't have tried to repartition my main system drive, so stupid...

Any other ideas? I haven't lost any data, but I'd really like to avoid potentially needing to reinstall the OS on this machine.

---

### Post by oldfred on 2011-06-17
Does the boot script now show a windows boot not the grub in sdc1's boot partition?

The windows way to fix it, if you have a windows repair CD is fixboot. The other commands may also repair something else that is wrong.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

You will need to reinstall grub2's boot loader to a MBR. It does not have to be sdc, if you want to keep the windows boot loader in sdc.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you have more than one drive, I prefer to have an operating system on each drive. I have windows on one, Ubuntu on one, and on my larger one several versions of Ubuntu and one or two others to play with.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate working one from drive to drive.

---

### Post by Quackers on 2011-06-17
I too know little of LVM2 but I notice from the boot script output that grub is installed to the sdc1 partition, which is a Windows partition. It shouldn't be there!
I would suggest that this needs repairing before Windows will boot.

Sorry oldfred! jmechy, please see above post!

---

### Post by jmechy on 2011-06-20
oldfred, tried all your suggestions (including the new part, running chkdsk), but saw no change in behavior.  Chkdsk did change the security identifies on literally every file on my windows partition though.  Also, it looks like my windows partition is on the D: drive, I can't remember if it had been D: or C: before.

---

### Post by oldfred on 2011-06-20
I would think it might only change to d: if you have another windows install and now you boot that first? The script did not parse several partitions, sdb1 - SFS is a windows only LVM and you had some errors or issues  in sdc6. 

Normally boot flag determines first windows to boot on a drive (C:) and BIOS sets which drive boots first if windows on different drives. But sometimes windows 7 will install boot files on one drive and the main install is on another. Often whichever windows you boot is C: and another NTFS partition is D:.

---

### Post by avi95 on 2011-06-23
Okay, please help me.
Till yesterday, I was dual booting Win 7 & Ubuntu 11.04 on my Dell Inspiron N4010. Ubuntu was giving me a few problems, so I decided to remove it.
I tried using EasyBCD
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I had installed BCD, but didn't get a chance to "Write MBR" as my brother shut down my laptop in the middle of the process.
This was the process I used :
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)

After that when I booted, I neither had GRUB nor MBR.
But thanks to Google & BootRepair([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) I was able to boot back to my Ubuntu Filesysytem.

The problem now is that Grub is now not showing my Win 7 boot option, instead its showing "Windows Vista" on sda 3 or something...
And when I click on that, it gives me an error saying some BCD file is missing.

I really want my Windows OS back & if possible, I don't want to re-install the entire OS.

PLEASE HELP !!!

---

