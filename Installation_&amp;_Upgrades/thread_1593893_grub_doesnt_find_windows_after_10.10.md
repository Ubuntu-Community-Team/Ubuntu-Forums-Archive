---
title: "grub doesnt find windows after 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by justin_3994 on 2010-10-11
Hello, i just built a new computer today, i have a 250gb hdd and a 160 hdd. i installed wind0ws 7 on the 250 and then ubuntu 10.10 on the 160. In the past (8.04-10.04) after install ubuntu on boot grub would give me the option to go into ubuntu or windows, now ti doesnt give me that option and boots directly into ubuntu. I dont even think it has recognized that windows is there. Please Help

---

### Post by VMC on 2010-10-11
> **justin_3994 said:**
> Hello, i just built a new computer today, i have a 250gb hdd and a 160 hdd. i installed wind0ws 7 on the 250 and then ubuntu 10.10 on the 160. In the past (8.04-10.04) after install ubuntu on boot grub would give me the option to go into ubuntu or windows, now ti doesnt give me that option and boots directly into ubuntu. I dont even think it has recognized that windows is there. Please Help

If you hold the Shift key down when you boot, do you then see the grub menu?

also have you check the values of /etc/default/grub?

---

### Post by justin_3994 on 2010-10-11
yes i do see the gub menu when holding shift on boot but there is no entry for windows 7 and i edited /etc/default/grub so the menu is no longer hidden by default

---

### Post by VMC on 2010-10-11
> **justin_3994 said:**
> yes i do see the gub menu when holding shift on boot but there is no entry for windows 7 and i edited /etc/default/grub so the menu is no longer hidden by default

What does it find using this command:

```
sudo os-prober
```

---

### Post by justin_3994 on 2010-10-11
> **VMC said:**
> What does it find using this command:

```
sudo os-prober
```

i get no results it pauses for a minute and then shows my username again

---

### Post by VMC on 2010-10-11
> **justin_3994 said:**
> i get no results it pauses for a minute and then shows my username again

OK, I think I see. You have dual hard drives. Lets get a better picture of what's going on. Download boot_into_script (see my "blue" link below. Its small and after download run it using sudo and output the RESULTS.txt file back here within CODES.

---

### Post by justin_3994 on 2010-10-11
this is the results.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        65c695c2-b21b-492a-bc1b-4d1fbb1c431a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ffebd407-4088-4f85-8e3d-ed7987c767e9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F642ED4942ED0EE5                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/MB SUPPORT CD     iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/F642ED4942ED0EE5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
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
    search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65c695c2-b21b-492a-bc1b-4d1fbb1c431a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65c695c2-b21b-492a-bc1b-4d1fbb1c431a ro single 
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
    search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65c695c2-b21b-492a-bc1b-4d1fbb1c431a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=ffebd407-4088-4f85-8e3d-ed7987c767e9 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
  56.0GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
  94.6GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
  94.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  89 14 24 e8 e8 f1 f9 ff  eb aa 8d b6 00 00 00 00  |..$.............|
00000010  89 14 24 e8 d8 f1 f9 ff  e9 d2 fe ff ff 8d 76 00  |..$...........v.|
00000020  89 14 24 e8 c8 f1 f9 ff  e9 0d ff ff ff 8d 76 00  |..$...........v.|
00000030  89 14 24 e8 b8 f1 f9 ff  e9 d8 fe ff ff 89 45 e4  |..$...........E.|
00000040  89 3c 24 e8 68 8b fc ff  8d 46 28 89 04 24 e8 bd  |.<$.h....F(..$..|
00000050  bf ff ff 8d 46 0c 89 04  24 e8 02 e1 fd ff 89 34  |....F...$......4|
00000060  24 e8 9a 3c 05 00 8b 45  e4 89 04 24 e8 2f f9 f9  |$..<...E...$./..|
00000070  ff 89 45 e4 eb d2 89 45  e4 eb e3 89 45 e4 66 90  |..E....E....E.f.|
00000080  eb d1 89 45 e4 89 3c 24  e8 53 ac ff ff eb c4 89  |...E..<$.S......|
00000090  45 e4 8d 47 0c 89 04 24  e8 43 ac ff ff eb a1 90  |E..G...$.C......|
000000a0  55 31 c0 89 e5 8b 55 08  8b 4a 1c 3b 4a 20 74 09  |U1....U..J.;J t.|
000000b0  8b 42 28 3b 42 2c 0f 95  c0 5d c3 90 8d 74 26 00  |.B(;B,...]...t&.|
000000c0  e8 21 24 fa ff 81 c1 2f  f3 1d 00 55 89 e5 5d c7  |.!$..../...U..].|
000000d0  81 34 1b 00 00 ff ff ff  7f 66 c7 81 38 1b 00 00  |.4.......f..8...|
000000e0  ff 7f 66 c7 81 3a 1b 00  00 ff 7f c7 81 3c 1b 00  |..f..:.......<..|
000000f0  00 ff ff ff 7f c7 81 40  1b 00 00 ff ff ff ff 66  |.......@.......f|
00000100  c7 81 44 1b 00 00 ff 7f  66 c7 81 46 1b 00 00 ff  |..D.....f..F....|
00000110  7f 66 c7 81 48 1b 00 00  ff 7f c7 81 4c 1b 00 00  |.f..H.......L...|
00000120  ff ff ff 7f 66 c7 81 50  1b 00 00 ff 7f 66 c7 81  |....f..P.....f..|
00000130  52 1b 00 00 ff 7f c3 90  90 8d b4 26 00 00 00 00  |R..........&....|
00000140  55 89 e5 83 ec 38 89 75  f8 8b 75 08 89 5d f4 8b  |U....8.u..u..]..|
00000150  4d 0c e8 70 23 fa ff 81  c3 9d f2 1d 00 89 7d fc  |M..p#.........}.|
00000160  0f b7 56 0c 0f b7 7e 10  89 0c 24 89 4d e4 89 54  |..V...~...$.M..T|
00000170  24 04 89 55 e0 e8 96 8c  05 00 8b 55 e0 89 54 24  |$..U.......U..T$|
00000180  04 89 04 24 e8 87 8c 05  00 89 7c 24 04 89 04 24  |...$......|$...$|
00000190  e8 7b 8c 05 00 89 7c 24  04 89 04 24 e8 6f 8c 05  |.{....|$...$.o..|
000001a0  00 8b 06 8b 4d e4 89 34  24 89 4c 24 04 ff 50 14  |....M..4$.L$..P.|
000001b0  8b 5d f4 8b 75 f8 8b 7d  fc 89 ec 5d c3 90 00 fe  |.]..u..}...]....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by wilee-nilee on 2010-10-11
Your missing the boot files, did you remove anything? it should look like this.

```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR="Red"]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe
```

You may be able to load these with the install dvd, I would unplug the Ubuntu HD to do it if possible though.

You can run the autorepair, three times is generally suggested. I'm not really if this will fix it but it may.

Here is the set of commands that are rumored to be run as part of the autorepair. This is just the manual method.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by justin_3994 on 2010-10-11
i didnt remove anything actually after windows installed i went and installed ubuntu...ill give the repair a try and see what happens.

---

### Post by justin_3994 on 2010-10-12
Ok so i figured it out, i cant believe i didnt think or do this first. All the previous time i unplugged the ubuntu hard drive when installing windows, that way the installer had only one place for all the files, then i would plug the other hdd back in and install ubuntu. So i just unplugged the ubuntu hdd and reinstalled windows then plugged it back in and installed ubuntu. grub now finds windows and works fine. Thank you for your help.

---

### Post by wilee-nilee on 2010-10-12
> **justin_3994 said:**
> Ok so i figured it out, i cant believe i didnt think or do this first. All the previous time i unplugged the ubuntu hard drive when installing windows, that way the installer had only one place for all the files, then i would plug the other hdd back in and install ubuntu. So i just unplugged the ubuntu hdd and reinstalled windows then plugged it back in and installed ubuntu. grub now finds windows and works fine. Thank you for your help.

Glad you got it worked out.;)

---

