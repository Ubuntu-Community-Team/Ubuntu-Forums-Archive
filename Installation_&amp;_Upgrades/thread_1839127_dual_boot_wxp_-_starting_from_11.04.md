---
title: "dual boot w/xp - starting from 11.04"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by bman2004 on 2011-09-05
Hi All.
I am currently running 11.04 and would like a dual boot option with xp. 

My hard drive info is as follows:
sda1 /              10gb ext4
sda2 /home     46gb ext4
sda3 swap      24gb 

I don't mind giving up 20gb from my /home directory for the xp install. 
Can someone walk me through what needs to be done? 
Thanks.

---

### Post by YannBuntu on 2011-09-05
Hello

here is what I would do:
1) Backup the /home on an external drive, by security
2) Boot on a Ubuntu CD , choose "Try Ubuntu", run Gparted, and reduce the SWAP partition to 4Go (if you have 4 Go RAM, basically SWAP must be same size as your RAM)
3) Install XP in the free space, reboot and check that XP works
4) Reinstall GRUB menu, e.g. via Boot-Repair

---

### Post by bman2004 on 2011-09-06
I have a new problem:

I wiped the drive. Created a single, new partition for XP, then used the Ubuntu Live CD to resize that partition to allow for Ubuntu to be installed. 

During the process of shrinking the NTFS partition (XP), I accidently selected mount point /dos. When the computer boots I am not given a screen to select which operating system and it defaults to Ubuntu.

Can you help me figure out how to fix the dual boot?
Thanks.

---

### Post by YannBuntu on 2011-09-06
Please can you indicate your Boot-Info URL (by following this little tutorial : [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980) )

it will help us understand the situation.

---

### Post by bman2004 on 2011-09-06
Boot Repair is stuck on 'Enabling RAID'

I opened up terminal from my Ubuntu install, not the Live CD on boot. Is that okay?

---

### Post by bman2004 on 2011-09-06
I tried it again and here are the [results]("http://paste.ubuntu.com/683618/").

---

### Post by YannBuntu on 2011-09-06
Thanks.

Your XP is correctly recognized by os-prober, so reinstalling GRUB may detect it. For this, the easiest way is to click the "Recommended repair" button of Boot-Repair.

The /dos mounting point is not a problem, we will correct it later (via Disk-manager).

---

### Post by bman2004 on 2011-09-06
Clicking the "Recommended repair" button of Boot-Repair didn't seem to fix it.
What would you recommend next?

---

### Post by jaj540 on 2011-09-06
try updating ur Grub by 


```
sudo update-grub2
```


if it doesnt work
Just try reinstalling grub..this may fix the problem..
 boot from ubuntu disk
 mount your ubuntu partition
 Verify if your partition is correctby typing the following in terminal


```
mount | tail -1
```


You should see output similar to this:


```
/dev/sda2 on /media/0d104aff-ec8c-44c8-b811-92b993823444 type ext4 (rw,nosuid,nodev,uhelper=devkit)


```
Note the designation for the disk /dev/sda which you will be using later, and the directory in /media.

now type
```
sudo grub-install --boot-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
```

where the boot-directory must be that u obtained from mount | tail -1




I dont know whether this will help u or not...i am a newbie here.. But i got it working when done this for a similar problem

---

### Post by bman2004 on 2011-09-06
The last recommendation didn't seem to work.

---

### Post by Hakunka-Matata on 2011-09-06
```

sudo update-grub2
```# try this

```
sudo update-grub
```later try ```
sudo update-
``` 
[LIST]

[/LIST]# then hit Tab key **TWICE**.  you'll see all the possible options listed

---

### Post by bman2004 on 2011-09-06
Bigger problem now:
In between posts, I did a little experimenting and now I can't seem to boot into my Ubuntu install. 

In the 'Boot Repair' utility under the Main Options tab, I selected 'restore MBR', then under the MBR options, I selected Windows XP for 'Partition booted by the MBR.

Now, in addition to not being able to select between my two OS's, the default OS is now XP.

Can anyone help me?

---

### Post by YesWeCan on 2011-09-06
It'll be sorted in no time. Better know exactly what's on your drive first so as to use the best means to fix it.
Please boot live CD, download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt file inside code tags (highlight text and click # above).
:)

---

### Post by bman2004 on 2011-09-06
I'm also dealing with another problem:
on boot up its stalling for 20 seconds or so on 'Initializing USB Controllers'. My keyboard then freezes up for a couple minutes before I can use it in the OS

In response to the last recommendation. Here are the results.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    21,005,131    21,005,069   7 NTFS / exFAT / HPFS
/dev/sda2          21,006,334   156,280,319   135,273,986   f W95 Extended (LBA)
/dev/sda5          40,965,813   156,280,319   115,314,507   e W95 FAT16 (LBA)
/dev/sda6          21,006,336    38,082,559    17,076,224  83 Linux
/dev/sda7          38,084,608    40,964,095     2,879,488  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 a2ae97af-967c-4e7a-93e0-b45e4e0cf335   swap       
/dev/sda1        9CB0F872B0F853EC                       ntfs       
/dev/sda6        b6f9bb19-cd7a-4568-a1cc-2512e48684f6   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b6f9bb19-cd7a-4568-a1cc-2512e48684f6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b6f9bb19-cd7a-4568-a1cc-2512e48684f6 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root b6f9bb19-cd7a-4568-a1cc-2512e48684f6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CB0F872B0F853EC
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b6f9bb19-cd7a-4568-a1cc-2512e48684f6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=18f4a368-9bcf-42a0-8331-d282d3b771e9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.420730591 = 15.484141568   boot/grub/core.img                             1
  16.989574432 = 18.242416640   boot/grub/grub.cfg                             1
  12.586914062 = 13.515096064   boot/initrd.img-2.6.38-8-generic               3
  14.461975098 = 15.528427520   boot/vmlinuz-2.6.38-8-generic                  1
  12.586914062 = 13.515096064   initrd.img                                     3
  14.461975098 = 15.528427520   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  fd 78 e4 89 37 e8 95 3d  ec f5 02 b9 06 14 58 c2  |.x..7..=......X.|
00000010  55 39 89 18 51 4c 38 d1  b1 84 2d 3d 3c 67 5c bf  |U9..QL8...-=<g\.|
00000020  43 cd 26 57 13 5d ea da  e4 d5 66 ed 4c 34 67 f6  |C.&W.]....f.L4g.|
00000030  fb 52 c4 5b 04 e2 17 47  d3 1a 88 ea c2 12 d4 51  |.R.[...G.......Q|
00000040  b7 1d 80 ab 38 a3 60 80  3a 2f 98 df 11 6b 77 67  |....8.`.:/...kwg|
00000050  d4 ee 7c cb f1 28 1f 0f  9b 0e 7d bd a5 4a b8 8d  |..|..(....}..J..|
00000060  cb 4d 2a 3c 1c 43 47 99  b8 42 ca a1 99 11 c3 6b  |.M*<.CG..B.....k|
00000070  96 4b d2 53 be 5a 9c d8  a9 30 9d b9 8d 1d ca 1c  |.K.S.Z...0......|
00000080  77 8a 85 db 89 dc 90 95  8d 53 9e 26 1f 16 2d 0f  |w........S.&..-.|
00000090  27 15 70 1e 02 35 2e 3b  6d 6b 99 96 72 b4 6a 0c  |'.p..5.;mk..r.j.|
000000a0  04 30 35 ba d6 c5 47 c8  ec c6 24 9d 70 98 46 67  |.05...G...$.p.Fg|
000000b0  b1 29 37 cd 99 d2 d3 7a  78 b0 73 a2 c9 76 f2 45  |.)7....zx.s..v.E|
000000c0  04 b2 87 6e 54 a3 d0 da  ff e8 d0 a1 77 ad 40 c1  |...nT.......w.@.|
000000d0  c4 0c 34 fa 40 1c 1e cd  fd 84 6a ce 93 26 cf ff  |..4.@.....j..&..|
000000e0  f0 a6 00 8b 09 9d ac 3e  d7 4c 64 61 02 30 c6 79  |.......>.Lda.0.y|
000000f0  b7 6c ba 55 f4 5c 84 54  dd 0a bd a1 8a 76 0f 06  |.l.U.\.T.....v..|
00000100  95 49 b1 a5 f8 ef 0f dc  bd e3 c7 89 74 94 90 d0  |.I..........t...|
00000110  6c ed cf 24 90 39 9a a8  ff d5 a3 70 bd ef c0 a5  |l..$.9.....p....|
00000120  b4 51 86 9e 83 d8 a2 b1  4e ff 6d 48 b1 6a e2 69  |.Q......N.mH.j.i|
00000130  ce ea ee 07 99 d2 cc e9  4b 02 30 8b 50 f8 4f 3b  |........K.0.P.O;|
00000140  e5 12 07 09 81 2e 8e 32  79 ff 5a c1 9b 45 0d 92  |.......2y.Z..E..|
00000150  1c 3c ab 8d 17 7b a1 07  99 f9 c7 44 a2 3b a0 4d  |.<...{.....D.;.M|
00000160  08 1b d2 e8 20 c8 27 2e  31 6e 5e 03 5f 4b 17 f7  |.... .'.1n^._K..|
00000170  e5 1a 4c 84 5e 3f 47 14  be 63 40 26 d5 19 00 c9  |..L.^?G..c@&....|
00000180  04 94 f4 28 64 93 d8 e9  72 c6 c1 22 1c 48 0a a4  |...(d...r..".H..|
00000190  87 97 c8 8e e7 47 a9 76  e5 d3 f5 48 df 48 7c 0c  |.....G.v...H.H|.|
000001a0  ff 2b a5 a3 2c c7 9f 8a  41 c6 de 21 44 81 03 3a  |.+..,...A..!D..:|
000001b0  ad 0d 8a 66 d0 3a 56 fa  f8 25 b8 97 1a 6b 00 01  |...f.:V..%...k..|
000001c0  c1 ff 0e fe ff ff b7 8e  30 01 4b 8f df 06 00 fe  |........0.K.....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 90 04 01 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by YesWeCan on 2011-09-06
The encrypted swap is unusual.
What happens when you boot?
do you get a grub menu?
do you get a grub> prompt or a rescue> prompt?
What works and what doesnt work?

---

### Post by bman2004 on 2011-09-06
I fixed the 'Initializing USB Controller' issue.

On booting the screen goes black and maybe 30-45 seconds later Ubuntu login screen comes up.
I don't get any menu allowing me to select the OS (XP or Ubuntu) it just goes straight to Ubuntu.

---

### Post by YesWeCan on 2011-09-06
Curious black screen delay.
For good measure, once it has booted Ubuntu do:
sudo update-grub
sudo grub-install /dev/sda

when it does the update you shoukd see XP listed.

---

### Post by bman2004 on 2011-09-06
No difference. It seems as though in the time between the BIOS reading and booting of Ubuntu the signal to the screen is dead. It says 'No Signal...."

Am I supposed to press something get the OS dual boot menu to come up? Is this menu GRUB?

---

### Post by YesWeCan on 2011-09-06
I suspect the grub menu is there but you cant see it because of some display problem. So it waits 10 sconds and then defaults to booting Ubuntu. This is while the screen is black. This may account for the long time it takes to boot.

You might find that after the screen goes black and within 10 seconds, you can press the down arrow key 6 times or so then press enter and it might boot XP instead. Maybe.

What is your hardware?

---

### Post by bman2004 on 2011-09-06
AMD Athlon 64 x2 dual core 4200+
1.3gb DDR

---

### Post by bman2004 on 2011-09-06
No luck with the keyboard down scrolling.
Signing off for 8 hours or so.

---

### Post by bman2004 on 2011-09-07
SOLVED!

The GRUB menu was in fact there. I just needed to make it visible. All that was needed was to uncomment (remove the hash from) ```
[COLOR=Red]_**#**_[/COLOR]****GRUB_GFXMODE=640x480
``` in the grub configuration file: sudo gedit /etc/default/grub

The other startup problem I was having where it would stall on 'Initializing USB Controllers', I solved by removing the cable from a a trouble USB device (my printer). Its an old cable, perhaps it needs a spray of DeoxIT, or complete replacement.

I also encountered difficulties getting my USB keyboard to work in the GRUB menu, I solved this by enabling 'Legacy USB Devices' in the menu dedicated to USB support in my BIOS.

Thanks everyone for your recommendations.

---

### Post by YesWeCan on 2011-09-07
Good.
Dont forget to mark this solved in [COLOR="Red"]Thread Tools.[/COLOR]

---

