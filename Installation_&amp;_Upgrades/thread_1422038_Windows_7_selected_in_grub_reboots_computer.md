---
title: "Windows 7 selected in grub reboots computer"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by ryan_cb on 2010-03-04
I recently installed Ubuntu, my first experience with Linux, but when I try to boot a previously installed Windows 7 from grub, it reboots the system back to the grub screen.  I can boot to Ubuntu.  

I've been searching for and working on possible solutions for several days to no avail.  There are some similar posts on various forums but few quite like mine, and solutions I've read haven't solved my problem.  I tried booting to the windows 7 repair disk and selecting the repair start up option, but the message tells me no problems were found.

Any advice would be appreciated.  Thanks in advance.

---

### Post by oldfred on 2010-03-05
Did win7 boot okay before? Did you use the win7 tools to resize the win7 partition and reboot several times to make sure win7 was ok with the new size?

To see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by ryan_cb on 2010-03-05
Yes.  I created the windows partition in windows and I was able to boot into windows several times before I installed ubuntu.  

The code below comes from your procedure.  I really appreciate your help with this.  Some of this stuff is over my head.  Thank you.



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 226062368 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #2 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

Disk /dev/sda: 200.0 GB, 200049647616 bytes
42 heads, 40 sectors/track, 232572 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fb05f41

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             40   216,958,399   216,958,360   7 HPFS/NTFS
/dev/sda2         216,958,560   278,399,519    61,440,960  83 Linux
/dev/sda3         278,399,520   382,527,487   104,127,968   7 HPFS/NTFS
/dev/sda4         382,527,600   390,720,959     8,193,360   5 Extended
/dev/sda5         382,527,640   390,720,959     8,193,320  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x68cb4030

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   586,099,394   586,099,332   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CEF42E3BF42E2665                       ntfs                                     
/dev/sda2        eda84c6a-d5ae-4140-9de8-6f45e534ba07   ext4       Ubuntu                        
/dev/sda3        28B0E19E719841E5                       ntfs       Storage                       
/dev/sda5        a4b2b4b5-1a0b-437e-92de-a180b6c61d3a   swap                                     
/dev/sdb1        01C4DB0F82D7F540                       ntfs       Work                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Work              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set eda84c6a-d5ae-4140-9de8-6f45e534ba07
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set eda84c6a-d5ae-4140-9de8-6f45e534ba07
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=eda84c6a-d5ae-4140-9de8-6f45e534ba07 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set eda84c6a-d5ae-4140-9de8-6f45e534ba07
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=eda84c6a-d5ae-4140-9de8-6f45e534ba07 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set eda84c6a-d5ae-4140-9de8-6f45e534ba07
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=eda84c6a-d5ae-4140-9de8-6f45e534ba07 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set eda84c6a-d5ae-4140-9de8-6f45e534ba07
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=eda84c6a-d5ae-4140-9de8-6f45e534ba07 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cef42e3bf42e2665
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=eda84c6a-d5ae-4140-9de8-6f45e534ba07 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a4b2b4b5-1a0b-437e-92de-a180b6c61d3a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Work ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda2: Location of files loaded by Grub: ===================


 115.7GB: boot/grub/core.img
 115.7GB: boot/grub/grub.cfg
 111.6GB: boot/initrd.img-2.6.31-14-generic
 111.4GB: boot/initrd.img-2.6.31-19-generic
 111.6GB: boot/vmlinuz-2.6.31-14-generic
 112.0GB: boot/vmlinuz-2.6.31-19-generic
 111.4GB: initrd.img
 111.6GB: initrd.img.old
 112.0GB: vmlinuz
 111.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

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
000001b0  00 00 00 00 00 00 00 00  30 40 cb 68 00 00 80 01  |........0@.h....|
000001c0  01 00 07 fe bf 82 3f 00  00 00 84 2a ef 22 00 00  |......?....*."..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf ```

```

---

### Post by oldfred on 2010-03-05
I do not see anything unusual except this:
42 heads, 40 sectors/track

If you look at your second drive:
255 heads, 63 sectors/track

The 255 heads 63 sectors is the most common with modern hard drives. Your windows partition also then starts at sector 40 where most linux and XP start at 63 and Vista & 7 start at 2048.

Is there anything unusual about your drive? It could indicate a bad partition table. But i am not real knowledgeable on partition tables. I would make sure I do have backups. Beyond that I cannot help. Someone else may see more.

---

### Post by ryan_cb on 2010-03-05
I don't know of anything unusual about my hard drive.  I bought the computer someone else so I don't know the history.

Is it possible to boot to windows using a boot disc?  What would happen if I uninstalled grub?  Would it boot directly to windows?

---

### Post by presence1960 on 2010-03-05
> **ryan_cb said:**
> I don't know of anything unusual about my hard drive.  I bought the computer someone else so I don't know the history.

Is it possible to boot to windows using a boot disc?  What would happen if I uninstalled grub?  Would it boot directly to windows?

You can restore the MBR to a windows MBR and if the windows install is functional it will boot to windows. Boot into Ubuntu and in terminal run ```
sudo apt-get install lilo
```Ignore warning. Then in terminal run ```
sudo lilo -M /dev/sda mbr
```You now have a windows MBR. Reboot & if windows is functional it will boot to windows.

---

