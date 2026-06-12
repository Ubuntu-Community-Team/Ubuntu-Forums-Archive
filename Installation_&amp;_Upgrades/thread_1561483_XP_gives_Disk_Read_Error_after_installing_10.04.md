---
title: "XP gives Disk Read Error after installing 10.04"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by Werchie on 2010-08-26
I'm completely new to Linux, and have just installed Lucid Lynx 10.04 Netbook Remix on my EeePC 1000H. From the factory, it has 2 partitions - C: and D: so I moved everything I had on D: to C: and then deleted the D: partition in windows so I had approx 37GB of unallocated space. I then used a USB drive to install Lucid.

Grub was loading fine, and Lucid would open up without a hitch. Then I tried to boot into Windows XP from the Grub menu, and was greeted by Disk Read Error  press Ctrl Alt Delete to reboot.

After much searching online, I tried running sudo update-grub. I then rebooted, but it didn't help, XP still wouldn't load.

After more searching, I decided to try booting with an XP installation cd via an external dvd drive. I got into the Recovery Console, and first of all tried just the fixboot command. I rebooted, and still the same error. I booted from the XP cd once again, then ran fixboot and then fixmbr. after rebooting, it still had no effect. I then booted with the cd once more, and ran chkdisk /R. Once that completed, I rebooted, and still no joy.

So now I have a netbook that won't boot into windows, and also now won't boot into linux due to overwriting the MBR.

I'm uncertain of the best way to restore Grub to working order. And I would really like to try and get Windows XP working again too.

These details are what I managed to generate BEFORE I over-wrote the MBR to try and get windows working again - so I don't know if anything will be different now or not.

Output of Boot Info Script:

```
  
Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of  /dev/sda and looks on the same drive in 
    partition #5 for  /boot/grub.

sda1:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector  info:  No errors found in the Boot Parameter Block.
    Operating System:   Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2:  _________________________________________________________________________

     File system:       
    Boot sector type:  -
    Boot sector info:   
    Mounting failed:
mount: unknown filesystem type ''

sda3:  _________________________________________________________________________

     File system:       Extended Partition
    Boot sector type:  Unknown
     Boot sector info:  

sda5:  _________________________________________________________________________

     File system:       ext4
    Boot sector type:  -
    Boot sector info:   
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:    /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6:  _________________________________________________________________________

     File system:       swap
    Boot sector type:  -
    Boot sector info:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 80.0  GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total  156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size  (logical/physical): 512 bytes / 512 bytes

Partition  Boot          Start           End          Size  Id System

/dev/sda1    *              63    91,195,871    91,195,809   7 HPFS/NTFS
/dev/sda2         156,231,936    156,296,447        64,512  ef EFI (FAT-12/16/32)
/dev/sda3           91,197,438   156,231,679    65,034,242   5 Extended
/dev/sda5           91,197,440   153,460,735    62,263,296  83 Linux
/dev/sda6          153,462,784   156,231,679     2,768,896  82 Linux swap /  Solaris


blkid -c /dev/null:  ____________________________________________________________

Device            UUID                                   TYPE       LABEL                          

/dev/sda1        30001C24001BEF98                        ntfs                                     
/dev/sda3: PTTYPE="dos"  
/dev/sda5        8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76    ext4                                     
/dev/sda6         0c3318db-20f6-4eea-8919-251557def3cd   swap                                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep  ^/dev  output: ===========================

Device            Mount_Point              Type       Options

/dev/sda5         /                        ext4        (rw,errors=remount-ro)


================================  sda1/boot.ini: ================================

[boot loader]  
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS  
[operating systems]  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home  Edition" /noexecute=optin /fastdetect 

===========================  sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT  THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig  using templates
# from /etc/grub.d and settings from  /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s  $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [  ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
   save_env saved_entry
  set prev_saved_entry=
  save_env  prev_saved_entry
  set boot_once=true
fi

function savedefault  {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env  saved_entry
  fi
}

function recordfail {
  set recordfail=1
   if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search  --no-floppy --fs-uuid --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
if loadfont  /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod  gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ;  else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
   fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid  --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
set  locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [  ${recordfail} = 1 ]; then
  set timeout=-1
else
  set  timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN  /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set  menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme  ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux  2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os  {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search  --no-floppy --fs-uuid --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
    linux     /boot/vmlinuz-2.6.32-24-generic root=UUID=8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76  ro   quiet splash
    initrd     /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux  2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu  --class os {
    recordfail
    insmod ext2
    set  root='(hd0,5)'
    search --no-floppy --fs-uuid --set  8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
    echo    'Loading Linux  2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic  root=UUID=8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76 ro single 
    echo     'Loading initial ramdisk ...'
    initrd     /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux  2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os  {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search  --no-floppy --fs-uuid --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
    linux     /boot/vmlinuz-2.6.32-21-generic root=UUID=8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76  ro   quiet splash
    initrd     /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux  2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu  --class os {
    recordfail
    insmod ext2
    set  root='(hd0,5)'
    search --no-floppy --fs-uuid --set  8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
    echo    'Loading Linux  2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76 ro single 
    echo     'Loading initial ramdisk ...'
    initrd     /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux  ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test  (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search  --no-floppy --fs-uuid --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
     linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+,  serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
     search --no-floppy --fs-uuid --set 8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76
     linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END  /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober  ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
     insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set  30001c24001bef98
    drivemap -s (hd0) ${root}
    chainloader  +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN  /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu  entries.  Simply type the
# menu entries you want to add after this comment.   Be careful not to change
# the 'exec tail' line above.
### END  /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab:  ===============================

# /etc/fstab: static file system  information.
#
# Use 'blkid -o value -s UUID' to print the universally  unique identifier
# for a device; this may be used with UUID= as a more  robust way to name
# devices that works even if disks are added and removed.  See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc             /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5  during installation
UUID=8c49a6a6-1c2a-430f-b3fc-fdf4e6021a76 /                ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during  installation
UUID=0c3318db-20f6-4eea-8919-251557def3cd none             swap    sw              0       0

=================== sda5: Location of  files loaded by Grub: ===================


  74.7GB:  boot/grub/core.img
  75.0GB: boot/grub/grub.cfg
  74.7GB:  boot/initrd.img-2.6.32-21-generic
  74.9GB:  boot/initrd.img-2.6.32-24-generic
  74.7GB:  boot/vmlinuz-2.6.32-21-generic
  74.7GB: boot/vmlinuz-2.6.32-24-generic
   74.9GB: initrd.img
  74.7GB: initrd.img.old
  74.7GB: vmlinuz
  74.7GB:  vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown BootLoader  on sda3

00000000  bd  5e ed da 6d d3 f0 7a  d5 3c 93 e9 69 54 64 cd   |.^..m..z.<..iTd.|
00000010  9a d9 53 28 00 09 77 e0  40 05 80 9c f3 e8 43  d3  |..S(..w.@.....C.|
00000020  01 0d 53 81 92 53 3e cb  93 45 07 93 3b c6  83 1d  |..S..S>..E..;...|
00000030  a4 43 39 d3 72 86 38 ca  82 d4 c2 04  7c c6 81 ff  |.C9.r.8.....|...|
00000040  fb e2 04 81 0c c6 b8 50  4b 1b bb  4b 72 d7 4a a9  |.......PK..Kr.J.|
00000050  73 77 49 7e 1b 85 53 2c  6f 6d  8d 4b 66 aa a5 4d  |swI~..S,om.Kf..M|
00000060  dc b2 68 14 c3 e2 80 c7  30  80 02 0e 98 6c 48 1e  |..h.....0....lH.|
00000070  41 c7 e1 99 85 5e 6e 1e   9d c4 46 d4 99 90 ac 60  |A....^n...F....`|
00000080  31 9c 11 80 81 66 49  21  98 20 60 4e 9a 42 88 4f  |1....fI!. `N.B.O|
00000090  40 31 80 0a 90 a8  ce bf  82 c2 92 bd 1b 14 05 72  |@1.............r|
000000a0  28 6b 56 5d ec  9a 5e d4  95 85 d3 70 23 2d 85 c3  |(kV]..^....p#-..|
000000b0  f6 93 22 93  4d d5 98 af  76 d4 66 d3 c7 17 88 da  |..".M...v.f.....|
000000c0  7e fa cf  23 71 0a 18 b5  a7 06 98 3a 28 1e 6d 08  |~..#q......:(.m.|
000000d0  8d e0  29 f4 42 45 93 c1  4a 04 c9 80 e1 49 18 a1  |..).BE..J....I..|
000000e0  a1  78 2c 18 d8 a3 53 ae  48 85 23 66 09 8c 88 ce  |.x,...S.H.#f....|
000000f0   51 d2 13 cd b6 a4 52 8e  e3 0a b4 c4 a0 e9 a8 94   |Q.....R.........|
00000100  75 59 30 dc 53 a7 a4 bb  79 9e 49 2b 6c 57 b5  80  |uY0.S...y.I+lW..|
00000110  00 cd f0 04 00 19 88 80  58 18 27 27 11 81  28 f2  |........X.''..(.|
00000120  99 e2 88 d9 80 29 53 98  72 83 a1 8c c8  bc 98 5b  |.....)S.r......[|
00000130  07 a9 83 68 e5 19 48 90  39 87 30 56  98 2f 08 99  |...h..H.9.0V./..|
00000140  82 78 29 98 31 06 61 b3  26 1c 21  11 e4 2a 9d 88  |.x).1.a.&.!..*..|
00000150  f9 c2 09 1b bb 61 9b 04  85  10 88 b4 8c 6c 44 0c  |.....a.......lD.|
00000160  0a 65 e3 e6 70 1e 63 c2   60 d3 e3 16 17 07 06 18  |.e..p.c.`.......|
00000170  50 c1 91 04 83 81 0c  44  00 2a 00 95 01 80 25 ee  |P......D.*....%.|
00000180  50 d0 50 ab 10 92  32 90  6b 58 81 8e 00 d2 28 32  |P.P...2.kX....(2|
00000190  33 4c 36 5d 21  01 60 e1  13 76 8d 17 9c b9 fc 20  |3L6]!.`..v..... |
000001a0  d3 de 22 b1  6e 8e a7 ce  57 cb c7 47 47 8a 78 fd  |..".n...W..GG.x.|
000001b0  0e c8 f0  be ad 51 fa 85  07 a7 61 f9 d2 42 00 fe  |.....Q....a..B..|
000001c0  ff ff  83 fe ff ff 02 00  00 00 00 10 b6 03 00 fe  |................|
000001d0  ff  ff 05 fe ff ff 02 10  b6 03 00 48 2a 00 00 00  |...........H*...|
000001e0   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55  aa  |..............U.|
00000200


```

Output of sudo fdisk -l
```
alex@LucEee:~/Downloads$ sudo fdisk -l

Disk /dev/sda: 80.0 GB,  80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units =  cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512  bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk  identifier: 0x13662e6d

   Device Boot      Start         End       Blocks   Id  System
/dev/sda1   *           1        5677    45597904+   7   HPFS/NTFS
/dev/sda2            9725        9730       32256   ef  EFI  (FAT-12/16/32)
Partition 2 does not end on cylinder  boundary.
/dev/sda3            5677        9725    32517121    5   Extended
/dev/sda5            5677        9553    31131648   83   Linux
/dev/sda6            9553        9725     1384448   82  Linux swap /  Solaris

Partition table entries are not in disk order

```


Any and all information, suggestions and assistance greatly appreciated.

Please help me to get Linux back up and running, and then hopefully Windows XP too.

Thanks in advance

---

### Post by viralmeme on 2010-08-26
> **Werchie said:**
> I'm completely new to Linux, and have just installed Lucid Lynx 10.04 Netbook Remix on my EeePC 1000H ..  and Lucid would open up without a hitch. Then I tried to boot into Windows XP from the Grub menu ..

Boot from the XP recovery CD and fireup the recovery console, enter your password and type `fixboot' followed by `fixmbr' ..

---

### Post by Werchie on 2010-08-28
*** Update ***

Okay, so I have managed to get things working as they should, HOWEVER fixboot and fixmbr didn't help.

In case anyone else comes across a similar situation, this is the process I followed to get things working:

I used an external dvd drive to boot via the XP cd, launching the Recovery Console, first of all trying the fixboot command by itself, rebooted - did not help. Then booted from the XP cd again, tried fixboot and then fixmbr, rebooted, still no good. Then booted off the cd a third time, then tried fixboot, fixmbr and then chkdsk /F (or it may have been chkdsk /R - I can't remember, but when I entered chkdsk /? there were two options, and I chose the one other than /P)- rebooted, but still same error message.

By now, the fixmbr command had overwritten Grub so I then had to go about repairing Grub itself. I still had the Live USB of Lucid that I had used to install in the first place, so used that to boot into a Live environment. I then mounted my Linux partition according to the instructions here (method 2 instructions):

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

After rebooting, I was greeted by Grub once more, and booting into Lucid worked as it should. However, I found that Windows still would not boot, giving the same error message as it did originally. 

I then followed the instructions here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

which had me download and install testdisk - after running through the steps listed on the website I rebooted, and lo and behold, Windows XP worked again. Lucid is still working fine too. So I finally have a happy dual-boot setup.

I hope that others who find themselves in a similar situation may find this information helpful.

---

