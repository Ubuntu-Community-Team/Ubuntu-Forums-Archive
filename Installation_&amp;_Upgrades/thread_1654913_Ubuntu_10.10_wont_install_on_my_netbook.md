---
title: "Ubuntu 10.10 wont install on my netbook"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by mcfritzl on 2010-12-29
I've been trying to install Ubuntu 10.10 netbook remix on my Acer laptop but it hasn't been working. I used a USB stick and did the installation process and I even got to where it said installation complete, but when I restart it it doesn't boot. It just hangs...I've tried to install it about 5 times now and I'm getting really frustrated. Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2010-12-29
Sounds like you've installed okay but are having hardware issues. I wouldn't bother trying to install again and if you do, try 10.04.

When you boot the computer where is it hanging? Do you get to a boot list where you can pick what kernel you are booting? If so, choose the recovery kernel (underneath the first option on the list) and see what it says when it hangs. 

If you get to the screen of recovery options, drop to a root shell and try typing:

```
startx
```That should get you to a desktop and if it doesn't it will give you some indication of why. Have a pen and paper ready when troubleshooting and include whatever details you can in next post, even if the errors make no sense to your good self. ;)

---

### Post by Quackers on 2010-12-29
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mcfritzl on 2010-12-29
@Bucky Ball 
It hangs right after the screen where you'd press F12 to enter the BIOS disappears.

@Quakers
Here's the info I got back:

```
 
=> No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,683,519    15,683,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   0c1baea6-b98a-4e50-a67e-103cb3e34a77   ext4                                     
/dev/mmcblk0p5   231b201c-2dc7-4022-b935-2dbeefaec0e1   swap                                     
/dev/sda1        5d3dfc03-ca31-4d9f-826b-ae6a606d46e7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        059b872f-38a6-4856-b530-a5a146392ab6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12E5-0D2A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/mmcblk0p1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0c1baea6-b98a-4e50-a67e-103cb3e34a77
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0c1baea6-b98a-4e50-a67e-103cb3e34a77 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/mmcblk0p1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0c1baea6-b98a-4e50-a67e-103cb3e34a77
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0c1baea6-b98a-4e50-a67e-103cb3e34a77 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=059b872f-38a6-4856-b530-a5a146392ab6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/core.img
   5.0GB: boot/grub/grub.cfg
   2.8GB: boot/initrd.img-2.6.35-22-generic
   5.0GB: boot/vmlinuz-2.6.35-22-generic
   2.8GB: initrd.img
   5.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3a 00 20 00 4e 00 65 00  74 00 52 00 74 00 52 00  |:. .N.e.t.R.t.R.|
00000010  65 00 74 00 75 00 72 00  6e 00 43 00 68 00 65 00  |e.t.u.r.n.C.h.e.|
00000020  63 00 6b 00 0d 00 0a 00  5b 00 30 00 34 00 2f 00  |c.k.....[.0.4./.|
00000030  31 00 38 00 2f 00 31 00  30 00 2c 00 31 00 30 00  |1.8./.1.0.,.1.0.|
00000040  3a 00 34 00 39 00 3a 00  35 00 32 00 5d 00 20 00  |:.4.9.:.5.2.]. .|
00000050  4d 00 69 00 63 00 72 00  6f 00 73 00 6f 00 66 00  |M.i.c.r.o.s.o.f.|
00000060  74 00 20 00 2e 00 4e 00  45 00 54 00 20 00 46 00  |t. ...N.E.T. .F.|
00000070  72 00 61 00 6d 00 65 00  77 00 6f 00 72 00 6b 00  |r.a.m.e.w.o.r.k.|
00000080  20 00 33 00 2e 00 35 00  4c 00 50 00 20 00 28 00  | .3...5.L.P. .(.|
00000090  78 00 36 00 34 00 29 00  20 00 2d 00 20 00 e5 65  |x.6.4.). .-. ..e|
000000a0  2c 67 9e 8a 3a 00 20 00  52 00 65 00 74 00 75 00  |,g..:. .R.e.t.u.|
000000b0  72 00 6e 00 20 00 74 00  79 00 70 00 65 00 3a 00  |r.n. .t.y.p.e.:.|
000000c0  0d 00 0a 00 5b 00 30 00  34 00 2f 00 31 00 38 00  |....[.0.4./.1.8.|
000000d0  2f 00 31 00 30 00 2c 00  31 00 30 00 3a 00 34 00  |/.1.0.,.1.0.:.4.|
000000e0  39 00 3a 00 35 00 32 00  5d 00 20 00 4d 00 69 00  |9.:.5.2.]. .M.i.|
000000f0  63 00 72 00 6f 00 73 00  6f 00 66 00 74 00 20 00  |c.r.o.s.o.f.t. .|
00000100  2e 00 4e 00 45 00 54 00  20 00 46 00 72 00 61 00  |..N.E.T. .F.r.a.|
00000110  6d 00 65 00 77 00 6f 00  72 00 6b 00 20 00 33 00  |m.e.w.o.r.k. .3.|
00000120  2e 00 35 00 4c 00 50 00  20 00 28 00 78 00 36 00  |..5.L.P. .(.x.6.|
00000130  34 00 29 00 20 00 2d 00  20 00 e5 65 2c 67 9e 8a  |4.). .-. ..e,g..|
00000140  3a 00 20 00 4e 00 65 00  74 00 52 00 74 00 52 00  |:. .N.e.t.R.t.R.|
00000150  65 00 74 00 75 00 72 00  6e 00 43 00 68 00 65 00  |e.t.u.r.n.C.h.e.|
00000160  63 00 6b 00 0d 00 0a 00  5b 00 30 00 34 00 2f 00  |c.k.....[.0.4./.|
00000170  31 00 38 00 2f 00 31 00  30 00 2c 00 31 00 30 00  |1.8./.1.0.,.1.0.|
00000180  3a 00 34 00 39 00 3a 00  35 00 32 00 5d 00 20 00  |:.4.9.:.5.2.]. .|
00000190  4d 00 69 00 63 00 72 00  6f 00 73 00 6f 00 66 00  |M.i.c.r.o.s.o.f.|
000001a0  74 00 20 00 2e 00 4e 00  45 00 54 00 20 00 46 00  |t. ...N.E.T. .F.|
000001b0  72 00 61 00 6d 00 65 00  77 00 6f 00 72 00 00 c8  |r.a.m.e.w.o.r...|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  82 4f ef 00 b6 3b 00 00  00 00 00 00 02 00 00 00  |.O...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 2a 0d e5 12 4e  4f 20 4e 41 4d 45 20 20  |..)*...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 94 77 00 00  66 ba 00 00 00 00 bb 00  |}.f..w..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Hope that helps :s

---

### Post by Bucky Ball on 2010-12-29
For a start you have an extended partition with no partitions in it on sda1. You knew that?

---

### Post by mcfritzl on 2010-12-30
No, I didn't know that...and I honestly am not really sure what that means, I don't know much about computers and related stuff. So what exactly does that mean?

---

### Post by 4md1t on 2010-12-31
[SIZE="5"]hi guys , this is my result , 
can someone tell me what is this  ?  [/SIZE]


[SIZE="6"]result.txt =>  [http://ge.tt/5hbXd17](http://ge.tt/5hbXd17) [/SIZE]

---

### Post by Bucky Ball on 2011-01-01
> **4md1t said:**
> [SIZE=5]hi guys , this is my result , 
can someone tell me what is this  ?  [/SIZE]


[SIZE=6]result.txt =>  [http://ge.tt/5hbXd17](http://ge.tt/5hbXd17) [/SIZE]

If you have a problem you would be MUCH better to post a new thread with a descriptive title and as much info about your problem and machine as you can think of. 

Not a good idea to barge a thread ten posts deep. You're chances of getting much help are not good and not considered good etiquette. ;)

---

### Post by Idefix82 on 2011-01-01
mcfritzl, if I read your output correctly, then for some strange reason the boot loader didn't install itself into the MBR. So the BIOS doesn't know that you have any operating system at all. I don't know how this happened (when you installed, did you choose "manual partitioning"?), but you can install GRUB, the Linux boot loader, manually. To do that, follow [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). You will be installing grub2, so you can skip all those paragraphs that refer to grub legacy.

---

### Post by mcfritzl on 2011-01-01
Okay, I have good news and bad news. Good news is that installing the boot loader to the MBR worked and I now have Ubuntu on my netbook again! Bad news is that my wireless still wont connect...

---

### Post by Idefix82 on 2011-01-01
Excellent, glad to hear that the first hurdle is taken. Please open a new thread for the wireless issue, providing details about your card. You might want to post the output from
```
lshw -C network
```
in the first post of the new thread.

---

### Post by Bucky Ball on 2011-01-01
> **Idefix82 said:**
> Excellent, glad to hear that the first hurdle  is taken. Please open a new thread for the wireless issue, providing  details about your card. You might want to post the output from
```
lshw -C network
```in the first post of the new thread.

+1. Mark thread as solved and start a new one for wireless issue as mentioned. Good luck. Post a link to the new thread here if you like. ;)

---

### Post by mcfritzl on 2011-01-02
Thanks guys!

[http://ubuntuforums.org/showthread.php?p=10306403#post10306403](http://ubuntuforums.org/showthread.php?p=10306403#post10306403)

^That's the link for the new thread I started for my wireless problem.

---

