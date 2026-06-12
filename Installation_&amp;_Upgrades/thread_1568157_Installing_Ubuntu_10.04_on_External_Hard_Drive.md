---
title: "Installing Ubuntu 10.04 on External Hard Drive"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by joseb on 2010-09-04
So im Trying to Install Ubuntu 10.04 on my External Hardrive

My Motherboard's BIOS does let me boot from a USB Hard Drive (Im Booting Ubuntu from a USB Pen Drive)

So Before I Finish the Graphical Installation I go to Options and choose to Install the Boot Loader(Grub) to /dev/sda , and Everything Worked Great

BUT when I re-booted from the Hard Drive, I got to a black screen with a grub> command  prompt. And Had no Clue what to do from there

ANY HELP PLEASE??

---

### Post by presence1960 on 2010-09-04
Grub is installed on the MBR of your internal hard disk but it looks for the boot files on your Ubuntu partition. if you have GRUB on the internal hard disk you must have the external plugged in every time you boot.

If you put Grub on the MBR of the external drive and repair the internal drive's MBR to windows you will not have that problem when you boot without the external disk.

Before giving you directions I need some info about your boot process and set up. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external plugged in.. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by joseb on 2010-09-04
Here are the Results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 407174320 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8065 MB, 8065646080 bytes
255 heads, 63 sectors/track, 980 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,753,212    15,753,150   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   966,213,631   966,211,584  83 Linux
/dev/sdb2         966,215,678   976,773,119    10,557,442   5 Extended
/dev/sdb5         966,215,680   976,773,119    10,557,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        293F-14ED                              vfat       UNTITLED 1                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        650b1193-ab7f-4b4a-9149-6c36c5dd1068   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2cc212b9-9f64-4352-b67d-a935546d4e36   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/650b1193-ab7f-4b4a-9149-6c36c5dd1068 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=650b1193-ab7f-4b4a-9149-6c36c5dd1068 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=650b1193-ab7f-4b4a-9149-6c36c5dd1068 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 650b1193-ab7f-4b4a-9149-6c36c5dd1068
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2cc212b9-9f64-4352-b67d-a935546d4e36 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 208.4GB: boot/grub/core.img
 182.6GB: boot/grub/grub.cfg
 208.5GB: boot/initrd.img-2.6.32-24-generic
 208.4GB: boot/vmlinuz-2.6.32-24-generic
 208.5GB: initrd.img
 208.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ea 96 5c 86 57 e7 73 12  62 7a de 68 d4 2e b4 ea  |..\.W.s.bz.h....|
00000010  9b 9d 45 1b 90 e4 96 40  f8 82 04 32 51 ee 5a 9a  |..E....@...2Q.Z.|
00000020  10 cb bf e5 00 a1 2f 4c  24 e9 66 95 c8 bf ef e1  |....../L$.f.....|
00000030  c8 ad d1 90 b2 91 89 28  af c6 1e 72 8b ac 2e c5  |.......(...r....|
00000040  df ed 76 06 1f 8b 73 55  77 9d 95 5e 9b 5b fb 9e  |..v...sUw..^.[..|
00000050  7c 49 74 72 49 56 6d aa  45 cc 09 16 da 3e 1b cb  ||ItrIVm.E....>..|
00000060  a4 ff 79 2e 02 0f 38 fb  7f 1a 67 db 2b fd 33 e1  |..y...8...g.+.3.|
00000070  6c b5 75 72 b2 81 0f 7b  e7 61 ef fc e1 f7 ce ce  |l.ur...{.a......|
00000080  e7 a2 6e e6 0e ae f9 f3  0c 7a 61 1f 47 6b 0f 3b  |..n......za.Gk.;|
00000090  ea 61 47 3d 9c 46 ab ed  b1 8f bf 2e fc f6 00 b2  |.aG=.F..........|
000000a0  88 d7 05 98 62 f5 4b 8b  1e f8 65 f7 15 27 53 8a  |....b.K...e..'S.|
000000b0  94 77 af 21 69 1a 5e dd  3f dc fb 08 4c b0 6d e4  |.w.!i.^.?...L.m.|
000000c0  c3 ae 41 cc 89 b2 c8 7a  9e b3 2a a2 9d 68 93 e7  |..A....z..*..h..|
000000d0  a2 7c bc ed a8 25 ba 94  bb b1 37 b6 2a c4 6c 70  |.|...%....7.*.lp|
000000e0  f7 4a 20 b8 2a cd 70 25  8a c7 2c 97 ad 74 cd c4  |.J .*.p%..,..t..|
000000f0  7e eb 58 34 fe fe cd fd  fa d0 4b 0a bf d7 ed aa  |~.X4......K.....|
00000100  fb f7 6f 3e c1 fd ca 05  48 c6 7a d4 9c b2 62 fa  |..o>....H.z...b.|
00000110  ef ef 34 5a 0f a3 ee 70  d6 0b c4 b7 c9 b4 e7 4f  |..4Z...p.......O|
00000120  06 95 ab ef dc b8 30 4e  45 dd 25 d5 e9 dd 38 48  |......0NE.%...8H|
00000130  e6 a3 11 41 62 2c 54 75  18 b3 42 04 e9 73 c6 c3  |...Ab,Tu..B..s..|
00000140  61 7c 43 bc 47 b2 70 8e  bc c8 64 1a 0f 83 88 f5  |a|C.G.p...d.....|
00000150  21 4e 1b 2d f1 75 e5 6f  85 04 fd 1a 93 41 f9 4a  |!N.-.u.o.....A.J|
00000160  22 5b 97 4c 27 b3 2e 1a  be c7 03 0f e5 3e 6f 91  |"[.L'........>o.|
00000170  e7 eb 3d db 3f 68 8a 4d  b1 b1 39 e9 26 f1 38 88  |..=.?h.M..9.&.8.|
00000180  8a 62 c3 ca b9 89 0a 17  f4 85 0d c2 4f 28 59 dc  |.b..........O(Y.|
00000190  f5 f0 2b ec c2 ea f3 27  62 33 10 1b 63 48 90 22  |..+....'b3..cH."|
000001a0  b9 1c b7 39 e6 07 00 aa  29 dc 85 c3 59 9f cb e3  |...9....)...Y...|
000001b0  57 e1 6b 3c 9a 1d 18 e8  e5 97 02 d0 92 41 00 fe  |W.k<.........A..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 18 a1 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```BTW I when I did the Test I had my External Hard Drive Connected where I tried to Install Ubuntu but Failed when Booting from It. Also I don't have an internal hard drive connected to my mobo I plan to always have the External and Boot from It Every time I want to use the Mobo

The Mobo is an AT3IONT-I
Running an Atom 330 @ 1.6 GHz
and an NViDIA iON

(I also attached the Results.txt File)

---

### Post by presence1960 on 2010-09-04
```
=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR="Red"]/dev/sdc1       /               ext4    errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sdc5 during installation
UUID=2cc212b9-9f64-4352-b67d-a935546d4e36 none            swap    sw              0 
```

The red above from your /etc/fstab concerns me. You need to edit that. boot from the Live CD/USB. Boot to the desktop. Open a terminal and run ```
gksu nautilus
``` Navigate to your /etc/fstab file and open it. Change the line in red above to:

```
# root was on /dev/sdb1 during installation
UUID=650b1193-ab7f-4b4a-9149-6c36c5dd1068  /               ext4    errors=remount-ro 0       1 
```
P.S. Scroll the scroll bar above to get complete info to enter into the line in fstab.

Click Save on toolbar at top. Close file. Now in terminal run ```
sudo mount /dev/sdb1 /mnt
```This will mount your ubuntu root (/) partition.

Now in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of external.

Reboot without Live CD/USB. Go into BIOS and set USB as first device to boot in the boot order. Save changes to CMOS and continue booting.

Or at reboot hit F9 or whatever key gives your machine the choice to choose a boot device and pick the external hard disk.

Either way you should get GRUB and choose Ubuntu.

**_Note: your fstab file will not be under FileSystem in nautilus, that is your Live CD file system. Your /etc/fstab will be under your external hard disk name on the left pane of nautilus. Edit that file. You may have to mount the external prior to running gksu nautilus by going to Places > Computer and clicking on your external hard disk in the left pane, then run gksu nautilus_**

---

### Post by joseb on 2010-09-04
Hey Sorry but I accidentaly Erased the External Hard Drive so I reinstalled Ubuntu on the Hard Drive and tried to boot from It and well it didnt work 

Here is the Results.txt If you can please check them again Thanks :D

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8065 MB, 8065646080 bytes
255 heads, 63 sectors/track, 980 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,753,212    15,753,150   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   966,213,631   966,211,584  83 Linux
/dev/sdb2         966,215,678   976,773,119    10,557,442   5 Extended
/dev/sdb5         966,215,680   976,773,119    10,557,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        293F-14ED                              vfat       UNTITLED 1                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7b30a16f-cf79-49bc-aa2a-9888dd68bd15   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2cc212b9-9f64-4352-b67d-a935546d4e36   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/7b30a16f-cf79-49bc-aa2a-9888dd68bd15 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7b30a16f-cf79-49bc-aa2a-9888dd68bd15 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7b30a16f-cf79-49bc-aa2a-9888dd68bd15 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7b30a16f-cf79-49bc-aa2a-9888dd68bd15
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7b30a16f-cf79-49bc-aa2a-9888dd68bd15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2cc212b9-9f64-4352-b67d-a935546d4e36 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 326.5GB: boot/grub/core.img
 427.5GB: boot/grub/grub.cfg
 326.5GB: boot/initrd.img-2.6.32-24-generic
 326.5GB: boot/vmlinuz-2.6.32-24-generic
 326.5GB: initrd.img
 326.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ea 96 5c 86 57 e7 73 12  62 7a de 68 d4 2e b4 ea  |..\.W.s.bz.h....|
00000010  9b 9d 45 1b 90 e4 96 40  f8 82 04 32 51 ee 5a 9a  |..E....@...2Q.Z.|
00000020  10 cb bf e5 00 a1 2f 4c  24 e9 66 95 c8 bf ef e1  |....../L$.f.....|
00000030  c8 ad d1 90 b2 91 89 28  af c6 1e 72 8b ac 2e c5  |.......(...r....|
00000040  df ed 76 06 1f 8b 73 55  77 9d 95 5e 9b 5b fb 9e  |..v...sUw..^.[..|
00000050  7c 49 74 72 49 56 6d aa  45 cc 09 16 da 3e 1b cb  ||ItrIVm.E....>..|
00000060  a4 ff 79 2e 02 0f 38 fb  7f 1a 67 db 2b fd 33 e1  |..y...8...g.+.3.|
00000070  6c b5 75 72 b2 81 0f 7b  e7 61 ef fc e1 f7 ce ce  |l.ur...{.a......|
00000080  e7 a2 6e e6 0e ae f9 f3  0c 7a 61 1f 47 6b 0f 3b  |..n......za.Gk.;|
00000090  ea 61 47 3d 9c 46 ab ed  b1 8f bf 2e fc f6 00 b2  |.aG=.F..........|
000000a0  88 d7 05 98 62 f5 4b 8b  1e f8 65 f7 15 27 53 8a  |....b.K...e..'S.|
000000b0  94 77 af 21 69 1a 5e dd  3f dc fb 08 4c b0 6d e4  |.w.!i.^.?...L.m.|
000000c0  c3 ae 41 cc 89 b2 c8 7a  9e b3 2a a2 9d 68 93 e7  |..A....z..*..h..|
000000d0  a2 7c bc ed a8 25 ba 94  bb b1 37 b6 2a c4 6c 70  |.|...%....7.*.lp|
000000e0  f7 4a 20 b8 2a cd 70 25  8a c7 2c 97 ad 74 cd c4  |.J .*.p%..,..t..|
000000f0  7e eb 58 34 fe fe cd fd  fa d0 4b 0a bf d7 ed aa  |~.X4......K.....|
00000100  fb f7 6f 3e c1 fd ca 05  48 c6 7a d4 9c b2 62 fa  |..o>....H.z...b.|
00000110  ef ef 34 5a 0f a3 ee 70  d6 0b c4 b7 c9 b4 e7 4f  |..4Z...p.......O|
00000120  06 95 ab ef dc b8 30 4e  45 dd 25 d5 e9 dd 38 48  |......0NE.%...8H|
00000130  e6 a3 11 41 62 2c 54 75  18 b3 42 04 e9 73 c6 c3  |...Ab,Tu..B..s..|
00000140  61 7c 43 bc 47 b2 70 8e  bc c8 64 1a 0f 83 88 f5  |a|C.G.p...d.....|
00000150  21 4e 1b 2d f1 75 e5 6f  85 04 fd 1a 93 41 f9 4a  |!N.-.u.o.....A.J|
00000160  22 5b 97 4c 27 b3 2e 1a  be c7 03 0f e5 3e 6f 91  |"[.L'........>o.|
00000170  e7 eb 3d db 3f 68 8a 4d  b1 b1 39 e9 26 f1 38 88  |..=.?h.M..9.&.8.|
00000180  8a 62 c3 ca b9 89 0a 17  f4 85 0d c2 4f 28 59 dc  |.b..........O(Y.|
00000190  f5 f0 2b ec c2 ea f3 27  62 33 10 1b 63 48 90 22  |..+....'b3..cH."|
000001a0  b9 1c b7 39 e6 07 00 aa  29 dc 85 c3 59 9f cb e3  |...9....)...Y...|
000001b0  57 e1 6b 3c 9a 1d 18 e8  e5 97 02 d0 92 41 00 fe  |W.k<.........A..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 18 a1 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Thanks Again

---

