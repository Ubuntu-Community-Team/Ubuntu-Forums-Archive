---
title: "upgrade to 10.04 and I'm stuck at a grub prompt"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by dgw on 2010-05-01
I upgraded to 10.04. After restarting the computer, it's at the grub prompt. I'm wondering what I need to do, if someone could point me in the right direction that would be keen.

---

### Post by bcbc on 2010-05-01
any more info? Did you install within windows (using wubi)? Anything interesting happen during the upgrade?

Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back as well.

---

### Post by garvinrick4 on 2010-05-01
> **dgw said:**
> I upgraded to 10.04. After restarting the computer, it's at the grub prompt. I'm wondering what I need to do, if someone could point me in the right direction that would be keen.

Put your install CD in and go to just trying Ubuntu and you will be in a Live CD and
be able to repair your install.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub  bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this  by going to a terminal and typing:      Code:
     sudo fdisk -l 
 You will get something like this:


[IMG]http://img517.imageshack.us/img517/713/svr8xil.jpg[/IMG]

From that you need to find the device name of your Ubuntu drive,  something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
     Code:
     sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 
And then, to reinstall the grub:      Code:
     sudo grub-install --root-directory=/media/sda5 /dev/sda 
Push enter and you&#8217;re done! Of course you need to replace  &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.
sda is your hard drive unless you have 2 or more drives that your boot from.

---

### Post by dgw on 2010-05-01
Thanks. Ok, this is going to seem silly, but I can't seem to mount anything but my boot partition. I have full disk encryption. I tried following a tutorial to mount the encrypted filesystem and am getting "Command failed: Can not access device". 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac45278c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        1733    13671315    5  Extended
/dev/sda3            1734       30401   230275710   83  Linux
/dev/sda5              32        1733    13671283+  83  Linux

``````

ubuntu@ubuntu:~$ sudo ./boot_info_script.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda3 for information... 
Searching komputer-root for information... 
Searching komputer-swap for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu
ubuntu@ubuntu:~$ cat RESULTS.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 307997 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

komputer-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

komputer-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac45278c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       498,014       497,952  83 Linux
/dev/sda2             498,015    27,840,644    27,342,630   5 Extended
/dev/sda5             498,078    27,840,644    27,342,567  83 Linux
/dev/sda3          27,840,645   488,392,064   460,551,420  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/devkit-disks-luks-uuid-175bb855-e77a-49f4-9f96-44b8fe2f4807-uid999 YCbjTt-VYkf-yBJW-GrJS-qY9Y-OLGH-5JoOLs LVM2_member                               
/dev/mapper/komputer-root 1d9d2fb1-483c-40ec-8dc2-b80e140a9a3e   ext4                                     
/dev/mapper/komputer-swap 618c8f87-8d7b-499b-a7f7-8caf8f02f97c   swap                                     
/dev/sda1: ambivalent result (probably more filesystems on the device)
/dev/sda5        175bb855-e77a-49f4-9f96-44b8fe2f4807   crypto_LUKS                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
devkit-disks-luks-uuid-175bb855-e77a-49f4-9f96-44b8fe2f4807-uid999

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/mountpoint        ext4       (rw)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
if loadfont /grub/unicode.pf2 ; then
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    linux    /vmlinuz-2.6.32-21-generic root=/dev/mapper/komputer-root ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=/dev/mapper/komputer-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    linux    /vmlinuz-2.6.31-21-generic root=/dev/mapper/komputer-root ro   quiet splash
    initrd    /initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /vmlinuz-2.6.31-21-generic root=/dev/mapper/komputer-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a42c084-0de8-4733-b430-fd71ac07468d
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-21-generic
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: vmlinuz-2.6.31-21-generic
    .0GB: vmlinuz-2.6.32-21-generic

=========================== komputer-root/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/komputer-root /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/mapper/komputer-swap none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  68 2c 3d 6d 75 aa 2b 63  94 6e 24 c5 73 38 4a 33  |h,=mu.+c.n$.s8J3|
00000080  7b 47 13 b9 f3 e3 ce 02  c4 78 e7 ca e4 0e 80 6a  |{G.......x.....j|
00000090  f4 e7 c2 49 60 53 9f ad  b3 ec 29 5b d9 91 28 b5  |...I`S....)[..(.|
000000a0  03 b8 35 43 00 00 00 0a  31 37 35 62 62 38 35 35  |..5C....175bb855|
000000b0  2d 65 37 37 61 2d 34 39  66 34 2d 39 66 39 36 2d  |-e77a-49f4-9f96-|
000000c0  34 34 62 38 66 65 32 66  34 38 30 37 00 00 00 00  |44b8fe2f4807....|
000000d0  00 ac 71 f3 00 03 47 a3  09 d6 90 59 e6 c4 c3 08  |..q...G....Y....|
000000e0  9c 5d 91 ff 00 59 c9 d7  d8 cb fa a4 39 ef ed 01  |.]...Y......9...|
000000f0  a9 61 b4 8e 5e bc 7c fa  00 00 00 08 00 00 0f a0  |.a..^.|.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sda3

00000000  81 0f b4 0d 14 91 5a 6e  09 94 e4 ef d3 0b 51 d3  |......Zn......Q.|
00000010  81 7b 99 9d 46 2a aa 01  c6 49 1d 55 b0 e6 6e ba  |.{..F*...I.U..n.|
00000020  2a 27 89 25 19 11 57 a6  c8 eb ff 63 be 17 f5 f7  |*'.%..W....c....|
00000030  11 bc ff ab ac dc 15 46  13 09 9e ad 24 42 7e 43  |.......F....$B~C|
00000040  28 1a 19 85 79 22 c3 c6  eb 5b 45 ba 4a 4e ce e8  |(...y"...[E.JN..|
00000050  f8 c6 ff 91 0e 8e e7 a6  d6 e6 bf c8 3e 54 ab f2  |............>T..|
00000060  d0 97 f1 db 73 62 21 62  34 0e e9 9e dd e5 ef 88  |....sb!b4.......|
00000070  65 55 13 14 ca 78 fc e3  03 13 21 6f a6 ef 79 37  |eU...x....!o..y7|
00000080  bc bc b3 71 7d e8 d5 30  02 a8 60 2a ec 63 2b 42  |...q}..0..`*.c+B|
00000090  fd ce e3 93 0b 23 bc 0d  89 5c 14 1c 97 7f 27 f5  |.....#...\....'.|
000000a0  f8 58 7e 8c f0 85 16 01  ec 1e e4 89 db 55 a3 e4  |.X~..........U..|
000000b0  62 88 db df b4 d2 bc be  c3 c9 99 81 f6 ee e5 5d  |b..............]|
000000c0  35 e5 53 10 8e 0a 10 05  e7 c6 96 9d 43 cf 7b e0  |5.S.........C.{.|
000000d0  07 24 64 2c b3 94 f5 b5  e6 c6 28 66 d9 fa 9d 11  |.$d,......(f....|
000000e0  c7 20 55 4a c5 b9 40 86  ba 14 de 52 ee 02 6e ba  |. UJ..@....R..n.|
000000f0  89 e4 9d c2 8d 3f b7 de  09 26 42 38 10 94 1e 8e  |.....?...&B8....|
00000100  ed c5 25 7f 1b 07 f8 05  95 07 7c 2a cc 3e 57 df  |..%.......|*.>W.|
00000110  0d 71 11 10 e3 2c 89 cc  b1 22 9d a3 e0 37 a2 0a  |.q...,..."...7..|
00000120  20 df 10 35 9c 6c da 05  ef 12 26 65 d0 76 15 2f  | ..5.l....&e.v./|
00000130  52 3f 1a 32 fe 7b 4d 24  7f 78 98 ab f0 1c df 58  |R?.2.{M$.x.....X|
00000140  bd 71 5b c1 44 b9 24 c5  b3 31 f9 45 7a a5 06 ff  |.q[.D.$..1.Ez...|
00000150  0b 3b 1c 58 5b 65 92 90  b9 92 85 e3 a9 38 de 21  |.;.X[e.......8.!|
00000160  85 a8 2f cc 65 a7 40 8c  b4 40 33 db b6 8e 60 b6  |../.e.@..@3...`.|
00000170  55 b7 9b 94 e7 f8 de 2a  77 f3 9a 05 84 3f 1a 2f  |U......*w....?./|
00000180  69 83 f6 8f 17 ba de 86  c4 e7 bf 4a 79 b2 43 f6  |i..........Jy.C.|
00000190  67 62 2b ba dd 21 50 6c  da e9 90 90 27 17 1b 84  |gb+..!Pl....'...|
000001a0  27 c1 2e 80 80 65 33 e7  6a cb 2e 81 13 2b ca 92  |'....e3.j....+..|
000001b0  05 80 ce f7 08 18 1c b2  54 b5 94 91 45 d3 34 0f  |........T...E.4.|
000001c0  79 8d ca 27 19 6e 9f 23  de 6f 31 f4 54 ce 69 cf  |y..'.n.#.o1.T.i.|
000001d0  68 c3 99 b9 dc 62 72 72  8d e8 ea e1 2f ac 73 90  |h....brr..../.s.|
000001e0  71 39 62 e0 e2 8f 91 ec  40 8c 75 07 bb 80 6e ba  |q9b.....@.u...n.|
000001f0  9b 7d 05 8a 95 06 69 f2  f2 ba 8f eb 5c 61 df 13  |.}....i.....\a..|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```I have Ubuntu installed on a 14 GB part of my hard drive, the rest of the hard drive is a truecrypt volume. I don't have Wubi. The upgrade seemed to go ok until I rebooted at the end.

---

### Post by garvinrick4 on 2010-05-01
I have never worked with encrypted partitions so you are going to need help from someone else or Google it and see if you can get info on mounting your file systems.
Good luck.

---

### Post by dgw on 2010-05-01
I've been googling it, and finding stuff like this: [http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

Different purpose for wanting to mount it, but the instructions for mounting it should work, and they don't. I did back everything up before doing the upgrade, and I guess I'll probably have to do a clean install, but I want to avoid having to do that. :(

---

### Post by bcbc on 2010-05-01
I don't know anything about encrypted drives either - life is complicated enough without encryption :)

But the bootinfoscript did report:
```
/dev/sda1: ambivalent result (probably more filesystems on the device)
```

You could try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

It doesn't sound like it will apply to you, but that's the only thing I can come up with. I'll leave it to others to provide more.

---

### Post by dgw on 2010-05-01
> **bcbc said:**
> I don't know anything about encrypted drives either - life is complicated enough without encryption :)

But the bootinfoscript did report:
```
/dev/sda1: ambivalent result (probably more filesystems on the device)
```You could try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

It doesn't sound like it will apply to you, but that's the only thing I can come up with. I'll leave it to others to provide more.
That isn't it, but I followed the links from that to related bug reports and one of them seems like it might be the reason for my problem: [https://bugs.launchpad.net/ubuntu/+bug/464411](https://bugs.launchpad.net/ubuntu/+bug/464411)

I tried sudo BLKID_DEBUG=0xffff blkid -p /dev/sda1:
```
ubuntu@ubuntu:/mnt$ sudo BLKID_DEBUG=0xffff blkid -p /dev/sda1
libblkid: debug mask set to 0xffff.
reseting blkid_probe
ready for low-probing, offset=0, size=0
--> starting probing loop [idx=-1]
linux_raid_member: call probefunc()
ddf_raid_member: call probefunc()
isw_raid_member: call probefunc()
lsi_mega_raid_member: call probefunc()
via_raid_member: call probefunc()
silicon_medley_raid_member: call probefunc()
nvidia_raid_member: call probefunc()
promise_fasttrack_raid_member: call probefunc()
highpoint_raid_member: call probefunc()
adaptec_raid_member: call probefunc()
jmicron_raid_member: call probefunc()
vfat: magic sboff=0, kboff=0
vfat: call probefunc()
assigning SEC_TYPE
assigning LABEL
assigning UUID
assigning VERSION
assigning TYPE
assigning USAGE
<-- leaving probing loop (type=vfat) [idx=16]
--> starting probing loop [idx=16]
ext4dev: magic sboff=56, kboff=1
ext4dev: call probefunc()
ext4: magic sboff=56, kboff=1
ext4: call probefunc()
ext3: magic sboff=56, kboff=1
ext3: call probefunc()
ext2: magic sboff=56, kboff=1
ext2: call probefunc()
ext2_sb.compat = 00000000:00000002:00000001
assigning UUID
assigning VERSION
assigning TYPE
assigning USAGE
<-- leaving probing loop (type=ext2) [idx=23]
--> starting probing loop [idx=23]
jbd: magic sboff=56, kboff=1
jbd: call probefunc()
ufs: call probefunc()
sysv: call probefunc()
<-- leaving probing loop (failed) [idx=49]
ERROR: ambivalent result detected (2 filesystems)!
/dev/sda1: ambivalent result (probably more filesystems on the device)
```If my disk has an old vfat header from before I reformated, I guess that would be from the Dell Utility partition that I used to have (I wiped the utility and recovery partitions when I reformatted to install the encrypted filesystem a few months ago). People are suggesting in the comments on that bug reports that running "sudo dd bs=512 count=1 if=/dev/zero of=/dev/sda1" will fix the problem. I'm a bit apprehensive, so I guess I'll sleep on it before I do that. Am I wrong about this?

edit: I did "sudo dd bs=512 count=1 if=/dev/zero of=/dev/sda1" and it worked, so now I can access my encrypted filesystem! Yay. I still can't boot though. I reinstalled grub and I'm stuck at a different looking grub prompt...

---

### Post by dgw on 2010-05-01
:) It works! Yay!!!

I looked into why grub still wasn't working and found that I'd reinstalled grub into /boot/boot/grub instead of /boot/grub. Oops. Fixed that, tried again...and it booted. I'm at my desktop, everything seems to be normal. Thanks.

---

### Post by bcbc on 2010-05-01
Awesome - glad you got it sorted out - I was out of ideas!

---

### Post by julester23 on 2010-08-30
I found that I also had to wipe the last 512 bytes of my partition. Wiping the first 512 bytes merely wiped out the actual partition type (xfs) while leaving ddf_raid_member metadata. In the example below, sda4 was the troublesome partition which refused to mount without "-t xfs".

```
#vol_id --probe-all /dev/sda4
ddf_raid_member
xfs
#parted /dev/sda unit b print
Disk /dev/sda: 1000204886015B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start         End             Size           Type     File system  Flags
 1      512B          15001000447B    15000999936B   primary  ext3              
 2      15001000448B  35001000447B    20000000000B   primary  xfs               
 3      35001000448B  37049000447B    2048000000B    primary  linux-swap        
 4      37049000448B  1000204886015B  963155885568B  primary  xfs               

Information: Don't forget to update /etc/fstab, if necessary.
#dd if=/dev/zero of=/dev/sda4 seek=`echo 963155885568-512 | bc` bs=1 count=512
```

That did the trick for me. I reformatted afterwards, so i cannot confirm the data integrity.

NOTE: I found this by stracing vol_id --probe-all to see where it was finding ddf_raid_member.

---

