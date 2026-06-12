---
title: "No grub after Ubuntu 11.10 installation"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Dearhell on 2012-01-12
I have Windows 7 and unallocated space.

I have tried to install Ubuntu three times, but the Grub menu doesn't appear. Ubuntu seems to be installed correctly, but when I boot my computer it starts directly Windows 7.

I have tried these options:

1. Install Ubuntu alongside Windows 7.
2. Manual Ubuntu installation, I select the unallocated space and make a ext4 partition and swap partition.

But the problem is the same.

Any suggestions?

---

### Post by kevdog on 2012-01-12
I just did a new install of Windows XP with 11.10 two days ago so maybe I can help.  I installed the OS's on different hard discs however.  Are you planning on doing the two installs on the same disc?  The tricky part about doing a dual boot install is planning how you need to do it, before you install any operating system.  This is important since you want to lay out in advance how you want to partition the hard drive(s).  Windows is always installed first, and then I used the ubuntu install to set up the /boot partition and then create a partition for Ubuntu (I actually created a few Ubuntu partitions /boot, /, /home, /swap).  I still believe Win7 is using NTFS.  I know within windows xp (so I assume its the same for Win7), there is a disc management utility that shows partitioning information and allows to resize partitions within the utility.  I can detect if there are other partitions (such as ext3/4), however it lists them as unknown since it doesn't understand ext3/4 journaling system.

---

### Post by Dearhell on 2012-01-12
I understand what you are saying but I think that my installation was properly planned.

The two installations are on the same HD.

I have a partition for Windows 7 in my HD (so is already installed first) and there is also unallocated (free) space for Ubuntu.

Also I don't need to resize anything.

But I still don't know why the Ubuntu 11.10 installation doesn't install grub, or if it is installed why it doesn't appear.

---

### Post by darkod on 2012-01-12
Follow the link in my signature and run the boot info script. Post the results as explained there. It will show more details what is going on.

---

### Post by Dearhell on 2012-01-12
There is more info, please tell me if it is needed. I only posted the summary because it seemed the more relevant part, otherwise the post would be too long.

```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files: 
```

---

### Post by drs305 on 2012-01-12
Grub appears to be installed on sda while your Ubuntu installation is on sdb.

You might get it to boot correctly by booting the LiveCD and then reinstalling Grub to sda with your Ubuntu partition mounted. While this isn't the normal way of doing things, it won't disturb the Windows bootloader currently installed on sdb - so it's worth a try.

Boot the LiveCD, then run these commands:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Don't use the partition number in the second command.

Again, this is a little odd, but it should work. Make sure your BIOS is set to boot sda first. If it doesn't work, we really need to see the entire contents of RESULTS.txt, or you can run the commands above but change the second command to install it to /dev/sdb rather than /dev/sdb. In this case though, it will overwrite the sdb Windows MBR information. This is ok as Grub can boot Windows and Ubuntu, but you should know you will  lose the Windows bootloader if you install Grub to sdb...

---

### Post by Dearhell on 2012-01-12
Ive just tried the commands but it didnt work, here is the full results.txt after doing it:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   897,103,843   896,896,996   7 NTFS / exFAT / HPFS
/dev/sdb3         897,103,870   976,769,023    79,665,154   5 Extended
/dev/sdb5         897,103,872   972,580,863    75,476,992  83 Linux
/dev/sdb6         972,582,912   976,769,023     4,186,112  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        420A5E150A5E05F7                       ntfs       secundario
/dev/sdb1        4E622BF0622BDC09                       ntfs       System Reserved
/dev/sdb2        1AEE2F04EE2ED831                       ntfs       
/dev/sdb5        b010142c-f3aa-4044-acb2-1c3356f875ba   ext4       
/dev/sdb6        740a8df4-52e1-47e4-ad44-255f78f2692d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
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
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=b010142c-f3aa-4044-acb2-1c3356f875ba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=b010142c-f3aa-4044-acb2-1c3356f875ba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root b010142c-f3aa-4044-acb2-1c3356f875ba
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 4E622BF0622BDC09
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=b010142c-f3aa-4044-acb2-1c3356f875ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=740a8df4-52e1-47e4-ad44-255f78f2692d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  66 6e f0 20 44 b2 1e 92  74 e6 7d a8 30 25 69 37  |fn. D...t.}.0%i7|
00000010  4e 7c 20 ea a0 65 9e 1c  7b e0 34 30 26 0a b0 7d  |N| ..e..{.40&..}|
00000020  2e a7 5e 47 93 65 34 7e  2a c3 78 88 cb 55 78 48  |..^G.e4~*.x..UxH|
00000030  fb 59 33 cd 4e 4a b5 37  99 33 83 23 f0 8c 7c c0  |.Y3.NJ.7.3.#..|.|
00000040  cc fd bb bc c4 85 46 4d  79 6a 48 bc b4 f2 67 20  |......FMyjH...g |
00000050  da e0 45 f8 51 b2 6c 42  25 88 d1 be b1 7f 19 07  |..E.Q.lB%.......|
00000060  47 77 23 8c e6 95 c4 68  31 bc b2 91 03 33 af 97  |Gw#....h1....3..|
00000070  85 8e 67 2e 28 53 40 ac  55 4d 42 a8 54 a0 62 31  |..g.(S@.UMB.T.b1|
00000080  94 3d 99 2d 11 99 dc 4b  c1 50 81 16 61 1d 78 81  |.=.-...K.P..a.x.|
00000090  4b 0c 99 b3 15 b9 3e 92  3a 03 6f 0b 73 5c a0 19  |K.....>.:.o.s\..|
000000a0  70 d1 40 f4 a9 64 4c a4  98 2c 95 23 f0 bd c7 2c  |p.@..dL..,.#...,|
000000b0  1f de c3 38 64 2d ad 16  1d 81 c1 84 d8 55 12 ae  |...8d-.......U..|
000000c0  c5 ac 80 46 15 1d 86 49  08 49 0c 3d 47 3f 45 c2  |...F...I.I.=G?E.|
000000d0  0a 15 13 bc 56 13 36 b4  b8 4f b1 a5 58 9e a8 27  |....V.6..O..X..'|
000000e0  a9 c2 c4 44 43 28 6c 9a  97 2a e8 42 49 9b c5 be  |...DC(l..*.BI...|
000000f0  7f f8 f5 12 f9 41 29 b1  c5 65 07 14 82 9f 15 4b  |.....A)..e.....K|
00000100  9c 99 bc bd 40 82 10 f4  36 6f 41 0e e0 26 26 65  |....@...6oA..&&e|
00000110  55 9f 83 c9 58 a8 91 1d  8c 22 67 80 75 08 c7 28  |U...X...."g.u..(|
00000120  4b 90 3d 54 df ac b1 ca  77 1c 1f 81 02 22 a0 61  |K.=T....w....".a|
00000130  f0 2a 38 8f 37 e6 2a 85  c3 61 90 60 d1 06 4c e1  |.*8.7.*..a.`..L.|
00000140  70 db 60 94 71 23 bb 73  b0 60 ae 0e 95 c1 9a 0e  |p.`.q#.s.`......|
00000150  3c ca 1b 4b f8 d1 45 af  3c 5c 14 9d 2b a6 6e 77  |<..K..E.<\..+.nw|
00000160  03 28 9b f8 43 f8 4e 54  55 4f 5c e8 27 d8 80 76  |.(..C.NTUO\.'..v|
00000170  29 67 c8 2a a0 f0 21 6b  03 07 2a ae 9c 3b 5e 77  |)g.*..!k..*..;^w|
00000180  07 33 3b 3c 05 68 b1 f2  30 22 71 10 f2 e7 20 05  |.3;<.h..0"q... .|
00000190  1a ab e5 85 50 32 c4 4d  09 16 7f c4 7f 03 35 a5  |....P2.M......5.|
000001a0  03 c2 46 c6 55 88 f0 42  6b 26 bf 98 c0 d4 ab 13  |..F.U..Bk&......|
000001b0  af 13 63 b1 21 e0 ee 00  b5 9f 43 24 af 64 00 fe  |..c.!.....C$.d..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 7f 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b0  7f 04 00 e8 3f 00 00 00  |............?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

If possible I would prefer not to eliminate the Windows bootloader in case I cant enter using grub.

---

### Post by drs305 on 2012-01-12
The full RESULTS.txt most likely confirms my suspicion that your BIOS can't see your Grub boot files. The reason is that the BIOS probably can only read the first 137GB of the drive. Since you have system and Grub files deeper into your drive Grub 2 can't find them.

Once the system boots (even from a LiveCD), OS's can see the files and everything appears normal.

You can confirm this if you are getting the Grub prompt during boot. Type the following commands. You may have to change (hd0,2) to (hd0,1) if the system reverses the drive designations.
```

ls (hd1,5)/ # A working system should find *vmlinux* and *initrd.img*
ls (hd1,5)/boot  # A normal system will display your vmlinuz... and initrd... files
ls (hd1,5)/boot/grub # A normal system should display lots of *.mod files, as well as grub.cfg
```

Please run these commands and tell us what happens.

---

### Post by Dearhell on 2012-01-12
> You can confirm this if you are getting the Grub prompt during boot

I dont see the grub prompt during boot, Windows just boots normally like before I installed Ubuntu.

Those three commands give the same syntax error:

```
ubuntu@ubuntu:~/Downloads/boot_info_script060$ ls (hd1,5)/
bash: syntax error near unexpected token `('

```

May be I didnt understand your explanation correctly, please tell me what Im doing wrong.

---

### Post by darkod on 2012-01-12
Did you try to boot from the other disk?

If you have grub2 on sda, and if you keep booting from sdb you will always boot directly into windows.

It might work just by switching the hdd boot order.

Later you can decide whether you want to keep the windows bootloader on sdb or not.

---

### Post by Dearhell on 2012-01-12
> **darkod said:**
> Did you try to boot from the other disk?

If you have grub2 on sda, and if you keep booting from sdb you will always boot directly into windows.

It might work just by switching the hdd boot order.

Later you can decide whether you want to keep the windows bootloader on sdb or not.

I dont understand, both Windows and Ubuntu are installed in the same physical disk (sdb in this case).

Anyway, how can I try to switch the hdd boot order?

In my bios boot options I can only choose boot from HD, boot from CD, boot from USB ...

---

### Post by darkod on 2012-01-12
> **Dearhell said:**
> I dont understand, both Windows and Ubuntu are installed in the same physical disk (sdb in this case).

Anyway, how can I try to switch the hdd boot order?

In my bios boot options I can only choose boot from HD, boot from CD, boot from USB ...

It doesn't matter where the OS is, but where the bootloader is. In your case grub2 is on sda.

In the BIOS there should be two types of options (but not in all BIOSes). One is for order of devices, HDD, CD-ROM, USB, etc. And look around for another setting, the order of HDDs. Because more and more people have more than one hdd, it still needs to know which one to boot from first. So there is another setting selecting the order of the disks.

Another option: install grub2 on sdb too. Boot with the ubuntu cd in live mode and in terminal:
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

Restart and see if you get the grub menu.

---

### Post by matza55 on 2012-01-14
> **darkod said:**
> Did you try to boot from the other disk?

If you have grub2 on sda, and if you keep booting from sdb you will always boot directly into windows.

It might work just by switching the hdd boot order.

Later you can decide whether you want to keep the windows bootloader on sdb or not.

Is there not a good idé to defragment Windows first? Don't help with this problem but......

---

