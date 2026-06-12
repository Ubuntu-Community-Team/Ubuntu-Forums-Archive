---
title: "Change location of Grub2 Loader"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by weizguy on 2010-01-22
I accidentally installed the Grub2 Loader on my MacOSx HD rather than on the Ubuntu HD.  How do I change the location?

---

### Post by presence1960 on 2010-01-22
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Get me that info & I'll give you the exact commands to run.

---

### Post by weizguy on 2010-01-23
Here is the info you requested:

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader? is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009d5dc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   293,041,664   293,041,602  af HFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x620baced

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   293,044,223   292,837,376   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dcbf0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   601,361,144   601,361,082  83 Linux
/dev/sdc2         601,361,145   625,137,344    23,776,200   5 Extended
/dev/sdc5         601,361,208   625,137,344    23,776,137  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 32.1 GB, 32078036992 bytes
5 heads, 32 sectors/track, 391577 cylinders, total 62652416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3106952

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,064    62,652,415    62,644,352   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ae1623f8-3185-3311-b9bd-d85ef9305e15" LABEL="MacOsX" TYPE="hfsplus" 
/dev/sdb1: UUID="F4CCCF27CCCEE2CA" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdb2: UUID="8674D10B74D0FF3D" TYPE="ntfs" 
/dev/sdc1: UUID="a65e9cb1-7750-46cc-9fd8-842041f8da03" TYPE="ext4" 
/dev/sdc5: UUID="52522ccb-180d-4bd8-978d-40645a641aaa" TYPE="swap" 
/dev/sdd1: LABEL="PATRIOT" UUID="8119-E3E7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/weizguy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=weizguy)
/dev/sdd1 on /media/PATRIOT_ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set a65e9cb1-7750-46cc-9fd8-842041f8da03
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set a65e9cb1-7750-46cc-9fd8-842041f8da03
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set a65e9cb1-7750-46cc-9fd8-842041f8da03
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set a65e9cb1-7750-46cc-9fd8-842041f8da03
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set a65e9cb1-7750-46cc-9fd8-842041f8da03
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod hfsplus
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ebdf17b9734636fb
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid ebdf17b9734636fb uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f4cccf27cccee2ca
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=a65e9cb1-7750-46cc-9fd8-842041f8da03 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=52522ccb-180d-4bd8-978d-40645a641aaa none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 08 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D..T.f1.f...|
00000020  80 7c 04 af 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|..u......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 08 66 51  06 53 30 e4 50 50 b0 2d  |..f.L.fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I believe sda would be my MacOSx drive which I am hoping I will be able to boot once I get this grub loader fixed.  sdb would be my Windows 7 drive and sdc is my Ubuntu drive.  I think sdd is my USB drive that I forgot was plugged in...

---

### Post by presence1960 on 2010-01-23
I would put GRUB on sdc and then make sdc first in hard disk boot order in BIOS, this way when you boot GRUB comes up. Boot with the Live CD, when the menu appears choose "try ubuntu without any changes ". When the desktop loads open a terminal and run ```
sudo mount /dev/sdc1 /mnt
```
This will mount your ubuntu / partition
next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```
This will put GRUB on MBR of sdc. Reboot without the CD & if you haven't done so already go into BIOS & set sdc as first disk to boot in the hard disk boot order. Save changes to CMOS and continue booting. You should be good to go.

Boot into ubuntu and open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```
On the last window use your arrow keys to navigate to sdc and the spacebar to choose sdc. Hit tab to highlight OK and depress enter. This will insure all updates to grub-pc (GRUB2) are placed in the MBR of sdc in the future.

Here is a link to that GRUB2 install from Live CD: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by weizguy on 2010-01-23
It worked :)

thanks, now to get the OSx to load...
[IMG]http://www.weizguy.com/Screenshot.png[/IMG]

---

### Post by presence1960 on 2010-01-23
> **weizguy said:**
> Nevermind, it worked :)

thanks, now to get the OSx to load...
[IMG]http://www.weizguy.com/Screenshot.png[/IMG]

I am not a OSx person. If you need to repair the MBR of sda make sure you go into BIOS and make sda the first disk to boot. just a precaution. I don't know how OSx works but windows writes it bootloader to the first disk to boot, even if windows is on another disk. This may be unneceesary. Refer to someone who really knows OSx for more info.

---

