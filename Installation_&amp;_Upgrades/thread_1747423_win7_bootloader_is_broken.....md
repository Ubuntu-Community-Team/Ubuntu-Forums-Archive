---
title: "win7 bootloader is broken...."
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by GibsonSGKing on 2011-05-02
I had vista installed, then I installed Win7 on a dif. partition. Then I installed Ubuntu 11.4 over the vista partition (formatted first), and now I can't get into Win7. I'm really at a loss. I've tried the Win7 disk, and it doesn't detect the Win7 installation. I've also tried sudo update-grub, and it doesn't seem to detect the win7 install either. I've tried making the Win7 partition bootable using gpart as well. Can someone please give me some help here? I'd like to dual boot Win7 and Ubuntu, however I need to do that. Thanks for any and all help.

---

### Post by coffeecat on 2011-05-02
Windows 7 *probably* installed its boot files to the Vista partition, and then these were lost when you reformatted the Vista partition for Ubuntu 11.04. Which would explain why running update-grub doesn't detect the Win7 partition. But rather than me speculate, let's investigate.

Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as instructed there and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Then we'll be able to see what the situation is.

---

### Post by GibsonSGKing on 2011-05-02
> **coffeecat said:**
> Windows 7 *probably* installed its boot files to the Vista partition, and then these were lost when you reformatted the Vista partition for Ubuntu 11.04. Which would explain why running update-grub doesn't detect the Win7 partition. But rather than me speculate, let's investigate.

Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as instructed there and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Then we'll be able to see what the situation is.

Will do. Also, that's sort of what I was speculating, because when I tried to use a program to make an image of the Win7 partition, it was going to force me to make an image of the vista partition as well because there was some sort of info on it that win7 needed to operate, if I remember correctly.

---

### Post by GibsonSGKing on 2011-05-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

/dev/sda1                  63   965,404,359   965,404,297  83 Linux
/dev/sda2         965,404,670 1,953,503,999   988,099,330   f W95 Ext d (LBA)
/dev/sda5    *  1,023,999,228 1,953,503,999   929,504,772   7 HPFS/NTFS
/dev/sda6         965,404,672 1,023,997,951    58,593,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d4ca95bf-11dd-475c-9757-4654c549a9c9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        E6A0DE3CA0DE12C3                       ntfs                                     
/dev/sda6        7ddf1339-bf97-49c4-a4f9-8a6659051dca   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        80F05B48F05B4396                       ntfs       My Book 3.0                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/My Book 3.0       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=d4ca95bf-11dd-475c-9757-4654c549a9c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=d4ca95bf-11dd-475c-9757-4654c549a9c9 ro single 
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d4ca95bf-11dd-475c-9757-4654c549a9c9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# swap was on /dev/sda6 during installation
UUID=7ddf1339-bf97-49c4-a4f9-8a6659051dca none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  49.5GB: boot/grub/core.img
 253.6GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.38-8-generic-pae
    .6GB: boot/vmlinuz-2.6.38-8-generic-pae
   1.4GB: initrd.img
    .6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  40 08 00 00 20 02 00 fa  1a 1b 00 00 00 00 00 00  |@... ...........|
00000010  60 10 20 00 28 b8 be f5  1a 1b 00 00 00 00 00 00  |`. .(...........|
00000020  a2 18 20 08 5a d5 0d b5  1a 1b 00 00 00 00 00 00  |.. .Z...........|
00000030  a1 18 40 08 7d 3f 38 5e  1a 1b 00 00 00 00 00 00  |..@.}?8^........|
00000040  03 21 20 08 fd 02 aa 55  1a 1b 00 00 00 00 00 00  |.! ....U........|
00000050  03 21 40 08 5f 60 6a 55  1a 1b 00 00 00 00 00 00  |.!@._`jU........|
00000060  a1 10 20 08 af ff 38 dc  1a 1b 00 00 00 00 00 00  |.. ...8.........|
00000070  a1 18 00 00 ff bf bc fe  1a 1b 00 00 00 00 00 00  |................|
00000080  61 10 20 00 ea 8a 8f f5  1a 1b 00 00 00 00 00 00  |a. .............|
00000090  61 10 00 00 82 f7 ff f7  1a 1b 00 00 00 00 00 00  |a...............|
000000a0  40 08 00 00 ea 82 8a 6a  1a 1b 00 00 00 00 00 00  |@......j........|
000000b0  41 08 00 00 f5 bc d7 79  1a 1b 00 00 00 00 00 00  |A......y........|
000000c0  60 10 00 00 d5 df 7a c3  1a 1b 00 00 00 00 00 00  |`.....z.........|
000000d0  81 10 00 00 0b 2b fd 55  1a 1b 00 00 00 00 00 00  |.....+.U........|
000000e0  a1 18 00 00 0a af f5 55  1a 1b 00 00 00 00 00 00  |.......U........|
000000f0  81 18 00 00 a0 2a b5 fd  1a 1b 00 00 00 00 00 00  |.....*..........|
00000100  a1 18 20 00 a2 e2 78 5f  1a 1b 00 00 00 00 00 00  |.. ...x_........|
00000110  81 10 20 08 b5 9f bb 2b  1a 1b 00 00 00 00 00 00  |.. ....+........|
00000120  a1 18 00 00 2a 28 2f df  1a 1b 00 00 00 00 00 00  |....*(/.........|
00000130  61 10 00 00 5e 5c 7a ea  1a 1b 00 00 00 00 00 00  |a...^\z.........|
00000140  20 08 00 00 fd 55 55 57  1a 1b 00 00 00 00 00 00  | ....UUW........|
00000150  20 08 00 00 05 25 35 df  1a 1b 00 00 00 00 00 00  | ....%5.........|
00000160  40 08 00 00 5e 5a 58 ff  1a 1b 00 00 00 00 00 00  |@...^ZX.........|
00000170  80 10 00 00 55 55 b5 29  1a 1b 00 00 00 00 00 00  |....UU.)........|
00000180  a1 18 00 00 d5 b5 fe a8  1a 1b 00 00 00 00 00 00  |................|
00000190  e2 20 40 08 d5 5d bb 3a  1a 1b 00 00 00 00 00 00  |. @..].:........|
000001a0  04 21 81 10 d5 f5 80 c0  1a 1b 00 00 00 00 00 00  |.!..............|
000001b0  a2 18 20 08 dc 5c 98 a8  1a 1b 00 00 00 00 80 01  |.. ..\..........|
000001c0  c1 ff 07 fe ff ff fe 14  7e 03 04 1e 67 37 00 fe  |........~...g7..|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 10 7e 03 00 00  |............~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

That's about what happened when I tried to rebuild GRUB, no Win7 entry to be found :S

EDIT: Wait a sec, it's right there, and even the XP info from ages ago :O
Surely this is a good sign, no?

---

### Post by coffeecat on 2011-05-02
Yes, it's more or less as expected, but slightly more tricky to fix.

Your Win7 partition is on sda5 which is a logical partition which adds another degree of complexity. Although it has the boot flag set, you will never be able to boot from it because Windows cannot boot from a logical partition. It can only use a logical partition for its C: partition if the boot files (and boot flag) are on a primary partition. The Windows 7 boot files were originally on sda1 (when it was the Vista partition) because your boot script output says this:
```

sda5: 
_________________________________________________________________________ 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  [COLOR="Red"]According to the info in the boot sector, sda5 starts
                         at sector 63[/COLOR].
     Operating System:  Windows 7
     Boot files/dirs:   /Windows/System32/winload.exe
```

And sector 63 is the start sector of sda1.

The only way to fix this is to create a small primary partition for the Win7 boot files. You will need a Win7 installation DVD or repair CD to write these. Also - something will have to be done about the sda5 boot sector looking to sector 63. Whether the Windows bootrec utility on the Win7 disc can do this, I don't know.

I'm not sure exactly how to proceed. This problem comes up regularly, but I've never seen it resolved, or I've never seen an OP confirming that they've resolved it.

---

### Post by GibsonSGKing on 2011-05-02
> **coffeecat said:**
> Yes, it's more or less as expected, but slightly more tricky to fix.

Your Win7 partition is on sda5 which is a logical partition which adds another degree of complexity. Although it has the boot flag set, you will never be able to boot from it because Windows cannot boot from a logical partition. It can only use a logical partition for its C: partition if the boot files (and boot flag) are on a primary partition. The Windows 7 boot files were originally on sda1 (when it was the Vista partition) because your boot script output says this:
```

sda5: 
_________________________________________________________________________ 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  [COLOR="Red"]According to the info in the boot sector, sda5 starts
                         at sector 63[/COLOR].
     Operating System:  Windows 7
     Boot files/dirs:   /Windows/System32/winload.exe
```

And sector 63 is the start sector of sda1.

The only way to fix this is to create a small primary partition for the Win7 boot files. You will need a Win7 installation DVD or repair CD to write these. Also - something will have to be done about the sda5 boot sector looking to sector 63. Whether the Windows bootrec utility on the Win7 disc can do this, I don't know.

I'm not sure exactly how to proceed. This problem comes up regularly, but I've never seen it resolved, or I've never seen an OP confirming that they've resolved it.
Oh jeez. That sounds really bad. Is there any way to change it so that the Win7 partition is where it boots from? So I can untangle all of this? Even if I maybe have to reinstall 7?

---

### Post by coffeecat on 2011-05-02
I can see two possible ways of doing this.

1 - Shrink the sda1 partition so that you can create a small primary partition for the Windows boot files, but exactly how you install the Windows boot files to the new partition, I don't know, as I said before. Perhaps someone else will be able to advise - there must be a way.

2 - Re-install Windows, but you'd have to create a primary partition for it. Logical partitions and Windows are more trouble than they're worth. Your current sda5 partition - being a logical - is the problem here. You'd need to remove or shrink the current extended partition so that you could create a new primary partition large enough for Windows. If that means losing your sda6 swap partition even temporarily, then you'd need to edit your Ubuntu /etc/fstab to stop Ubuntu complaining.

Unfortunately, you have Ubuntu and Windows both on inconvenient partitions at the moment. Ubuntu doesn't need to be on a primary partition, but it is. Windows needs to be on a primary partition, but it isn't. If you eventually decide on a complete re-install of both OSs, then put Windows on sda1. That's where it's happiest. Then you could put everything else on logicals within one extended partition.

---

### Post by GibsonSGKing on 2011-05-02
> **coffeecat said:**
> I can see two possible ways of doing this.

1 - Shrink the sda1 partition so that you can create a small primary partition for the Windows boot files, but exactly how you install the Windows boot files to the new partition, I don't know, as I said before. Perhaps someone else will be able to advise - there must be a way.

2 - Re-install Windows, but you'd have to create a primary partition for it. Logical partitions and Windows are more trouble than they're worth. Your current sda5 partition - being a logical - is the problem here. You'd need to remove or shrink the current extended partition so that you could create a new primary partition large enough for Windows. If that means losing your sda6 swap partition even temporarily, then you'd need to edit your Ubuntu /etc/fstab to stop Ubuntu complaining.

Unfortunately, you have Ubuntu and Windows both on inconvenient partitions at the moment. Ubuntu doesn't need to be on a primary partition, but it is. Windows needs to be on a primary partition, but it isn't. If you eventually decide on a complete re-install of both OSs, then put Windows on sda1. That's where it's happiest. Then you could put everything else on logicals within one extended partition.
I just installed linux, so I'm ok with reinstalling that. I'm plenty experienced with windows installs. There isn't really any personal data to lose, so if I wipe the entire drive, how exactly should I go about re doing everything? This is sort of more trouble than it's worth atm.

---

### Post by coffeecat on 2011-05-02
Well - it's Windows that's being the trouble with its primary partition limitation. I don't really see how I can add much to what I said: Windows on sda1, and everything else on logical partitions. My preference would be to wipe the drive with Gparted from the live Ubuntu CD and make one primary NTFS partition for Windows, leaving the rest unallocated. Then I would start the Windows installer and install it to the partition created with Gparted. Once Windows is up and running I would use the live CD again to create the rest of my partitions and to install Ubuntu. If you create the Windows partition with the Windows installer, I believe you can set the size, but the Win7 installer defaults to setting up two partition: a ~100MB boot ("System") partition and the larger C: one.

You might find this link helpful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by GibsonSGKing on 2011-05-02
> **coffeecat said:**
> Well - it's Windows that's being the trouble with its primary partition limitation. I don't really see how I can add much to what I said: Windows on sda1, and everything else on logical partitions. My preference would be to wipe the drive with Gparted from the live Ubuntu CD and make one primary NTFS partition for Windows, leaving the rest unallocated. Then I would start the Windows installer and install it to the partition created with Gparted. Once Windows is up and running I would use the live CD again to create the rest of my partitions and to install Ubuntu. If you create the Windows partition with the Windows installer, I believe you can set the size, but the Win7 installer defaults to setting up two partition: a ~100MB boot ("System") partition and the larger C: one.

You might find this link helpful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Ok. I probably should have worded that a bit better, I just meant to ask what order I should go with. Sounds good though. Will ubuntu recognize the windows install and put it in the Grub loader for me?

---

### Post by MAFoElffen on 2011-05-02
> **GibsonSGKing said:**
> Oh jeez. That sounds really bad. Is there any way to change it so that the Win7 partition is where it boots from? So I can untangle all of this? Even if I maybe have to reinstall 7?
Just what I would do... and it  would be a bit of work:

You know that Windows OS'es like to live ifn the lower half of HHD's and get quarky when the y are not, right?

If you deleted the first partition, you could move your Win7 partition to be first, starting it after the first sector, not on the first sector.  (Prevents problems later with Grub this way.) You could then mark it as bootable.  Then boot from a Win7 disk and sys it:
    [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
That way, you wouldn't have to reinstall Win7.

Then you could reinstall linux in a new partition that you can create after that partition.

Sorry, I don't know of any utilities to "move" the physicall and loigal order of a partition and it's data... that would prevent a reinstall of one-- but since 11.04 is a new fresh install... that would be ht elogical choice.  Install grub in sda and it will pick up the Win7.

---

### Post by coffeecat on 2011-05-02
Oh yes. Definitely Windows first. Windows will overwrite grub in the mbr if you install it second, whereas the Ubuntu installer will detect Windows if it is already there and set you up with a dual-booting menu. So yes, Ubuntu will detect Windows so long as the Windows partition has Windows boot files in it. Which it will with a fresh install, and which is your problem at the moment.

By the way, just one thing to add to my suggestion to make a partition for Windows and to leave the rest of the HD unallocated until after you have installed Windows. This is because, in certain circumstances, the Windows installer can create havoc in the partition table when there are logical partitions present.

Good luck!

---

### Post by GibsonSGKing on 2011-05-02
Well, I'm going to do it right now. Hopefully I don't forget to back anything up. Is there anything I should learn from this? :P
I really don't want to make this mistake again. To be perfectly honest, I really don't understand what the difference is between the different types of partitions. Could you maybe explain a bit? Or possible point me to some resources? 
Also, thanks a lot for your help, I've been attempting to fix this for days...

---

### Post by oldfred on 2011-05-02
Coffeecat gave you a good link on partitions, I think it is the second page that starts to explain partition types.

My suggestion  (and each of us has at least one, and none are really wrong) 

Create a 30-50GB primary NTFS partition which should be sda1. It must also have boot flag for installer to see it. Unless you are planning on encryption, you do not need the separate boot partition that windows otherwise creates.

Also create another primary NTFS for data that you may want to share between Windows & Ubuntu. It is best to only read from a foreign system (windows or Ubuntu) and create the shared NTFS for read/write.

After windows is working, then using gparted create a large extended partition which is a container for all the logical. This should then be sda3 and we do not use sda4 in case you need a primary in the future.
All the logical partitions will start at sda5 & up.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint /  logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

How to actually make the partitions:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by GibsonSGKing on 2011-05-02
> **oldfred said:**
> Coffeecat gave you a good link on partitions, I think it is the second page that starts to explain partition types.

My suggestion  (and each of us has at least one, and none are really wrong) 

Create a 30-50GB primary NTFS partition which should be sda1. It must also have boot flag for installer to see it. Unless you are planning on encryption, you do not need the separate boot partition that windows otherwise creates.

Also create another primary NTFS for data that you may want to share between Windows & Ubuntu. It is best to only read from a foreign system (windows or Ubuntu) and create the shared NTFS for read/write.

After windows is working, then using gparted create a large extended partition which is a container for all the logical. This should then be sda3 and we do not use sda4 in case you need a primary in the future.
All the logical partitions will start at sda5 & up.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint /  logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

How to actually make the partitions:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Ok. I think I'm going to do what Coffeecat said, mainly because your suggestion seems like a lot of different partitions. Thank you for the advice though, I will definitely keep it in mind as an alternative. Also, I have 4GB of RAM, so I don't think a swap space is that hugely important for this system (also, it boots in around 20 seconds, so that's no biggie).

Thank you guys for all of your help though, really :)

---

### Post by GibsonSGKing on 2011-05-02
New problem. I thought I formatted everything, but now I'm getting
"error: unknown filesystem.
grub rescue>"
Whenever I put the win7 disk in

What did I do wrong? I followed coffeecats instructions :S

Edit: Jeeze, no I reformatted it in NTFS and it's starting the windows installer..... hopefully I won't have any more issues

---

### Post by coffeecat on 2011-05-03
> **GibsonSGKing said:**
> New problem. I thought I formatted everything, but now I'm getting
"error: unknown filesystem.
grub rescue>"
Whenever I put the win7 disk in

What did I do wrong? I followed coffeecats instructions :S

Edit: Jeeze, no I reformatted it in NTFS and it's starting the windows installer..... hopefully I won't have any more issues

Sounds like you sorted it out, but fyi, the grub rescue error message was because the system was trying to boot from the HD. You needed to set the BIOS to boot from the optical drive for the Win7 disc to boot.

---

### Post by satanselbow on 2011-05-03
Could I just chip in that it can save a hell of a lot of head scratching and ghost hunting later on if before you start reinstalling ubuntu (regardless which flavour) you use gparted on a live CD to align the "main" NTFS partition created by the W7 installer to "cylinder" - usually /sda2 and the one you will be booting windows from in grub later.

It only takes a few seconds and can make life so much simpler when you  come to creating your extended partition for ubuntu - likewise ensure  you align ALL you ubuntu partitions to cylinder at creation ;) Don't be tempted to use the windows tools for partition creation as they fail to adhere to the long established standards (with regards to boundaries) that ubuntu/linux strive hard to maintain.

You can avoid the creation of the 1st 100MB W7 partition by preformatting a NTFS partition (which it looks like you have done anyway) thus saving 25% of your available primary partition allocation - removing it (the 100MB) once it has been created can have dire consequences as it contains your W7 boot files :(


... good luck!

---

### Post by oldfred on 2011-05-03
I agree with satanselbow on your not needing the windows boot partition. They created it to allow encrypting the main install as the boot could not be encrypted. Also some advantage to having recovery on a partition vs. having to use repairCD to fix errors. 
But I do not agree on cylinder alignment. While versions of fdisk report that cylinders are not aligned, cylinders have not been used since hard drives got over 8GB. Drives use LBA and CHS is not used now. satanselbow may be thinking of the new alignment on 1MiB.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by coffeecat on 2011-05-03
@GibsonSGKing, with regard to this alignment to 1MiB, if you are using the 10.10 or 11.04 CD, the version of Gparted used in those releases will default to that for you. So the 10.10 and 11.04 versions of Gparted are just fine for creating a partition for Windows 7. I've done that myself - Windows 7 is happy.

---

### Post by satanselbow on 2011-05-03
> **oldfred said:**
> While versions of fdisk report that cylinders are not aligned, cylinders have not been used since hard drives got over 8GB. Drives use LBA and CHS is not used now. satanselbow may be thinking of the new alignment on 1MiB

yeah... i am that old :D gone all nostalgic now - 8GB was H-U-G-E! :popcorn:

---

