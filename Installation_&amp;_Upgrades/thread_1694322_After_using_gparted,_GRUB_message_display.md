---
title: "After using gparted, GRUB message display"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by cristian.ene on 2011-02-24
Hmm... i have a problem... after using gparted... to delete my ntfs  part, and increase my linux partition, moving (by copying or deletin)   SWAP and one other partition, used for system... 

i ended up having this message displayed on restart     

                            [PHP]Error: file not foud.
grub rescue>  [/PHP]i will post ASAP a print screen of gparted maybe you can help me in sorting this out
[B]
I would like NOT to reinstall ubuntu, but to find a sollution to this problem :)[/B]

---

### Post by cristian.ene on 2011-02-24
you will find attached the photo

---

### Post by Hippytaff on 2011-02-24
Can you post the results.txt of running this [boot script]("http://sourceforge.net/projects/bootinfoscript/")
 
You are being fropped into a grub cli, so for some reason it looks as though grub can not be found. This script will give detailed info of your setup, so others (more knowedgable than I) can try to resolve the problem with you.

---

### Post by cristian.ene on 2011-02-24
Dear hippytaff, this are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8064.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *          2,046   117,229,567   117,227,522   5 Extended
/dev/sda5               2,048   106,840,063   106,838,016  83 Linux
/dev/sda6         106,842,112   108,840,959     1,998,848  83 Linux
/dev/sda7         108,843,008   117,229,567     8,386,560  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,913,727     3,905,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2209dd2a-d3a4-461b-b0f8-fbb1e991c69b   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7335af5f-9a12-4f2b-bfed-36e732847eb4   ext4                                     
/dev/sda6        09fb1643-f2d5-4c76-84aa-433bbfe66a06   ext4                                     
/dev/sda7        3e0a3a11-6af2-4952-8cfd-bf02f0890189   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2578-A42C                              vfat       Volum nou                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/7335af5f-9a12-4f2b-bfed-36e732847eb4 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/09fb1643-f2d5-4c76-84aa-433bbfe66a06 ext4       (rw,nosuid,nodev,uhelper=udisks)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
# Commented out by Dropbox
# UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=09fb1643-f2d5-4c76-84aa-433bbfe66a06 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a27c18a6-ff6b-4cbf-8c6f-31ebf4c831da none            swap    sw              0       0
UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 / ext4 errors=remount-ro,user_xattr 0 1

============================= sda6/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7335af5f-9a12-4f2b-bfed-36e732847eb4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
set locale_dir=($root)/grub/locale
set lang=ro
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    linux    /vmlinuz-2.6.35-25-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro   quiet splash
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /vmlinuz-2.6.35-25-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    linux    /vmlinuz-2.6.35-24-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    linux    /vmlinuz-2.6.35-22-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=7335af5f-9a12-4f2b-bfed-36e732847eb4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 09fb1643-f2d5-4c76-84aa-433bbfe66a06
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda6: Location of files loaded by Grub: ===================


  54.8GB: grub/core.img
  54.8GB: grub/grub.cfg
  54.8GB: initrd.img-2.6.35-22-generic
  54.8GB: initrd.img-2.6.35-24-generic
  54.9GB: initrd.img-2.6.35-25-generic
  54.8GB: vmlinuz-2.6.35-22-generic
  54.8GB: vmlinuz-2.6.35-24-generic
  54.8GB: vmlinuz-2.6.35-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 3e 00 00 00 00 00  |........>.>.....|
00000020  80 98 3b 00 e0 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 2c a4 78 25 56  6f 6c 75 6d 20 6e 6f 75  |..),.x%Volum nou|
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
00000100  7d 00 66 b8 c0 c5 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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


```

---

### Post by cristian.ene on 2011-02-24
no ideas?

---

### Post by dino99 on 2011-02-24
when resizing partition, the uuid change so grub dont know about it. What you need to do:

- boot on livecd
- run: blkid
take note of the uuid you need to boot on.

- reboot on hdd to get the grub menu (if it is hidden, then hold "shift" key down at end of bios process to unhide the grub menu)

- select (highlight) the boot line, edit it (hit E) and change the uuid by the new one you get with blkid command, then ctrl+x to save and boot

after booted, open a terminal and run:

sudo upgrade-grub

---

### Post by cristian.ene on 2011-02-24
this is the reply i am getting... but this is weird. Do i have to mention that i am new with ubuntu?
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="2209dd2a-d3a4-461b-b0f8-fbb1e991c69b" TYPE="ext3" 
/dev/sda5: UUID="7335af5f-9a12-4f2b-bfed-36e732847eb4" TYPE="ext4" 
/dev/sda6: UUID="09fb1643-f2d5-4c76-84aa-433bbfe66a06" TYPE="ext4" 
/dev/sda7: UUID="3e0a3a11-6af2-4952-8cfd-bf02f0890189" TYPE="swap" 
/dev/sdb1: LABEL="Volum nou" UUID="2578-A42C" TYPE="vfat" 

```now what?

LaterEdit:
When i reboot, without my LIVE usb stick, i keep shhift key pressed but nothing happens
whatever i type, the answer is unknown command.

this is what i see  "grub rescue>"

---

### Post by Hippytaff on 2011-02-24
you have to be quick with the shift key.

---

### Post by cristian.ene on 2011-02-24
> **Hippytaff said:**
> you have to be quick with the shift key.
tell me you're kidding me :)
and this is a joke...


All i get is
 ```
grub loading... 
error: fole not found
grub rescue>
```

**is there another way?**

---

### Post by cristian.ene on 2011-02-24
It simply doesn't work

---

### Post by Hippytaff on 2011-02-24
haha...no...honestly (I know it's annoying) but as soon as the bios finishes what it's doing press shift to get to the grub menu. The thing is...how do you know when the bios has finished what it is doing? you don't...and that's the frustrating part. I'd say just boot and press the shift key a couple of times then hold it down. then the grub menu should appear - I know there should be a better way :-)

---

### Post by cristian.ene on 2011-02-24
> **Hippytaff said:**
> haha...no...honestly (I know it's annoying) but as soon as the bios finishes what it's doing press shift to get to the grub menu. The thing is...how do you know when the bios has finished what it is doing? you don't...and that's the frustrating part. I'd say just boot and press the shift key a couple of times then hold it down. then the grub menu should appear - I know there should be a better way :-)
but it says grub loading... and after that... file nout found
it's blody irritating

---

### Post by cristian.ene on 2011-02-24
> **Hippytaff said:**
> haha...no...honestly (I know it's annoying) but as soon as the bios finishes what it's doing press shift to get to the grub menu. The thing is...how do you know when the bios has finished what it is doing? you don't...and that's the frustrating part. I'd say just boot and press the shift key a couple of times then hold it down. then the grub menu should appear - I know there should be a better way :-)

Well... it's official.... i got it 3 times, with keeping the shift key pressed, it says it's loading but it's not....so? other options?

It's not me giving up,... it's IT not working :)

if you want... i can make a video

---

### Post by cristian.ene on 2011-02-24
hey hippy,....

do you know anything about rescatux?

---

### Post by Hippytaff on 2011-02-24
> **cristian.ene said:**
> hey hippy,....

do you know anything about rescatux?

no...

---

### Post by cristian.ene on 2011-02-25
Anybody else knows a  solution to my problem?

What if i reinstall,... will i loose all my programs, IF... i have 2 partitions, in witch 1 is as far as i remember "boot" and the other one is....home...?

---

### Post by cristian.ene on 2011-02-25
So... i've taken 2 screenshots, one without shift key pressed, one WITH the key pressed

Please advise

---

### Post by Hippytaff on 2011-02-25
If you reinstall you will losse your files unless you have a seperate /home partition.

---

### Post by cristian.ene on 2011-02-25
How do you suggest i repartition,... so i won't have this problem again?

I would like that my programs remain installed, if possible, and of course, a /home partition.

I have a Compaq Mini 700 EI with 60GB hdd, and 1GB ram 

I thought about:
/ 5 gigs?
/boot 200 megs
/swap 2048 megs
/home "rest"

 do you have any options or remarks?

---

### Post by cristian.ene on 2011-02-25
solved by reinstalling

[http://ubuntuforums.org/showthread.php?t=1695226](http://ubuntuforums.org/showthread.php?t=1695226)

---

