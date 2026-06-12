---
title: "Ubuntu 11.04 / Windows XP Dual Boot Problem"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by iCeD00D on 2011-07-02
Good evening. It seems that after loading Ubuntu 11.04 along side Windows XP (same hard drive) I can not get Windows to boot. It shows up in the grub menu but when I select it, the screen goes blank with the 'dos' prompt just sitting there blinking. No Windows. I can boot into Ubuntu just fine. Below is my grub menu for Windows. Thanks in advance.. 
 
GNU Grub v1.99~rc1-12ubuntu3
 
setparams 'Microsoft Windows XP Professional (on /dev/sda1)'
 
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root F410174B8D2FCF79
drivemap -s (hd0) ${root}
chainloader +1

---

### Post by Pen16 on 2011-07-03
Im having the same problem, im not as accustomed to ubuntu as i am with windows.

I first installed a copy of xp onto a 100 gb hard drive and then from that os i downloaded and burnt a copy of ubuntu to install on my 200 gb hard drive.  I installed it no problem and still sustained the dual boot menu so i could chose between the two. but something happened.

I think i was either messing around with a compiz or it came from the installation of nvidia accelerated graphics driver 173. But now when i boot the machine, after the initial bios boot options, my screen goes completly blank for awhile and then all of a sudden the ubuntu login screen pops up and i can log in. When i log in under regular graphics mode everythings fine but i have no titlebars on anything(which im sure that has to do with compiz)

But my main concern is i cant boot my windows anymore, even from selecting the winders hard drive to boot first all it does is hang with a dos prompt like iCed00d.
It hasn't been real pressing until recently, i need to use some xp software.

I thought if i changed my grub from the terminal it would fix it, i changed the line Grub-default=0 to my xp installation which happen to be six but alas i have no change.

Is anyone willing to help?

---

### Post by shrakmoose on 2011-07-03
When did this occur for you (I have the same problem)?

---

### Post by Lkm on 2011-07-03
Hello, did you install ubuntu on the same partition as windows or a different one?

---

### Post by shrakmoose on 2011-07-03
I did the one where you can just use a slider to do the partitioning and the Ubuntu installer did the rest.

---

### Post by mörgæs on 2011-07-03
This one might help:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have not tried myself, though.

---

### Post by shrakmoose on 2011-07-04
That only installed the grub thingy again and left me with the same problems. Do you have any other techniques?

---

### Post by mörgæs on 2011-07-04
No, sorry. I left Windows five years ago.

---

### Post by shrakmoose on 2011-07-05
do you think it would work if i forced grub into the first partition, where windows is installed?

---

### Post by YesWeCan on 2011-07-05
[FONT=Arial][SIZE=2]Three of you have the same Xp/11.04 problem?
More specific info may help diagnose it. You may want to download and run this, and post the RESULTS.txt file here: [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Navy]http://bootinfoscript.sourceforge.net/[/COLOR][/SIZE][/FONT]

[FONT=Nimbus Sans L, sans-serif][SIZE=2]I wouldn't recommend installing Grub to a partition using grub-install because although this is the intuitive place for it, there is a potential reliability problem due to the way the Grub boot code locates the first Grub file when installed this way. You can do it and make the partition "active" and keep your standard MBR code and it will work but may not work forever.[/SIZE][/FONT]

You definitely don't want to force install it to your Windows partition because it will overwrite your Windows boot code and Grub needs to run this code to boot Windows!

[FONT=Nimbus Sans L, sans-serif][SIZE=2]If your Ubuntu partition is "logical" rather than "primary" the MBR code will not be able to boot it directly and the Grub installer does not set up the extended partition boot code needed to enable this. This is another reason the Grub code is put in the MBR by default.
[/SIZE][/FONT]

---

### Post by Teraunce on 2011-07-05
well, I have a similar problem. the GRUB boot menu doesn't even show up and it defaults automatically to the windows one, which lacks an entry for grub. I have Ubuntu installed on a 3rd partition on my hard drive, the logical partition, and my question is how to set boot.ini to point to GRUB.

---

### Post by shrakmoose on 2011-07-06
Hears my results file:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   105,875,615   105,875,553   7 NTFS / exFAT / HPFS
/dev/sda2         105,877,502   160,086,015    54,208,514   5 Extended
/dev/sda5         105,877,504   156,940,287    51,062,784  83 Linux
/dev/sda6         156,942,336   160,086,015     3,143,680  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52CC7949CC79287D                       ntfs       
/dev/sda5        066c1688-b12a-4495-8345-d2e6b638f0ec   ext4       
/dev/sda6        60461e6a-445c-4e47-87ed-78b93a7163a6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/52CC7949CC79287D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=066c1688-b12a-4495-8345-d2e6b638f0ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=066c1688-b12a-4495-8345-d2e6b638f0ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 066c1688-b12a-4495-8345-d2e6b638f0ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52CC7949CC79287D
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=066c1688-b12a-4495-8345-d2e6b638f0ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=60461e6a-445c-4e47-87ed-78b93a7163a6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.676322937 = 78.035607552   boot/grub/core.img                             1
  60.700153351 = 65.176293376   boot/grub/grub.cfg                             1
  65.775318146 = 70.625710080   boot/initrd.img-2.6.38-8-generic               2
  72.819499969 = 78.189342720   boot/vmlinuz-2.6.38-8-generic                  1
  65.775318146 = 70.625710080   initrd.img                                     2
  72.819499969 = 78.189342720   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  52 b6 44 8a 10 52 16 21  29 47 12 d2 53 42 29 32  |R.D..R.!)G..SB)2|
00000010  92 87 d4 2c 69 69 21 54  97 52 2b 2a 25 14 2c 69  |...,ii!T.R+*%.,i|
00000020  20 00 52 fd 30 1d 69 86  55 20 a5 d8 46 13 ea 11  | .R.0.i.U ..F...|
00000030  01 d6 99 a6 91 40 24 98  9c b5 08 13 50 06 51 43  |.....@$.....P.QC|
00000040  e0 00 0a 92 6a 90 53 50  04 55 48 15 11 29 23 0a  |....j.SP.UH..)#.|
00000050  52 42 00 40 15 52 9a 94  50 8a a9 21 08 06 92 04  |RB.@.R..P..!....|
00000060  92 92 84 6c 84 55 49 02  4b 02 53 02 07 44 28 26  |...l.UI.K.S..D(&|
00000070  05 52 11 35 10 c0 d2 94  98 05 24 81 a9 22 80 52  |.R.5......$..".R|
00000080  ac 06 50 04 91 42 0a 49  a8 36 92 5a c1 b7 52 01  |..P..B.I.6.Z..R.|
00000090  88 00 2b 04 8d 61 13 a8  15 48 12 48 06 a3 4c 5f  |..+..a...H.H..L_|
000000a0  14 09 98 29 49 14 51 56  92 87 d4 21 08 12 57 01  |...)I.QV...!..W.|
000000b0  aa 11 55 35 2a d2 40 29  31 a0 52 9a a9 20 14 c0  |..U5*.@)1.R.. ..|
000000c0  00 40 60 1d 08 02 2c 01  54 ee 18 09 2d 54 a5 25  |.@`...,.T...-T.%|
000000d0  46 b2 4e ce 84 b4 98 42  bd 97 88 6b bc 8a b4 bd  |F.N....B...k....|
000000e0  60 1e a4 9f 90 b1 73 02  1f 53 28 59 45 c8 4f b3  |`.....s..S(YE.O.|
000000f0  d3 7c 1e 99 d9 9d e9 9b  c6 f4 83 9e 74 ce 4e 80  |.|..........t.N.|
00000100  f4 b8 c7 a2 11 bc a2 2e  40 de 08 5c 97 b4 50 7f  |........@..\..P.|
00000110  3a 4c 02 f1 62 93 9b 44  26 26 30 31 24 31 30 0c  |:L..b..D&&01$10.|
00000120  dc 01 99 61 c0 c4 da a4  7e 51 82 0d ba 38 04 7f  |...a....~Q...8..|
00000130  6c 7c 3c d2 e6 e5 a7 89  57 12 b3 08 ae 69 73 72  |l|<.....W....isr|
00000140  d3 c4 ab 89 59 84 50 86  3e fc a9 5a 18 26 6d dc  |....Y.P.>..Z.&m.|
00000150  6b 4b 4b 4b 69 92 b5 6e  36 fa 43 e0 02 28 09 a2  |kKKKi..n6.C..(..|
00000160  aa 49 35 4b f5 b8 0f d2  08 a6 8b 72 56 93 4f 12  |.I5K.......rV.O.|
00000170  d3 f8 29 87 d8 46 4a 0c  d5 49 49 09 a0 04 d3 94  |..)..FJ..II.....|
00000180  13 4a 10 65 24 d0 6a a4  23 ff 25 05 2e cb 41 92  |.J.e$.j.#.%...A.|
00000190  81 2c 2d 64 82 50 50 85  b0 12 70 eb 25 3a a0 89  |.,-d.PP...p.%:..|
000001a0  2b 3c 03 04 88 69 82 58  10 40 20 83 57 4c 21 92  |+<...i.X.@ .WL!.|
000001b0  d2 4b 13 35 20 8b 80 4c  99 09 d0 c2 30 c4 00 fe  |.K.5 ..L....0...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 28 0b 03 00 fe  |...........(....|
000001d0  ff ff 05 fe ff ff 02 28  0b 03 00 00 30 00 00 00  |.......(....0...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```But i dont know what any of it means

---

### Post by YesWeCan on 2011-07-06
> **shrakmoose said:**
> Hears my results file:
But i dont know what any of it means
You don't want to know. :P
It looks squeaky clean to me except that you have some Wubi files in your XP partition. Were you running Ubuntu with Wubi before you installed Ubuntu separately?
This may or may not be the cause of XP failing to complete its boot. I don't know anything about Wubi so I can't advise; you may want to look into how to remove it completely.
Or you can use your XP disk to repair your system and this will make XP boot again. Then you can re-install Grub using your Ubuntu live CD/USB (must be same Ubuntu version as on disk):
[COLOR="Navy"]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

---

### Post by shrakmoose on 2011-07-06
I had Wubi cause i thought i needed it to install ubuntu (turns out you don't) and so i never bothered to delete it. I couldn't delete it from the windows side after because i couldn't enter windows straight after. I don't have the XP disk either because some guy gave  me the computer for free, without anything else.

---

### Post by YesWeCan on 2011-07-08
> **shrakmoose said:**
> I had Wubi cause i thought i needed it to install ubuntu (turns out you don't) and so i never bothered to delete it. I couldn't delete it from the windows side after because i couldn't enter windows straight after. I don't have the XP disk either because some guy gave  me the computer for free, without anything else.
It might be as simple as editing the boot.ini file and removing any entries related to Wubi. I am not sure whether this will fix XP boot or not.

---

### Post by Tiraryoko on 2011-07-08
Hello, I seem to be having a similar problem. I had windows XP installed on one hard drive and then decided to install Ubuntu 11.04 on a second hard drive. Now my computer boots straight into Ubuntu with no choices of going into Windows XP. 

Here is my results.txt:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 54855680 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    77,129,727    77,127,680  83 Linux
/dev/sdb2          77,131,774    78,176,255     1,044,482   5 Extended
/dev/sdb5          77,131,776    78,176,255     1,044,480  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DCB4D067B4D04624                       ntfs       
/dev/sdb1        8da9fc34-794c-494d-8328-5816e010e049   ext4       
/dev/sdb5        bd4ee072-7209-4e2a-beba-1648c1ce9f0f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
if background_color 44,0,30; then
  clear
fi
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
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8da9fc34-794c-494d-8328-5816e010e049 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8da9fc34-794c-494d-8328-5816e010e049 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8da9fc34-794c-494d-8328-5816e010e049
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8da9fc34-794c-494d-8328-5816e010e049 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=bd4ee072-7209-4e2a-beba-1648c1ce9f0f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  26.157253265 = 28.086136832   boot/grub/core.img                             1
  26.159622192 = 28.088680448   boot/grub/grub.cfg                             1
  26.368164062 = 28.312600576   boot/initrd.img-2.6.38-8-generic               2
  26.255187988 = 28.191293440   boot/vmlinuz-2.6.38-8-generic                  1
  26.368164062 = 28.312600576   initrd.img                                     2
  26.255187988 = 28.191293440   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  45 4c 5f 4c 4f 57 20 20  20 20 20 20 20 20 31 37  |EL_LOW        17|
00000010  31 30 34 0d 0a 23 64 65  66 69 6e 65 20 49 44 43  |104..#define IDC|
00000020  5f 53 54 41 54 49 43 5f  48 49 47 48 4c 45 56 45  |_STATIC_HIGHLEVE|
00000030  4c 5f 48 49 47 48 20 20  20 20 20 20 20 31 37 31  |L_HIGH       171|
00000040  30 35 0d 0a 23 64 65 66  69 6e 65 20 49 44 43 5f  |05..#define IDC_|
00000050  53 54 41 54 49 43 5f 4c  4f 57 4c 45 56 45 4c 5f  |STATIC_LOWLEVEL_|
00000060  4c 4f 57 20 20 20 20 20  20 20 20 20 31 37 31 30  |LOW         1710|
00000070  36 0d 0a 23 64 65 66 69  6e 65 20 49 44 43 5f 53  |6..#define IDC_S|
00000080  54 41 54 49 43 5f 4c 4f  57 4c 45 56 45 4c 5f 48  |TATIC_LOWLEVEL_H|
00000090  49 47 48 20 20 20 20 20  20 20 20 31 37 31 30 37  |IGH        17107|
000000a0  0d 0a 23 64 65 66 69 6e  65 20 49 44 43 5f 53 54  |..#define IDC_ST|
000000b0  41 54 49 43 5f 44 45 46  41 55 4c 54 5f 44 50 49  |ATIC_DEFAULT_DPI|
000000c0  5f 53 57 49 54 43 48 45  52 20 31 37 31 30 38 0d  |_SWITCHER 17108.|
000000d0  0a 23 64 65 66 69 6e 65  20 49 44 43 5f 53 54 41  |.#define IDC_STA|
000000e0  54 49 43 5f 55 4e 53 55  50 50 4f 52 54 45 44 20  |TIC_UNSUPPORTED |
000000f0  20 20 20 20 20 20 20 20  20 31 37 31 30 39 0d 0a  |         17109..|
00000100  23 64 65 66 69 6e 65 20  49 44 5f 55 4e 53 55 50  |#define ID_UNSUP|
00000110  50 4f 52 54 45 44 5f 44  4f 57 4e 4c 4f 41 44 20  |PORTED_DOWNLOAD |
00000120  20 20 20 20 20 20 20 20  31 37 31 31 30 0d 0a 0d  |        17110...|
00000130  0a 2f 2f 20 4e 65 78 74  20 64 65 66 61 75 6c 74  |.// Next default|
00000140  20 76 61 6c 75 65 73 20  66 6f 72 20 6e 65 77 20  | values for new |
00000150  6f 62 6a 65 63 74 73 0d  0a 2f 2f 20 0d 0a 23 69  |objects..// ..#i|
00000160  66 64 65 66 20 41 50 53  54 55 44 49 4f 5f 49 4e  |fdef APSTUDIO_IN|
00000170  56 4f 4b 45 44 0d 0a 23  69 66 6e 64 65 66 20 41  |VOKED..#ifndef A|
00000180  50 53 54 55 44 49 4f 5f  52 45 41 44 4f 4e 4c 59  |PSTUDIO_READONLY|
00000190  5f 53 59 4d 42 4f 4c 53  0d 0a 23 64 65 66 69 6e  |_SYMBOLS..#defin|
000001a0  65 20 5f 41 50 53 5f 4e  45 58 54 5f 52 45 53 4f  |e _APS_NEXT_RESO|
000001b0  55 52 43 45 5f 56 41 4c  55 45 20 20 20 20 00 fe  |URCE_VALUE    ..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 0f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by shrakmoose on 2011-07-08
Here is my boot.ini file:
```

timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```What part should i change?

---

### Post by YesWeCan on 2011-07-09
> **Tiraryoko said:**
> Hello, I seem to be having a similar problem. I had windows XP installed on one hard drive and then decided to install Ubuntu 11.04 on a second hard drive. Now my computer boots straight into Ubuntu with no choices of going into Windows XP. 
There is something odd going on here. You have no Grub boot code in either disk and yet it boots into Ubuntu somehow! Are you sure you are booting into the Ubuntu on sdb? Also, your XP partition looks a little odd as no boot.ini is listed.

Well, Since you have a dedicated disk for Ubuntu you ought to have the Grub boot code in its MBR, and then tell your bios to boot this disk first.
Either
1) after booting Ubuntu on sdb run
[COLOR=Navy]sudo update-grub
sudo grub-install /dev/sdb[/COLOR]
or 2) after booting Ubuntu 11.04 from live CD/USB
[COLOR=Navy]sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb[/COLOR]
after booting Ubuntu on sdb run [COLOR=Navy]sudo update-grub[/COLOR]

Then tell your bios to boot sdb first. This should get you a boot menu with XP on it. I am not convinced that XP will boot, tho. You may have to run an XP disk and repair your XP installation.

I am very curious as to how it currently boots Ubuntu at all. :-k

---

### Post by YesWeCan on 2011-07-09
> **shrakmoose said:**
> Here is my boot.ini file:
```

timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```What part should i change?
I don't know. That looks fine as it is.
You may have to run an XP CD and do a repair. You might try deleting c:\ubuntu (if that's where the Wubi ubuntu folder is located) and see if that changes anything, but I'm clutching at straws.

---

### Post by charliewhizbeez on 2011-07-09
> **shrakmoose said:**
> I did the one where you can just use a slider to do the partitioning and the Ubuntu installer did the rest.

First of all, for future reference, I think it is always best to shrink it within windows (in fact I screwed up my entire computer doing it the other way :))

Windows is like a spoiled child that way.  Everything must be done it's way.  

But I also dual boot w/ windows :)

However, to fix it you could always to an update grub.

```
sudo apt-get upgrade grub
```

Best of luck to you!

---

