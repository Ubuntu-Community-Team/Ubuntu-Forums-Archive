---
title: "Booting from BIOS or from Live CD 'first hard drive'??"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-05-08
If an old bios and mainboard is being used, such that it cannot handle the large size of HD, then is it useful to say use a live CD and from its initial menu (pressed a key), choose 
'Boot From First Hard Disk'?
Would this be similar in getting around a bios and disk size limitation I wonder - like - does  the use of a live CD in this way avoid using the bios to point to the active partition??

You can probably tell I do not know that much about this subject so please excuse lack of understanding here.

The reason for asking is that a friend has a couple of quality old rack mounted server machines and wants to use Ubuntu having now fitted 80 GB empty drives. Live CD seems ok, and 11.04 install goes ok but on boot up grub comes back with an error.

I recall that early machines cannot see larger(?) HDs  for booting purposes even though installs go ok in very large HDs.
I wondered if a live CD to boot up temporarily - trouble shooting - would be worth trying for this reason, or am I way off?

tia

---

### Post by Hedgehog1 on 2011-05-08
I believe that the 80 gig size is not the limit (it is more around 137 gigs).

You can get around that limit by making sure your first partition is smaller.

For example:

[B]/dev/sda1 20 gigs ext4 '/' (root)
/dev/sda2 55 gigs ext4 '/home'
/dev/sda3 5 gigs swap[/B]

Depending on how the servers were used, they may have vestiges of software raid setups on them, and this can cause issues like this until that is all removed.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-08
If the severs have internet access, can you or your friend do the following from them:

Boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.


***The Hedge***

:KS

---

### Post by candtalan on 2011-05-08
> **Hedgehog1 said:**
> If the severs have internet access, can you or your friend do the following from them:

Boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***
:KS

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   154,222,591   154,220,544  83 Linux
/dev/sda2         154,224,638   156,301,311     2,076,674   5 Extended
/dev/sda5         154,224,640   156,301,311     2,076,672  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2005 MB, 2005925888 bytes
32 heads, 62 sectors/track, 1974 cylinders, total 3917824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            512     3,917,823     3,917,312   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        161a6a4b-3061-4506-bdcd-18efe731ec4b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ad581a86-98bf-4da1-851e-bfb3711c8a7a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1DE9-0E48                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=161a6a4b-3061-4506-bdcd-18efe731ec4b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=161a6a4b-3061-4506-bdcd-18efe731ec4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 161a6a4b-3061-4506-bdcd-18efe731ec4b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=161a6a4b-3061-4506-bdcd-18efe731ec4b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad581a86-98bf-4da1-851e-bfb3711c8a7a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  62.4GB: boot/grub/core.img
  62.4GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.38-8-generic
    .2GB: boot/vmlinuz-2.6.38-8-generic
    .5GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 02 00 00  |........?.......|
00000020  00 c6 3b 00 c6 1d 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 48 0e e9 1d 4e  4f 20 4e 41 4d 45 20 20  |..)H...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 78  f7 24 00 66 ba 00 00 00  |..E}.f.x.$.f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

He sent me this file it looks like what you asked?

I also just found this:
ubuntu 10.10 Grub gives message error: out of disk Bug #668224
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/668224](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/668224)

which also sounds possible?

---

### Post by candtalan on 2011-05-08
> I believe that the 80 gig size is not the limit (it is more around 137 gigs).


Mmm. According to this old and historic item:
=============
BIOS dated 1998 or later can work with drives up to 32 gigabytes.....The 32GB barrier is due to the inability of the BIOS to address an LBA that is larger than 66,060,287. Only in the most recent computer systems has the BIOS been upgraded to work with drives larger than 32GB. In addition, in some computers, a 64GB barrier is still to be overcome.
=============
link:
[http://www.spcug.org/reviews/bl0107.htm](http://www.spcug.org/reviews/bl0107.htm)

I have seen HDs with a 32GB limit jumper position I think, also.

On this direction - coming back to the question of booting from a live CD, will it work? ( I do not think it has been tried here yet)

tia

---

### Post by oldfred on 2011-05-08
How old is system?

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

> Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
                                    

---

### Post by Hedgehog1 on 2011-05-08
> **candtalan said:**
> Mmm. According to this old and historic item:
=============
BIOS dated 1998 or later can work with drives up to 32 gigabytes.....The 32GB barrier is due to the inability of the BIOS to address an LBA that is larger than 66,060,287. Only in the most recent computer systems has the BIOS been upgraded to work with drives larger than 32GB. In addition, in some computers, a 64GB barrier is still to be overcome.
=============
link:
[http://www.spcug.org/reviews/bl0107.htm](http://www.spcug.org/reviews/bl0107.htm)

I have seen HDs with a 32GB limit jumper position I think, also.

On this direction - coming back to the question of booting from a live CD, will it work? ( I do not think it has been tried here yet)

tia

OK - I will add this to my 'really REALLY old hardware trivia file' (one forgets when all his drives are 1tb and larger).  :D

So, the install following this method:

> For example:

/dev/sda1 20 gigs ext4 '/' (root)
/dev/sda2 55 gigs ext4 '/home'
/dev/sda3 5 gigs swap

Should get Ubuntu working on the server, as the first partition is less than 32 gigs.

This will give a much faster speed then permanently booting from a customized CD.

***The Hedge***

:KS

p.s. Swap partiton size should be: Size of RAM + 10%.

---

### Post by candtalan on 2011-05-08
Thanks everyone for the responses!

---

### Post by candtalan on 2011-05-09
Latest information is that when the same drive is used to install xp, then xp boots ok, so it i snot th edrive size as I postulated, anyway the hardware is apparently this
[http://www.supermicro.com/products/system/1U/5013/SYS-5013G-M.cfm](http://www.supermicro.com/products/system/1U/5013/SYS-5013G-M.cfm)
(P4) so it is not so old as I had guessed after all.

Still trying things...

---

