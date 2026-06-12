---
title: "How to fix overlapping partitions"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by CVGH on 2011-03-30
I've had a dual boot PC at work for some time. It was built and set-up by a local vendor. Runs XP and Ubuntu 9.04.
CD drive is dying and 9.04 never could figure out the combo NIC/Sound card, so I used XP 100%.
I have 10.10 installed on a USB here at home and so far it is working well so thought I'd try to get it installed at work from the CD.
I thought it would just install into the 9.04 partition, but it didn't[I think]. Grub pops up selections for 10.01,XP and 9.04.
Gparted shows sda as unallocated. However, the thing boots 10.10 and XP fine! 
I can try to get some more info from the command line if you let me know what you'd like to see....

I'm thinking about using Easeus partition manager in XP to delete all but the NTFS partition, 
resize that partition to take the whole HD [does that wipe GRUB out so it will boot ok?]. 
Reboot and defrag then reboot into the liveCD and reinstall. 
This way I have a clean HDD and I can hopefully make a separate partition for Ubuntu. Would this work?

Thanks!!

---

### Post by Hedgehog1 on 2011-03-30
You can recover from this.

If you opt to remove the Ubuntu partitions - GRUB will stop working.

So first do a FIXMBR for the XP using the install CD and selecting the repair option.  You will type FIXMBR at the Command line once you finally get there.

You can also boot into the new Ubuntu 10.10, load gparted, and remove the 9.04 partitions and run
```
sudo update-grub
```

And you will have just XP and 10.10.  You can then resize either XP or Ubuntu to use the empty space.

***The Hedge***

:KS

---

### Post by CVGH on 2011-03-31
Hi Hedge!

Is FIXMBR on the Ubuntu CD? Don't have a XP disc.
What concerns me is that Gparted shows the whole HDD as unallocated, does not see any partitions.....

Here is some more info:

bootinfo script output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       67878712 sectors, but according to the info from 
                       fdisk, it has 67890626 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 102397952.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    67,890,689    67,890,627   7 HPFS/NTFS
/dev/sda2         102,397,952   156,301,311    53,903,360   b W95 FAT32
/dev/sda4          67,878,910   102,397,951    34,519,042   5 Extended
/dev/sda5          67,878,912   100,861,951    32,983,040  83 Linux
/dev/sda6         100,864,000   102,397,951     1,533,952  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda4
/dev/sda1 overlaps with /dev/sda5

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8220AF9820AF91A9                       ntfs                                     
/dev/sda2        CF49-0F11                              vfat       share                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b72eec44-de3c-4ccb-885d-0a5c799f4773   ext4                                     
/dev/sda6        764d6ad3-868d-4df0-ad83-933a901dee9b   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=b72eec44-de3c-4ccb-885d-0a5c799f4773 ro  vga=789  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=b72eec44-de3c-4ccb-885d-0a5c799f4773 ro single  vga=789
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b72eec44-de3c-4ccb-885d-0a5c799f4773
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8220af9820af91a9
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b72eec44-de3c-4ccb-885d-0a5c799f4773 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=764d6ad3-868d-4df0-ad83-933a901dee9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  45.8GB: boot/grub/core.img
  47.9GB: boot/grub/grub.cfg
  36.2GB: boot/initrd.img-2.6.35-28-generic-pae
  45.7GB: boot/vmlinuz-2.6.35-28-generic-pae
  36.2GB: initrd.img
  45.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  5c 98 9d d1 d1 47 66 78  3f 8e 7f e0 9f 9f 06 7c  |\....Gfx?......||
00000010  41 aa 5c eb 5a 52 6b 9a  31 b8 73 2b 5a e9 97 71  |A.\.ZRk.1.s+Z..q|
00000020  2c 01 8f 27 62 4b 14 85  06 7b 02 00 ce 00 03 02  |,..'bK...{......|
00000030  b9 8d 8f 06 f1 a7 ec 71  e1 5f 06 78 8e 18 ae 2e  |.......q._.x....|
00000040  3c 51 71 a2 dc e1 04 89  35 b8 9a 07 c7 3b d8 c1  |<Qq.....5....;..|
00000050  b5 94 e0 90 d8 1d 70 79  00 bf c6 71 3e 61 c4 39  |......py...q>a.9|
00000060  6b 8d 4c ae 95 3a 90 7f  cd 19 b7 17 d7 9b 96 6b  |k.L..:.........k|
00000070  4e bc c9 69 b3 5b 37 f4  99 2e 0b 29 c7 41 c7 17  |N..i.[7....).A..|
00000080  52 50 a8 bc e2 94 97 95  e3 bf 95 f5 dd 75 b7 a8  |RP...........u..|
00000090  7c 21 fd 8c 7f 67 cb ed  4e df 50 d4 6e f5 dd 65  ||!...g..N.P.n..e|
000000a0  d7 12 25 8d fd ec 4b 11  91 09 2f 1c 89 14 48 cd  |..%...K.../...H.|
000000b0  c6 0e 37 60 80 d9 18 07  3d bc 3b 9d d6 cd 21 cb  |..7`....=.;...!.|
000000c0  8b 51 55 12 4d f2 de d7  ea b5 6d e8 f6 f2 39 73  |.QU.M.....m...9s|
000000d0  6c b2 18 17 7a 4d b8 de  da da fe 4f 43 e9 ed 72  |l...zM.....OC..r|
000000e0  ce 1b 3f 15 f8 72 de da  14 8a 28 ec 2f d1 11 14  |..?..r....(./...|
000000f0  2a aa 86 b5 00 00 38 00  0e d5 f5 d8 7d d9 f3 f5  |*.....8.....}...|
00000100  b6 46 a6 0d 76 1c e1 83  40 1f 37 7e d9 ff 00 07  |.F..v...@.7~....|
00000110  be 21 fc 5a ff 00 85 4b  ff 00 08 06 80 35 4f f8  |.!.Z...K.....5O.|
00000120  46 7e 20 69 da d6 ab 9b  b8 2d fe cf 65 1e ef 32  |F~ i.....-..e..2|
00000130  5f de ba ef db 91 f2 a6  e6 39 e1 4d 65 56 2e 56  |_........9.MeV.V|
00000140  b7 72 e9 b5 1b dc d6 fd  af 3c 23 f1 af e2 7f 83  |.r.......<#.....|
00000150  74 bf 83 ff 00 09 74 f6  b5 d3 fc 63 7a 2c fc 57  |t.....t....cz,.W|
00000160  e2 2f b6 41 08 d2 74 80  57 cf 55 8d a4 12 ca f3  |./.A..t.W.U.....|
00000170  02 50 08 d1 86 d5 75 6d  bb c1 a7 51 39 2b 2e a1  |.P....um...Q9+..|
00000180  0b 27 76 79 be b1 fb 2e  78 bf f6 7c f8 d9 e0 4f  |.'vy....x..|...O|
00000190  8b 1f b2 af 84 85 f6 88  d6 50 78 63 c6 be 1c 17  |.........Pxc....|
000001a0  f0 59 fd ae c2 34 54 8e  f8 34 ce 89 24 e8 14 31  |.Y...4T..4..$..1|
000001b0  c6 19 9e 35 38 22 49 2a  39 1c 24 a5 0f 99 00 fe  |...58"I*9.$.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 f7 01 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  f7 01 00 70 17 00 00 00  |.......H...p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```fdisk:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a5f9a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4226    33945313+   7  HPFS/NTFS
/dev/sda2            6374        9730    26951680    b  W95 FAT32
/dev/sda4            4226        6374    17259521    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            4226        6279    16491520   83  Linux
/dev/sda6            6279        6374      766976   82  Linux swap / Solaris

Partition table entries are not in disk order
```fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b72eec44-de3c-4ccb-885d-0a5c799f4773 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=764d6ad3-868d-4df0-ad83-933a901dee9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Hakunka-Matata on 2011-03-31
I think FIXMBR is not available on the Ubuntu LiveCD, but it is available on several other Linux downloads.  I don't use it much and I have an XP disk so I cannot tell you immediately where to get, but give us a few minutes and can do.  However, you may not need it.  Read on please.

> fdisk:
     

     Disk /dev/sda: 80.0 GB, 80026361856 bytes 255 heads, 63 sectors/track, 9729 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9a5f9a5f     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1        4226    33945313+   7  HPFS/NTFS /dev/sda2            6374        9730    26951680    b  W95 FAT32 /dev/sda4            4226        6374    17259521    5  Extended Partition 4 does not end on cylinder boundary. /dev/sda5            4226        6279    16491520   83  Linux /dev/sda6            6279        6374      766976   82  Linux swap / Solaris  Partition table entries are not in disk order dev/sda2 is an error, it overlaps everything that follows.  Gparted refuses to listen to liars so it doesn't know what to report.  Do you know what was, or is in sda2.  Otherwise, it appears you have a workable installation.  [COLOR=Red]Grub 2 is installed to the MBR[/COLOR] and that is where it is suppose to be. One thing you can try is to attempt to do a check on every partition you can using GParted while running from a LiveCd.


There are other ways to execute the FIXMBR command, but don't do it yet.

---

### Post by Hakunka-Matata on 2011-03-31
Are you working from a  Ubuntu LiveCD now?

---

### Post by Hakunka-Matata on 2011-03-31
[B][COLOR=red]\
[/COLOR][/B]

---

### Post by Dutch70 on 2011-03-31
This is from his boot info script and I believe it is correct, but the OP's hdd is out of whack, for lack of a better word. 
There is no sda3, which should have came before sda4, for starters.

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for (,msdos5)/boot/grub.

Running "sudo update-grub" without the quotes will get 9.04 out of the Grub menu.

---

### Post by Hakunka-Matata on 2011-03-31
> **Dutch70 said:**
> This is from his boot info script and I believe it is correct, but the OP's hdd is out of whack, for lack of a better word. 
[COLOR=Red]There is no sda3[/COLOR], which should have came before sda4, for starters.



Running "sudo update-grub" without the quotes will get 9.04 out of the Grub menu.

There probably was a partition 3 at the time the last primary #4, was created.

---

### Post by Dutch70 on 2011-03-31
CVGH,
 I'm not sure if you noticed it, but as I said earlier, running...
```
sudo update-grub
```
will get 9.04 out of your grub menu. 

Just a thought here, but you could try going to synaptic package manager and click "edit" & select "fix broken packages". 
It can't hurt anything & should resolve any dependency problems you have and maybe it will make Gparted to start seeing your partitions again.

 If it doesn't work then please run the following commands separately & post the output so Hedge or other more knowledgeable people than myself can have a look.
```
sudo parted /dev/sda print
sudo fdisk -lu /dev/sda
sudo sfdisk -d /dev/sda
```

Do your partitions show up when running from the live cd/usb?

Best regards

---

### Post by CVGH on 2011-03-31
Hi guys,

I have no problem booting in to XP or 10.10. Both appear to work just fine.
I am finally using Linux at work \\:D/

I used startup-manager to fix Grub, no more 9.04.......

Synaptic: did the "fix broken ..." , but no change.

Everything seems fine, just seems like the HDD is a mess and am wasting space.


```
brian@briansUbuntu:~$ sudo parted /dev/sda print
[sudo] password for brian: 
Error: Can't have overlapping partitions.                                 
brian@briansUbuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a5f9a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    67890689    33945313+   7  HPFS/NTFS
/dev/sda2       102397952   156301311    26951680    b  W95 FAT32
/dev/sda4        67878910   102397951    17259521    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5        67878912   100861951    16491520   83  Linux
/dev/sda6       100864000   102397951      766976   82  Linux swap / Solaris

Partition table entries are not in disk order
brian@briansUbuntu:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 67890627, Id= 7, bootable
/dev/sda2 : start=102397952, size= 53903360, Id= b
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start= 67878910, size= 34519042, Id= 5
/dev/sda5 : start= 67878912, size= 32983040, Id=83
/dev/sda6 : start=100864000, size=  1533952, Id=82
brian@briansUbuntu:~$ 
```

---

### Post by Hakunka-Matata on 2011-03-31
> **CVGH said:**
> Hi guys,

I have no problem booting in to XP or 10.10. Both appear to work just fine.
I am finally using Linux at work \\:D/

I used startup-manager to fix Grub, no more 9.04.......

Synaptic: did the "fix broken ..." , but no change.

Everything seems fine, just seems like the HDD is a mess and am wasting space.


```
brian@briansUbuntu:~$ sudo parted /dev/sda print
[sudo] password for brian: 
Error: Can't have overlapping partitions.                                 
brian@briansUbuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a5f9a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    67890689    33945313+   7  HPFS/NTFS
/dev/sda2       [COLOR=Magenta]102397952   156301311    26951680[/COLOR]    b  W95 FAT32
/dev/sda4        67878910   102397951    17259521    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5        67878912   100861951    16491520   83  Linux
/dev/sda6       100864000   102397951      766976   82  Linux swap / Solaris

Partition table entries are not in disk order
brian@briansUbuntu:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 67890627, Id= 7, bootable
/dev/sda2 : start=102397952, size= 53903360, Id= b
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start= 67878910, size= 34519042, Id= 5
/dev/sda5 : start= 67878912, size= 32983040, Id=83
/dev/sda6 : start=100864000, size=  1533952, Id=82
brian@briansUbuntu:~$ 
```


[LIST]
[*]So Brian, Boot to LiveCD (you can't fix partitions that are mounted and in use, so you have to boot to a CD) thereby leaving the HardDrive free to be operated on.
[*]then using GParted, highlight each partition in order, right click and choose Check, that is sorta the same as doing a chkdsk /f in windows
[*]see if that doesn't fix the partition table.
[/LIST]
Another way of doing it would be to boot into XP, then under disk management, choose to check the disk, you'll have to reboot at which timr Windows will run a Chkdsk /f before it starts the OS.

Please let us know how that works.

---

### Post by CVGH on 2011-03-31
I'm home now, but tomorrow will boot the Gparted Live CD and let you know what happens!

Thanks for all the help!

Brian

---

### Post by Hakunka-Matata on 2011-03-31
My aim (other than being faulty) is to educate (pass along what I've learned from others) thereby contributing to the exponential increase of qualified, bona-fide, sincere Linux savvy nice people.  Unless of course you're an alien, they count two [sic].

So do what people suggest (command lines, etc.) and see what works, then pass it on.

---

### Post by CVGH on 2011-04-01
Had a very busy day at work, so not much time to experiment....
Got a iso of gparted rather than boot from a Ubuntu iso because the CD drive is dying and I get lots of sr0 errors.
Gparted ran fine but was unable do anything with the HDD.
Message was that there are overlapping partitions and the HDD was "unallocated".
 I do remember that after I installed 10.10 and then rebooted into windows, chkdsk ran on it's own.
I have Easus windows partition manager and it doesn't know what do do either. 
Partition magic 8 won't even start.

So I am at a loss as what to try next......

---

### Post by Dutch70 on 2011-04-02
Well, since you have discovered that your problem is overlapping partitions. I would create another thread and give it an informative thread title, 
like ..."xp overlapping my Ubuntu partition" or "how do I fix overlapping partitions". 

It would be a good idea to read this, before creating another thread.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by Hakunka-Matata on 2011-04-02
CVGH:  Worry NOT.  You're in GNU/Linux land now, and there is always a next thing to try.  Just hang in there, the bigger guns haven't even chipped in here yet, if it doesn't get fixed real soon, we'll put out a call for the next level of troubleshooters.

If you are booted from the same HDD you want to repair, it will not work.  You MAY NOT mess with partitions on the Physical drive you're using to run the machine.  That's why you see the ubiquitous reference to Boot from Live CD.  When you do that, the HDD is available to get a massage.  You may have to unmount a partition, but the HDD is not being used to run the program that you want to destroy it with.  Most HDDs are averse to Suicide.

If the CD Player gives errors, can you boot to a USB Stick, they're better in a couple of ways, they are faster, reusable, and more.  If you can boot to a Live CD, then do it.  Then use GParted and try to "FIX partition 2.  Check all the partitions with the Check function of GParted.  It goes very quickly.  

If you do not have Data in the Windows partitions that is important, then try deleting the partition, and recreating a partition to replace it.  Format to NTFS instead of W95 or FAT32.

You'll get it and then it will be over, then you'll forget it ever happened????

Let us know and Good Luck:

[LIST]
[*]Information we need:  Is your Windows installation backed up in case something goes terribly wrong?
[*]While running Ubuntu, can you see your Windows Partition in the file manager, if you can you can copy Data off that partition to back up.
[/LIST]

---

### Post by CVGH on 2011-04-02
Hi H-M,

I knew I couldn't mess with a mounted partition, so that is why I tried it from a Gparted iso. Checked the BIOS, and that PC does not allow boot from USB. I'm using 10.10 on my home laptop from a USB and it works great.

As I can boot into XP just fine, all I would need is to back up is my documents and AutoCad files. But I do not have a CD to reinstall windows. I think it would be easier to wipe the Ubuntu partition(s) in XP and resize the NTFS partition to use the whole HDD. The question I have with that is will that get rid of GRUB and re enable the NT bootloader?

If that is true, I would then use the Gparted iso to shrink the NTFS partition and then use what's left to install 10.10.

Thanks,

Brian

---

### Post by CVGH on 2011-04-02
> **Dutch70 said:**
> Well, since you have discovered that your problem is overlapping partitions. I would create another thread and give it an informative thread title, 
like ..."xp overlapping my Ubuntu partition" or "how do I fix overlapping partitions". 


I will give that a try!

Thanks.

Brian

---

### Post by CVGH on 2011-04-02
I tried a 10.10 dual boot install and seem to have wound up with overlapping partitions. The original post is:

[http://ubuntuforums.org/showthread.php?t=1718074](http://ubuntuforums.org/showthread.php?t=1718074)

Both XP and 10.10 boot and run just fine, but seems like I could clean it up and get some space back.

Anyone run into this before?

Thanks,

Brian

---

### Post by Quackers on 2011-04-02
As I see it, the problem is not with sda2, but with sda1 and sda4/5.
sda1 ends at block 67890689
sda4 (your extended partition) starts at block 67878910 (in other words before sda1 ends!)
sda5, which is the logical partition within sda4 starts at block 67878912 (before sda1's end block)
It may be worth looking at this page, which refers to a new program created by forum user srs5694 (who knows his onions :-) )

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Quackers on 2011-04-02
Sorry - copied from other thread

As I see it, the problem is not with sda2, but with sda1 and sda4/5.
sda1 ends at block 67890689
sda4 (your extended partition) starts at block 67878910 (in other words before sda1 ends!)
sda5, which is the logical partition within sda4 starts at block 67878912 (before sda1's end block)
It may be worth looking at this page, which refers to a new program created by forum user srs5694 (who knows his onions :-) )

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Hakunka-Matata on 2011-04-02
@Quackers, you know your zwiebel too.  Thanks for that finer grained examination of the start/end blocks.  Will I ever learn?  haha

---

### Post by Quackers on 2011-04-02
zwiebel? I don't! :-)
It's difficult to decipher problems sometimes - there's a lot to look at.
Shouldn't you be watching the cricket?  :-)

---

### Post by srs5694 on 2011-04-02
FixParts can help, but only by deleting either /dev/sda1 or /dev/sda5 and rebuilding /dev/sda4 to match. In the end, that's what I recommend doing, actually; although it's theoretically possible to resize your partitions into a valid configuration, doing so is very risky, since you really don't know whether it's /dev/sda1's or /dev/sda5's data in the overlapping area. Worse, an inopportune change to /dev/sda1 could render both /dev/sda5 and /dev/sda6 inaccessible, so you do *not* want to start making changes to /dev/sda1! My recommendation is:


[list=1]
[*]Back up *everything* on /dev/sda1 and /dev/sda5.
[*]Use Linux's fdisk utility to delete /dev/sda1 or FixParts to delete /dev/sda5 (whichever you think will be easier to rebuild).
[*]Run a disk check (CHKDSK from Windows for /dev/sda1, fsck from Linux on /dev/sda5) on the partition you've left in place.
[*]Create a new /dev/sda1 or /dev/sda5 (whichever you deleted). Note that the number may change, particularly if you create a replacement for /dev/sda5.
[*]Restore the data you backed up.
[*]If you know what disk partitioning utility created this mess, throw it away and tell us what it was so we can all avoid it.
[/list]


You may also need to deal with boot loader issues once you've done all that.

---

### Post by Hakunka-Matata on 2011-04-02
> **CVGH said:**
> Hi H-M,

I knew I couldn't mess with a mounted partition, so that is why I tried it from a Gparted iso. Checked the BIOS, and that PC does not allow boot from USB. I'm using 10.10 on my home laptop from a USB and it works great.

As I can boot into XP just fine, all I would need is to back up is my documents and AutoCad files. But I do not have a CD to reinstall windows. I think it would be easier to wipe the Ubuntu partition(s) in XP and resize the NTFS partition to use the whole HDD. The question I have with that is will that get rid of GRUB and re enable the NT bootloader?

If that is true, I would then use the Gparted iso to shrink the NTFS partition and then use what's left to install 10.10.

Thanks,

Brian

Brian, great to know you know you cannot mess with a mounted partition.  And do you know you cannot mess with an unmounted partition on an active drive?  This is something that is lacking the overall design of this and other forums.  I never know how much the OP knows, well maybe sometimes it's evident, but that leaves a responder in the position of guessing what level of help is appropriate.  I don't want to assume the OP is totally ignorant, they wouldn't be trying to fix it themselves to start with if that were the case, but how do I know that?  
Thanks for defining your level of ability, more or less.

You know you can't mess with a mounted partition.  Does that mean you think you can mess with an unmounted partition on an active drive?  Maybe, maybe not, that one is undefined, because we (me at least) don't know which partition is screwed up, is it sda1, that's reporting it's end already into the beginning of the next partition, or is it sda2, that's misreporting it's beginning.  So I don't think we can say with any amount of veracity whether sda1, sda2, or who knows what else is actually screwed up.  The effect is that both partitions are reporting the block numbers incorrectly.  Any maybe it's a cylinder vs. Mib block problem, ahhh, the sun is finally shining, I'm going outside.

I eat crickets any time of day

---

### Post by CVGH on 2011-04-03
I guess my experience level is "advanced noob" :P
I used to run Kanotix as a live CD with usb as /home but got a iPhone last year, so have stuck to XP for itunes since.
Always wanted to have Linux at work and thought that when I got a new pc, I'd make sure the guys made it dual boot.

I thought you could mess with a partition as long as it wasn't mounted, but guess I learned something new!!

I'm going to boot the Gparted iso Monday and see what happens with fdisk....

---

### Post by CVGH on 2011-04-03
Thanks for the tip on the software, I'll check it out.

AFAIK, this happened when I ran the install from the Ubuntu CD,
should have done the partitions manually I guess.....

---

### Post by Pumalite on 2011-04-03
That's the best way to do it.

---

### Post by Hakunka-Matata on 2011-04-03
It seemed you were experienced, and thanks for being frank about your level of expertise, much more efficient communications from here on.

My boss was always aware of the people who seemed warm and happy at work, he knew who had GNU/Linux running with VLC playing the network stream  [http://www.radioparadise.com/musiclinks/rp_128aac.m3u](http://www.radioparadise.com/musiclinks/rp_128aac.m3u),  and projectM makin the graphics card's Heat Sync glow a bit red!

I'll bet a bit of dosh, you'll return Monday evening with a report of success.  Keep the faith brother, remember, HE loves music too.

---

### Post by srs5694 on 2011-04-04
If the Ubuntu installer created overlapping partitions, then that's a very serious bug. My impression was that the Ubuntu installer's partitioner is based on libparted, and that this is true for both manual and automatic installations, but I'm not positive of that. I've never before heard of libparted creating overlapping partitions like this, but of course it's possible it's caused by a bug that doesn't turn up very often.

Fortunately, there are alternatives to libparted, although they aren't as easy to use as the GUI partitioner in the Ubuntu installer. Specifically, Linux's fdisk, sfdisk, and cfdisk utilities can do the job for MBR disks; and my GPT fdisk (gdisk and sgdisk) can do it for GPT disks. All of these tools do partitioning alone; if you use them, you'll need to create filesystems with mkfs or similar tools.

---

### Post by fudoki on 2011-04-04
The listing to 9.xx is an "artifact", the list simply did not update and delete this old line.

If 10.10 and XP are both working fine, then LEAVE IT ALONE.  You will only create problems where none now exist.

Sounds to me like the install went just fine (you say everything is working).  Updating the list is one of the very last "housekeeping" steps in the install, and on dual-boot machines the reference to the old version is not always removed correctly.  This means nothing. It's just a clerical error on a list.  Ignore it.

The seeming misreporting of the partitions, a seeming overlap, is likely a similar error.  If this were really the case Windows would likely not boot, and Linux would either fail to load or give you pages of error messages in the log files.  Check /var/log/system.log and/or /var/log/message.log - if there are not messages about partition size problems, don't worry about it.

Since this is a production machine at work, you should have backups of your data regardless.  Keep these current.  Still, this sounds like some of the typical problems dual-boot setups sometimes have, caused by differences in the way Windows and everything else counts and reports disk space, etc.  The Windows folks think they have a better idea, and confusion is often the result.  Trust what the Linux side says.  If the partitions really overlapped, you would have serious, obvious problems and would not be saying that both systems work...

The risk of breaking something fooling with the partitions and boot parameters is high.  Sounds like you are a "normal" user, not a Linux guru.  If it ain't broke, don't fix it.  Windows can be hostile in dual boot situations, and MBRing from the Windows side will make Linux inaccessible, most likely, and may well damage the partition table, or worse.  This is not your machine (I assume you don't own the company here), so be conservative.

The reference to the #2 partition sounds like it may be the "host" partition of the "logical" partition that Linux is installed on.  Both these partitions occupy the same space - logical partitions are made "inside" physical partitions.  I won't confuse you with the technical reasons for this and why many installers create logical partitions when physical partitions are available - it's an old technical argument.

Sounds like you don't have a real problem, but you will have if you start MBRing, partition resizing, etc.  Folks are trying to be helpful here, but unless 10.10 or Windows are not working correctly, or you are missing a big block of disk space, your only problem is a leftover entry in your OS list.  No big deal.

---

### Post by fudoki on 2011-04-04
Be aware that in most cases changing the size of a pratition can lead to loss of all the data on the partition.  Backup first!

Also, be sure you are not mistaking the space that is automatically set aside by the system for "spare" sectors for "unused" space.  A percentage (usually 3% to 5%, depending on disk capacity) is set aside in case sectors fail over time.  These "spare" sectors are then mapped to hold the data that would be held by the sectors that went bad.  This is normal in all hard drives, and often a source of confusion.  You definitely want to leave some spare sectors, else, when sectors fail (as they will over time) the drive will become unusable.  No bad sectors are allowed in the data area, yet some sectors will fail over time.  Keeping some spare sectors unallocated solves this dilema.

---

### Post by Hakunka-Matata on 2011-04-04
fudoki, it sounds like you know your onions.....eemmhh, peaches?  From the purely technical POV your argument is solid.  From the GNU/Linux side I believe your argument is nothing more than an additional, exceptionally fresh and informative post.  Leaving something like that half baked is not in my playbook. As you say, it's working, and therefore the OP should leave it alone.  I say what's wrong with messing (BIGTIME I might add) with the partition table and everything else about the HDD if the worst that can happen is to break it.  He's backed up, so big bananas if it breaks, reload and reload with a larger magazine for ammo than  extant to date.
Great, very informative post, thanks.  
I'll be waiting with baited breath to see what a few other FMs have to say about your philosophy, like 'oldfred, drs305, cariboo907, Quackers, kansasnoob, willee-nillee and more I've not listed (read don't recall handles of).  Those guys are tried and true and I dare say, your opinion runs counter to what the general mo is here.
thanks again,

---

### Post by overdrank on 2011-04-04
Threads merged :)

---

### Post by Quackers on 2011-04-04
fudoki,
there are other users of this forum much better qualified to respond to your posts, and no doubt they will. However, I would say that to ignore the possibility of overlapping partitions is not sensible imho. 
It is even more important when the last blocks of a Windows partition are involved. This is because Windows uses the last blocks of its partitions for storing some data. The likelihood of two different operating systems writing data to the same blocks is a very serious problem. In my view it is much better to fix things now, before problems occur.
You advise the OP to trust the Linux side of things, but it is the Linux side of things that is reporting a problem, yet you advise the OP to leave things alone. This seems somewhat contradictory.
Several similar situations have been seen on this forum previously. If you do a search you will see that most of these seem to be resolved relatively painlessly (due mostly to srs5694's detailed explanations and methods - indeed sometimes his own programs are used).
I agree wholeheartedly that partitioning is potentially disastrous, and that it should be taken on with much more caution than some users appear to take. It seems that many people don't even have backups or a means to recover their system in the event of an accident! This is folly, in my view, and should be avoided at all costs!
However, in this case, it appears that the damage has been done and whether there are any symptoms present at the moment, or not, it is likely that serious problems will result at some time, in my opinion.

---

### Post by srs5694 on 2011-04-04
> **fudoki said:**
> The seeming misreporting of the partitions, a seeming overlap, is likely a similar error.  If this were really the case Windows would likely not boot, and Linux would either fail to load or give you pages of error messages in the log files.  Check /var/log/system.log and/or /var/log/message.log - if there are not messages about partition size problems, don't worry about it.

Do ***not*** ignore overlapping partitions!!!!!

If you think the reporting utility is misreporting the issue, you can cross-check it with something else. Linux's fdisk, GNU Parted, and GPT fdisk (gdisk) are all independent code bases. If any two of these utilities report the same partition start and end points that overlap, then ***it is real***. You can use the following commands to check partition sizes with sector precision:

```

sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

```

Note that the fdisk results will be uninformative for GPT disks, but the OP doesn't seem to have GPT disks; I mention this only in case somebody who does have GPT disks runs across this thread in the future.

The logic that an OS would not boot or would report errors in case of overlapping partitions is, sadly, mistaken. I've deliberately created overlapping partitions in the past, and in my experience, OSes don't gripe about it in normal use. They just use the partitions they're fed. This can work fine for a long time, until some write operation happens to trample on data used in the other partition. At that point, problems are likely to crop up, but not before.

Thus, I must ***strongly*** advise that CVGH fix this problem. If doing so immediately is impossible, don't write to either of the overlapping partitions until a fix can be implemented.

> Since this is a production machine at work, you should have backups of your data regardless.  Keep these current.

This is certainly good advice.

> Still, this sounds like some of the typical problems dual-boot setups sometimes have, caused by differences in the way Windows and everything else counts and reports disk space, etc.  The Windows folks think they have a better idea, and confusion is often the result.

It sounds like you may be thinking of differences in the way cylinder/head/sector (CHS) values were determined in the past. This did indeed cause problems a decade or two ago, but all hard disks larger than about 8 GiB use logical block addressing (LBA) values to define partitions, since the CHS fields in the Master Boot Record (MBR) partitioning system max out at a bit under 8 GiB. With LBA mode, there's no confusion over CHS values. The Boot Info Script output in post #3 of this thread clearly shows LBA values that overlap. The Boot Info Script output even warns explicitly about this. The problem is almost certainly real, and not an artifact.

> The risk of breaking something fooling with the partitions and boot parameters is high.  Sounds like you are a "normal" user, not a Linux guru.  If it ain't broke, don't fix it.

It is (almost certainly) broke, though. The breakage is likely to cause data loss at some unknown point in the future, if the disks are used enough.

> The reference to the #2 partition sounds like it may be the "host" partition of the "logical" partition that Linux is installed on. Both these partitions occupy the same space - logical partitions are made "inside" physical partitions.

Post #3 includes Boot Info Script output that clearly identifies partition #2 as being a FAT32 partition, and partition #4 as being an extended partition (which you refer to with the non-standard term "physical partition").

> Sounds like you don't have a real problem, but you will have if you start MBRing, partition resizing, etc.  Folks are trying to be helpful here, but unless 10.10 or Windows are not working correctly, or you are missing a big block of disk space, your only problem is a leftover entry in your OS list.  No big deal.

I must ***strongly*** disagree with your analysis. The overlapping partitions problem is almost certainly real, and given that, if the partitions are used for long enough, the overlap *will* eventually cause data loss.

---

### Post by CVGH on 2011-04-04
Well, I was wondering the same thing as fudoki. If there is a problem, why no errors or signs of data loss?

What I think I'm going to do is get any CAD/Word/Excel, etc files off sda1 and onto a CD.
Then I'm going to disable the swap file and defrag sda1. Then I'm going to use Easeus to remove all partitions and then expand "c:" to the full 80GB.
Question is does this fix the MBR and remove GRUB? In other words, will I be able to reboot into windo$e as if nothing had happened[I'm sure it will probably run chkdsk]?
I have no data I need in Ubuntu as I've just started using it.

Thank You to everyone for all the help!!!

Brian

---

### Post by Quackers on 2011-04-04
I think your first question has already been answered.
If that's the route you choose to take, you will need to restore the Windows bootloader to the mbr of the drive with a Windows repair/installation disc. Otherwise you'll just get a grub error and Windows won't boot.

I feel bound to point out that if you delete all the other partitions, that may, or may not, remove Windows data from the end of its partition. That's the risk you will be taking.

---

### Post by srs5694 on 2011-04-04
> **CVGH said:**
> Well, I was wondering the same thing as fudoki. If there is a problem, why no errors or signs of data loss?

Partly it's a matter of probabilities. Your /dev/sda1 is 67,890,627 sectors in size, /dev/sda5 is 32,983,040, and the area of overlap is 11,870 sectors. That means that the overlap is 0.017% of /dev/sda1's size, and 0.036% of /dev/sda5's size. I don't recall your specifying how full either of those partitions is, but given the small amount of overlap, it's entirely plausible that these areas simply aren't currently used by files on both filesystems. If the filesystems are used for long enough, or filled to capacity, though, there *will* be conflicts, sooner or later.

Another factor is that there could already be damage and you're just not aware of it. Suppose that an NTFS file got saved into a location where an ext4fs file already existed. This data corruption might go unnoticed until you tried to use the ext4fs file.

I'd also like to point out that there's a very critical, albeit very small, data structure included in the overlap: It's the Extended Boot Record (EBR) for /dev/sda5. This is a partitioning data structure that defines the start and end point of /dev/sda5 and points to the next logical partition (/dev/sda6). This EBR is just one sector in size, but if Windows (or, if you mount /dev/sda1 read/write in Linux, Linux) decides to write to that one sector, you'll become unable to access your Linux installation at all. You might be able to recover from this disaster by using the data posted in this thread, but such a write operation might well write over some critical ext4fs data, thus making full recovery impossible. Of course, unless you fill the disk completely, the odds of this happening are fairly small, but the consequences would be pretty bad. I wouldn't want to risk it.

> What I think I'm going to do is get any CAD/Word/Excel, etc files off sda1 and onto a CD.
Then I'm going to disable the swap file and defrag sda1. Then I'm going to use Easeus to remove all partitions and then expand "c:" to the full 80GB.

That should work, but it will of course wipe out Linux. I'd do it a bit differently:


[list=1]
[*]Back up your important data.
[*]Use Linux's fdisk to delete /dev/sda6, /dev/sda5, and /dev/sda4, in that order. You can do this from your regular Linux boot. I recommend using fdisk for this because I'm certain that fdisk does *not* write into the partitions it modifies. I don't know how EASEUS works in that respect; if it writes into the space it frees up, it could damage NTFS data. If you're certain EASEUS doesn't do this, you could use it instead, which will obviate the next step. Alternatively, you could use the Windows version of FixParts to do this, which will also obviate the next step.
[*]Boot using a Windows emergency disc.
[*]Run CHKDSK on C: (/dev/sda1).
[*]Repair the MBR. (See below.)
[*]Reboot to Windows.
[*]If desired, resize C: to fill the available space on the disk.
[/list]


> Question is does this fix the MBR and remove GRUB? In other words, will I be able to reboot into windo$e as if nothing had happened[I'm sure it will probably run chkdsk]?

No, you won't be able to boot Windows, at least not without further fixes. GRUB will still be installed to the MBR, and it will be trying to locate files on a Linux partition that will no longer exist. This situation can be corrected by re-installing a standard Windows boot loader to the MBR. I'm pretty sure that the Windows installation/recovery disc can do this, but I don't recall the exact commands, offhand. In the old DOS/Win9x days, "FDISK /FIXMBR" would do this, but I'm not sure if this command is still valid with modern versions of Windows. Alternatively, you could install a third-party boot loader to the MBR. [GRUB4DOS](http://gna.org/projects/grub4dos/) should work, for instance.

---

### Post by CVGH on 2011-04-05
Hi Rod,

Haven't had a chance to really dig into this yet but I did realise that
sda2 is empty. sda4 contains logical partitions 5 and 6 right?
Can I just delete sda2?

Thanks!

Brian

---

### Post by srs5694 on 2011-04-05
> **CVGH said:**
> Haven't had a chance to really dig into this yet but I did realise that
sda2 is empty. sda4 contains logical partitions 5 and 6 right?
Can I just delete sda2?

If /dev/sda2 is empty, then yes, deleting it should be safe. It won't help you solve your problems, though, since the overlap is between partitions /dev/sda1 and /dev/sda5 (and therefore also /dev/sda4, the extended partition that contains /dev/sda5). Despite the fact that the number 2 comes between the numbers 1 and 5, /dev/sda2 does not come between /dev/sda1 and /dev/sda5 in terms of on-disk locations. Check the start sector numbers in the Boot Info Script output from your post #3:

> ```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    67,890,689    67,890,627   7 HPFS/NTFS
/dev/sda2         102,397,952   156,301,311    53,903,360   b W95 FAT32
/dev/sda4          67,878,910   102,397,951    34,519,042   5 Extended
/dev/sda5          67,878,912   100,861,951    32,983,040  83 Linux
/dev/sda6         100,864,000   102,397,951     1,533,952  82 Linux swap / Solaris

```

This out-of-order nature of the partition numbers is confusing but legal.

---

### Post by CVGH on 2011-04-05
Hi Rod,

sudo fdisk -l:

```
root@briansUbuntu:/home/brian# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a5f9a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4226    33945313+   7  HPFS/NTFS
/dev/sda2            6374        9730    26951680    b  W95 FAT32
/dev/sda4            4226        6374    17259521    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            4226        6279    16491520   83  Linux
/dev/sda6            6279        6374      766976   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Has something changed here?

sda1 and sda2 are Primary. sda4 is Primary with sda5 and sda6 Logical partitions?

Brian

---

### Post by oldfred on 2011-04-05
You need to run this as it shows more detail.

sudo fdisk -lu /dev/sda

---

### Post by Hakunka-Matata on 2011-04-05
At this level of diagnosis, the words become a picture, a Large Clear Highly defined and memorable picture, thank you guys, very much indeed.  'you guys' logically equal to those who have jumped in with abandon post post#33, you know who you are.  I appreciate it very much, it's gratifying and it better be gratifying to the OP as well, I have the feeling it
 is.  Great thread.

CIAO

---

### Post by CVGH on 2011-04-06
sudo fdisk -lu /dev/sda

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a5f9a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    67890689    33945313+   7  HPFS/NTFS
/dev/sda2       102397952   156301311    26951680    b  W95 FAT32
/dev/sda4        67878910   102397951    17259521    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5        67878912   100861951    16491520   83  Linux
/dev/sda6       100864000   102397951      766976   82  Linux swap / Solaris

Partition table entries are not in disk order
```Looks like a sector view has more info than cylinder view.....

Ok, I need to check out Rod's tools I think....

Brian

---

### Post by Quackers on 2011-04-06
It still appears that partitions overlap.

---

### Post by Hakunka-Matata on 2011-04-08
I trust that surprises no one?

---

### Post by Hakunka-Matata on 2011-04-08
Evidently my smartie-pants responses occasionally get mis-interrupted, which is simply another way of saying I'm not being clear.  You all do have my sincere apologies.  As My account here on ubuntuforums is now carrying  a debt load of 1 point as a result of my post in (hold for salient data), I shall endeavour to be more elegantly verbose in the likely futile attempt to clear the record.  As is usually (always) the case "the cloud has a silver (read any commodity in this market) lining.  Thankful I am that good education continues to be this inexpensive in our uniquely modeled countries political anatomy.  GO FW.

cheerio mate (ies)  HK

---

### Post by yasirimteyaz on 2011-04-29
I am also facing overlapping partitions issue. :(

Following is the output of fdisk -l command. 
It seems that there is overlapping with swap partition.  Ain't.?

Any help would be appreciated.


$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01ff01fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1994    16016773+   7  HPFS/NTFS
/dev/sda2            1995       14593   101200865+   f  W95 Ext'd (LBA)
/dev/sda3            2147        4806    21366418+  83  Linux
/dev/sda5            1995        2146     1219584   82  Linux swap / Solaris
/dev/sda6            4807        7413    20940696    7  HPFS/NTFS
/dev/sda7            7414       13917    52243348+   7  HPFS/NTFS
/dev/sda8           13918       14593     5429938+   b  W95 FAT32


Thanks.

---

### Post by oldfred on 2011-04-29
@yasirimteyaz
Your extended has to overlap. The extended is just a container for all the logical partitions it holds. parted or fdisk -lu show more detail. See above posts.

---

### Post by yasirimteyaz on 2011-04-29
fdisk -lu gives out following results:


```

 sudo fdisk -lu 
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01ff01fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    32033609    16016773+   7  HPFS/NTFS
/dev/sda2        32034814   234436544   101200865+   f  W95 Ext'd (LBA)
/dev/sda3        34475553    77208389    21366418+  83  Linux
/dev/sda5        32034816    34473983     1219584   82  Linux swap / Solaris
/dev/sda6        77208453   119089844    20940696    7  HPFS/NTFS
/dev/sda7       119089908   223576604    52243348+   7  HPFS/NTFS
/dev/sda8       223576668   234436544     5429938+   b  W95 FAT32


```

parted doesn't seem to work and gparted gives out ovelapping partitions warning. :(

---

### Post by srs5694 on 2011-04-29
Your /dev/sda3 (a primary partition) resides within /dev/sda2 (an extended partition). This is a no-no. FWIW, the Windows XP installer is known to break disks in this way under some circumstances, and there may be other tools that do the same.

Before proceeding, I recommend you back up your partition table and all important data on the disk; there's always a chance that repair efforts will make matters worse. (Partition table backups are covered on the page I'm about to reference.)

Repairing this damage is most easily done with my [FixParts](http://www.rodsbooks.com/fixparts/) program. After backing up the partition table, as described on the FixParts page, run the program, type "p" to view the partitions and verify that they'll all be included (all six of your non-extended partitions are present and none is marked as "omitted"), and type "w" to save the changes. One caveat: Windows must boot from a primary partition. It appears that your /dev/sda1 is a primary, and so is probably your Windows boot partition. Be sure that FixParts doesn't try to change /dev/sda1 to a logical partition. Chances are /dev/sda3 and /dev/sda5 were both originally logical partitions, and you might try to configure them that way for greatest flexibility; however, if FixParts makes them both primaries and you don't want to mess with it, that should work too.

---

### Post by CVGH on 2011-05-10
It was time for a new harddrive anyhow, so got a 300GB and installed Ubuntu 10.10. Enough of this windo$e foolishness........

Thanks to you all for helping!!

---

### Post by BreuJa on 2011-07-25
Well, I personally don't consider buying a new harddisk as an solution, however...

I just ran into the same problem and the trick was to just set the alignment to "cylinder" instead of "MiB" (which is the default).

HTH

---

