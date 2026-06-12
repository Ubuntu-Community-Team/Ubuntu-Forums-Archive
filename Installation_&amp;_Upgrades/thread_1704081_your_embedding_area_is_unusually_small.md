---
title: "your embedding area is unusually small"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by razorneck on 2011-03-10
Oi. Some days it just doesn't pay to play with computers.

- Clean install of Windows XP and Ubuntu 10.10 from flashdrive onto two separate physical drives. (250GB and 200GB)
- Wipped all partitions and did full formats to NTFS on both drives from the XP install menu.
- Installed XP first on the 250GB drive, then Ubuntu 10.10 on the 200GB drive.
- At the end of the Ubuntu install... got a whole whack of I/0 errors when it went to restart.
- On restart... the system simply hangs where the GRUB loader should show up.

How odd. I've done this several times before with no problem at all. So I tried to reinstall the GRUB2 from my liveCD.
- followed one of the popular 'reinstalling GRUB2' tuts that google gave me.
- got the following...



```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23557   189215744   83  Linux
/dev/sdb2           23557       24322     6142977    5  Extended
/dev/sdb5           23557       24322     6142976   82  Linux swap / Solaris

Disk /dev/sdc: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         502     4030432    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/# 

```So... this is new and disturbing. My embedding area is unusually small? Crap. How did that happen?

More forum reading later...sudo fdisk -lu gives :

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
135 heads, 14 sectors/track, 258411 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x62dd62dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          14   488394899   244197443    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037f4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   378433535   189215744   83  Linux
/dev/sdb2       378435582   390721535     6142977    5  Extended
/dev/sdb5       378435584   390721535     6142976   82  Linux swap / Solaris

Disk /dev/sdc: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060927 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     8060926     4030432    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)
ubuntu@ubuntu:~$ 
```Since sdb1 starts at 2048, there shouldn't be any problem right?

Wrong?

Carrying on. More forum reading later... here's the results of boot_info_script055.sh :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 59016856 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
135 heads, 14 sectors/track, 258411 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             14   488,394,899   488,394,886   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   378,433,535   378,431,488  83 Linux
/dev/sdb2         378,435,582   390,721,535    12,285,954   5 Extended
/dev/sdb5         378,435,584   390,721,535    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060927 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     8,060,926     8,060,864   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2A1468B014688125                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7096aaa2-1bf7-40c4-9dca-da660ee31e53   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        67004236-30d8-4597-9e45-06de0a3f36cf   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1F04-0B20                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
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
    search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7096aaa2-1bf7-40c4-9dca-da660ee31e53 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7096aaa2-1bf7-40c4-9dca-da660ee31e53 ro single 
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
    search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7096aaa2-1bf7-40c4-9dca-da660ee31e53
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2a1468b014688125
    drivemap -s (hd0) ${root}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=67004236-30d8-4597-9e45-06de0a3f36cf none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
 113.9GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  30.2GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  30.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 ff 7a 00 43 3d 00 00  00 00 00 00 02 00 00 00  |..z.C=..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 20 0b 04 1f 4e  4f 20 4e 41 4d 45 20 20  |..) ...NO NAME  |
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
00000100  7d 00 66 b8 aa 7a 00 00  66 ba 00 00 00 00 bb 00  |}.f..z..f.......|
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



```I'm really starting to hate my life at this point. I've reinstalled this exact configuration several times and never had a problem before. It seems I'm in way over my head now so... HELP!

Could someone throw me a fricking bone here? thanks.

---

### Post by Hedgehog1 on 2011-03-10
I see TWO boot partitions.  sda1 & sd**[COLOR="Red"]c[/COLOR]**1

[COLOR="red"] => Grub 2 is installed in the MBR of /dev/sda and looks at sector 59,016,856 of the same hard drive for core.img, but core.img can not be found at this location.[/COLOR]

sda ends at 488,394,899 and 59,016,856 is 'plop' in the middle of that.

Can you disconnect dev/sdc and try the install again?

***The Hedge***

p.s. Don't hate your life.  Just your hardware.  It is easier that way :)

---

### Post by coffeecat on 2011-03-10
The embedding area is the space between the mbr (the first 512 bytes of the hard drive) and the first sector of the first partition. Grub code is written to the embedding area as well as the mbr and the root Linux partition.

fdisk -lu tells you what you need to know:

> **razorneck said:**
> 
More forum reading later...sudo fdisk -lu gives :

[CODE]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          [COLOR=Red]14[/COLOR]   488394899   244197443    7  HPFS/NTFS

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            [COLOR=Red]2048 [/COLOR]  378433535   189215744   83  Linux

/dev/sdc1   *          [COLOR=Red]63[/COLOR]     8060926     4030432    c  W95 FAT32 (LBA)

A start sector of 63 or 2048 is OK. A start sector of 14 is not. No doubt the installer was trying to write grub code to the embedding are of sda, which would be expected since sda would probably be your first boot drive.

Since you probably have Windows on sda1 (please confirm whether this is so), this is going to be an interesting problem to solve. Windows will not like having the partition moved and cloning tools often want to put back a clone to the same start sector. Setting sdb or sdc as your first boot disc will introduce other complications, so re-installing Windows with a sensible start sector in sda1 would be one option.

---

### Post by razorneck on 2011-03-10
I don't know what to tell ya. Like I said, I installed winXP on my 250GB drive and my Ubuntu on my 200GB drive. I've done this many times before... and it just worked. I used the full auto settings - do I reinstall Ubuntu and choose a different drive / mount point instead? I confess I don't really understand all the options in the advanced settings.

Yes I'm assuming the NTFS fdisk -lu info is windows.

---

### Post by coffeecat on 2011-03-10
> **razorneck said:**
> I don't know what to tell ya. Like I said, I installed winXP on my 250GB drive and my Ubuntu on my 200GB drive. I've done this many times before... and it just worked. I used the full auto settings - do I reinstall Ubuntu and choose a different drive / mount point instead? I confess I don't really understand all the options in the advanced settings.

Yes I'm assuming the NTFS fdisk -lu info is windows.

I've seen the Windows XP installer do some strange things, and I'll add a starting sector of 14 to the list. *Very* strange. 

The only thing I can suggest, if you're willing to re-install Windows XP, is to reformat your 250GB sda hard drive with Gparted before using the Windows installer.  If you use Gparted on the 10.04/Lucid live CD, it will create a first partition with a start sector of 63. If you use the 10.10/Maverick live CD, Gparted will create a first partition with a start sector of 2048.

Boot up from an Ubuntu live CD, open Gparted and use the Device menu to create a new partition table. This will effectively remove everything. Now create one primary NTFS partition in the whole of the space. Now boot up with the XP installer and tell it to install to the single partition on the 250GB drive. You don't have to reformat it. It will be quite happy with the partition created with Gparted - I've done this many times.

Also - before you run the  the XP installer, physically disconnect your sdb and sdc drives. Given half a chance the installer will do really weird things - *really* weird things. (I've said that already, haven't I? :)) If it knows only about the one partition on the one drive so much the better. Less scope for it to do something silly.

---

### Post by razorneck on 2011-03-10
Thanks Coffeecat.

Before I blow it all away AGAIN... would you confirm my settings are correct?

danke

---

### Post by coffeecat on 2011-03-10
That looks good. Doubly good because that looks like the Maverick Gparted. You'll see that it defaults to 1MiB freespace before the partition.

Once you've clicked on the green button and created the partition, and before you close Gparted, go to Partition > Information to check you really do have a start sector of 2048.

Also, once you've installed XP, and are back in the Maverick live desktop again, before you start the installer open Gparted and check the start sector of the XP partition in Partition > Information once more. Just to be sure that the XP installer hasn't done something daft, such as move the partition. :?

Good luck! :)

---

### Post by razorneck on 2011-03-10
Ok here I go!

If I don't make it back... remember I love you all!

CHARGE!

---

### Post by Hedgehog1 on 2011-03-10
> **razorneck said:**
> Ok here I go!

If I don't make it back... remember I love you all!

CHARGE!

That has to be the single most ominous post I have ever read.

I do hope **razorneck** makes it back...

***If not, services will be held next Saturday.***  :KS

---

### Post by Hedgehog1 on 2011-03-10
> **coffeecat said:**
> That looks good. Doubly good because that looks like the Maverick Gparted. You'll see that it defaults to 1MiB freespace before the partition.

coffeecat,

I have wondered why gparted leaves that 1 meg of free space, but never thought to ask.

Your description of what the embedded area is (and does) makes this gparted behavior more logical and clearer to me now.

Thanks!

I keep learning every day on this forum.  It is awesome!

***The Hedge***

:KS

---

### Post by razorneck on 2011-03-10
RETREAT!

It's bad sarg... real bad. Just leave me. Save yourself... SAVE YOURSELF! *cough cough*

Windows XP was extremely UNHAPPY trying to be installed on that volume. It went through, copied it's files, did the reboot thing to begin the installation... and threw an error. Something about being unable to boot the OS or some crap like that.

Sooooo I reinstalled it again, turfing the partition we made and let windows make one and it installed once again just fine.

And now I'm back here taking a look-see at the partition with GParted like you recommended just to see what I could see aaaaand the first sector reported is noooooow... 10.

10!??

Wasn't it 14 last time? IT'S GETTING SMALLER everytime I create a new partition? I don't think I even dare attempting to install 10.10 again. This is madness!

... is it just me or is everyone feeling like the walls are closing in?

---

### Post by coffeecat on 2011-03-10
> **Hedgehog1 said:**
> coffeecat,

I have wondered why gparted leaves that 1 meg of free space, but never thought to ask.

I think the 2048 start sector in newer versions of Gparted at least be something to do with the newer advanced format drives, but I might be wrong.

> **razorneck said:**
> RETREAT!

It's bad sarg... real bad. Just leave me. Save yourself... SAVE YOURSELF! *cough cough*

Windows XP was extremely UNHAPPY trying to be installed on that volume. It went through, copied it's files, did the reboot thing to begin the installation... and threw an error. Something about being unable to boot the OS or some crap like that.

Sooooo I reinstalled it again, turfing the partition we made and let windows make one and it installed once again just fine.

And now I'm back here taking a look-see at the partition with GParted like you recommended just to see what I could see aaaaand the first sector reported is noooooow... 10.

10!??

Wasn't it 14 last time? IT'S GETTING SMALLER everytime I create a new partition? I don't think I even dare attempting to install 10.10 again. This is madness!

... is it just me or is everyone feeling like the walls are closing in?

I'm sorry to hear that. That's very disappointing. I wonder what on Earth the XP installer is up to.

At the moment I don't know what to suggest but I will think about it. A question. Are you using a Microsoft XP install CD or some sort of OEM manufacturer's restore disc? I've never had anything like this happen with a Microsoft disc.

I've been doing some experiments recently with the XP installer on a test machine. I will see if I can reproduce your problem, but not today. It's too late here.

---

### Post by razorneck on 2011-03-10
I'm using a standard Windows XP Home Edition SP 2 CD.

I'm going to try installing a copy of Win7 that I... uh... 'found' and see what sort of first sector that gives me.

---

### Post by coffeecat on 2011-03-10
> **razorneck said:**
> I'm using a standard Windows XP Home Edition SP 2 CD.

That's exactly what I'm using. Weird. Perhaps your disc is scratched/blemished enough for it to do strange things but not enough to prevent it from working at all.

> **razorneck said:**
> I'm going to try installing a copy of Win7

I've installed Windows 7 to a Gparted created partition and it was quite happy with the 2048 start sector.

---

### Post by razorneck on 2011-03-10
I followed the exact same steps as I did with XP and installed Win7. I didn't use Gparted or anything, just did a standard windows install.

And everything is cool. Aha?

Win7 gave me a first sector of (after I figured out I had to manually install Gparted from a fully installed Ubuntu 10.10 installation :p) [COLOR=Red]206848[/COLOR]!

Far cry from the [COLOR=Red]14[/COLOR].. and then [COLOR=Red]10[/COLOR] that XP was giving me!

Anyway - it's a cracked version of 7, so I don't know how long I'll end up using it. May just try to reinstall XP without blowing away the partition(s) (why does 7 make two?) and see if I'm golden.

At least now I know what to look out for in the future :)

cheers!

---

### Post by oldfred on 2011-03-10
Something very strange about sda.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
135 heads, 14 sectors/track, 258411 cylinders, total 488397168 sectors

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors

Flash drives and other non-rotating drives had odd heads & sectors/track. But with LBA which has been the standard for about 10 years it is usually 255/63 like your sdb drive.

Do you have some setting in BIOS making not LBA (some have had issues with auto or IDE)?
I was helping another user that had a similar issue. He had a large drive and could not install Ubuntu after. Once he changed it to 255 heads it worked, but he wanted to test the issue and could not change back. Note sure how he changed it but I think it was a BIOS setting.

---

### Post by coffeecat on 2011-03-11
> **razorneck said:**
> [COLOR=Red]206848[/COLOR]!

A first sector of 206848 would be  about 105MB from the start of the drive, which is as little bigger than a Windows 7 boot partition. Do a fdisk on the drive - It may be that the  W7 installer has set up two partitions: a ~100MB sda1 for the boot files and the rest of the drive for the C: partition, sda2 - this is what the W7 installer defaults to if you don't tell it otherwise. If so, see what the start sector is on sda1. That start sector of 206848 is probably for sda2.

Just for the record, with a sector size of 512 bytes, your embedding area would be about 32 KB with a start sector of 63, and about 1MB with a start sector of 2048. At this time a start sector of 63 is probably the commonest so the grub code would certainly fit into 32KB comfortably. A start sector of 14 represents an embedding area of only about 7 KB which is clearly not enough.

oldfred makes some interesting points. I have a spare 250GB HD, but it's an older PATA one. Whatever, I thought I would format it NTFS with the Maverick Gparted and then install XP to it to see what happens. Whether it works or does something weird like yours, I'll post the results.

---

### Post by coffeecat on 2011-03-11
> **coffeecat said:**
> Whatever, I thought I would format it NTFS with the Maverick Gparted and then install XP to it to see what happens. Whether it works or does something weird like yours, I'll post the results.

@razorneck, I don't get your issue, but I do get something weird.

First, I booted with the Maverick live USB, created a new partition table on the 250GB drive and created one ntfs partition. This, before installing Windows:

```
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   488396799   244197376    7  HPFS/NTFS
```Note the start sector of 2048. Next I installed Windows XP which proceeded OK and booted up OK too. Then I rebooted with the Maverick USB and got this:

```
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
76 heads, 10 sectors/track, 642627 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376    7  HPFS/NTFS
```The start sector is still 2048, but the head, track and cylinder figures have changed. I thought they were fixed parts  of hardware; I'm puzzled. @oldfred, any thoughts? :?

Whatever, I have no idea why the XP partition seems to have a floating start sector on your sda. I have only one other suggestion if you want to go back to XP. Change the boot priority so that the system boots from sdb which has an adequate embedding area. You'd need to install grub to the mbr of sdb if you did that and then run update-grub once you'd reinstalled XP to sda to get a Windows entry on your grub menu. With the old legacy grub you had to do some clever stuff with the Windows stanza in menu.lst when Windows was on any drive other than the first one -  I don't know whether that's still so for grub 2.

---

