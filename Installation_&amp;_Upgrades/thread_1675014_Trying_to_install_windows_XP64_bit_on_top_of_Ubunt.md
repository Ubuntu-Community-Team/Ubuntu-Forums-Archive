---
title: "Trying to install windows XP64 bit on top of Ubuntu."
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by RyanMcD86 on 2011-01-24
Hi. i just got done reading this post here
[http://ubuntuforums.org/showthread.php?t=350090](http://ubuntuforums.org/showthread.php?t=350090)

After attempting to install windows.. i get a message in the windows install saying...

"To install Windows on the partition you selected setup must write some startup files to the following disk: 
XXXXXX MB disk 0 at ID 1 on bus 0 on atapi [MBR]
However, this disk does not contain a windows compatible partition"

I went into the recovery console and did the FIXMBR, but windows still won't install. Any ideas on what i can do to install windows with out removing Ubuntu?

---

### Post by Bucky Ball on 2011-01-24
You need some free space or if you want to install Windows *inside* Ubuntu you will need to use something like Virtualbox. ;)

Windows will NOT natively recognise EXT file system (Linux partitions). That is why you're getting a message about "this disk does not contain a windows compatible partition..."

---

### Post by presence1960 on 2011-01-24
> **RyanMcD86 said:**
> Hi. i just got done reading this post here
[http://ubuntuforums.org/showthread.php?t=350090](http://ubuntuforums.org/showthread.php?t=350090)

After attempting to install windows.. i get a message in the windows install saying...

"To install Windows on the partition you selected setup must write some startup files to the following disk: 
XXXXXX MB disk 0 at ID 1 on bus 0 on atapi [MBR]
However, this disk does not contain a windows compatible partition"

I went into the recovery console and did the FIXMBR, but windows still won't install. Any ideas on what i can do to install windows with out removing Ubuntu?

Do you have multiple hard disks? If so, you need to go into BIOS and set the hard disk you are installing windows onto as first to boot in the hard disk boot order. Windows ALWAYS writes it's bootloader to MBR of first disk to boot. That is probably why you are getting that message/warning.

If you are not sure :

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

It may also be what buckyball says. I have seen the first part of that message in the scenario I explained.

---

### Post by RyanMcD86 on 2011-01-25
okay. thanks :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 38072672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,194,047   104,192,000  83 Linux
/dev/sda2         104,196,094   312,580,095   208,384,002   5 Extended
/dev/sda5         104,196,096   117,268,479    13,072,384  82 Linux swap / Solaris
/dev/sda6         117,270,528   214,926,777    97,656,250  83 Linux
/dev/sda7         214,930,863   312,545,519    97,614,657   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        24e55012-8bde-42cf-a0c3-7649c4b4a902   swap                                     
/dev/sda6        48617547-fd32-4da6-b84d-81ae2c14bd48   ext4                                     
/dev/sda7        80E0B76BE0B76656                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /usr/local               ext4       (rw,commit=0)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0
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
UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 /               ext4    errors=remount-ro 0       1
# /usr/local was on /dev/sda6 during installation
UUID=48617547-fd32-4da6-b84d-81ae2c14bd48 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=24e55012-8bde-42cf-a0c3-7649c4b4a902 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
  32.7GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  19.7GB: boot/initrd.img-2.6.35-24-generic
  19.5GB: boot/vmlinuz-2.6.35-22-generic
  19.5GB: boot/vmlinuz-2.6.35-24-generic
  19.7GB: initrd.img
    .9GB: initrd.img.old
  19.5GB: vmlinuz
  19.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6c 48 74 20 c0 b4 23 3d  0f 0c 7a 01 10 13 16 81  |lHt ..#=..z.....|
00000010  43 40 c4 04 02 a6 14 86  3a 8c 61 02 e3 1d 17 a0  |C@......:.a.....|
00000020  ca c8 c9 08 eb 44 3e 10  66 60 e8 c9 ee 44 e5 2d  |.....D>.f`...D.-|
00000030  8c 19 00 08 21 1a 49 fe  5f 05 a0 30 01 60 42 c7  |....!.I._..0.`B.|
00000040  81 43 7f 9a 0a df 80 1a  9b ac c1 12 25 c5 93 b9  |.C..........%...|
00000050  0a 58 f7 36 58 15 ac b3  38 fe e0 47 01 ad 3a 6e  |.X.6X...8..G..:n|
00000060  d3 2e 6e b1 f8 0a 86 ab  ef 01 c3 d4 30 d5 e7 f6  |..n.........0...|
00000070  35 6a 08 8b 3d 12 ba 7b  d5 ec d8 c2 c1 ad 07 80  |5j..=..{........|
00000080  b2 08 93 04 49 48 50 24  64 98 d9 43 91 06 d4 49  |....IHP$d..C...I|
00000090  02 87 88 82 8b 13 9c 40  81 00 94 a2 e8 42 f0 51  |.......@.....B.Q|
000000a0  a4 43 b3 ef 4c 81 87 21  62 31 6b 0e 12 76 d8 f8  |.C..L..!b1k..v..|
000000b0  83 ea 25 3d 9d d5 fb 77  5e ef d7 8e f9 e5 ee 7f  |..%=...w^.......|
000000c0  2f bd 7f ff f9 fe 5a 9b  aa 2d 7e f9 c8 5d c6 17  |/.....Z..-~..]..|
000000d0  72 5c 1b 72 f7 06 e0 9b  6f a8 4d f5 34 2e 11 16  |r\.r....o.M.4...|
000000e0  4c 20 37 33 c0 08 cf 41  d3 46 09 0c 6e 10 30 fa  |L 73...A.F..n.0.|
000000f0  0c cb 03 63 30 da 0c 46  2d 1c 0a 98 9d 5e 66 b2  |...c0..F-....^f.|
00000100  a9 9d 86 46 93 27 1b 04  04 61 f1 11 91 45 67 08  |...F.'...a...Eg.|
00000110  62 10 18 42 86 1e b1 86  5c 01 4c 68 19 16 b4 ca  |b..B....\.Lh....|
00000120  98 2d 31 a2 12 63 27 85  55 1d e1 e3 00 80 05 00  |.-1..c'.U.......|
00000130  dc c4 46 cc 49 00 c5 69  86 17 26 84 a5 ca b0 a0  |..F.I..i..&.....|
00000140  e1 10 68 08 1a 8e bf 0a  00 c5 16 7a 1e 2a bc b0  |..h........z.*..|
00000150  08 01 3f e5 4a da b8 20  e8 f5 f7 e9 ef 96 bc ce  |..?.J.. ........|
00000160  4a 76 ae e7 4a 6d 9d 43  53 b0 4c 52 cc a6 57 6e  |Jv..Jm.CS.LR..Wn|
00000170  68 52 21 d0 a8 7d 15 11  02 88 d7 64 e3 38 79 61  |hR!..}.....d.8ya|
00000180  46 91 13 25 a4 cc 9b 64  91 01 e5 09 49 20 51 a6  |F..%...d....I Q.|
00000190  31 25 99 04 28 c9 34 d0  c1 09 54 10 56 74 f4 28  |1%..(.4...T.Vt.(|
000001a0  87 2c d2 ce 23 05 05 21  5e cc 4a f0 c1 12 37 ee  |.,..#..!^.J...7.|
000001b0  87 d0 51 1a 2c d4 dd a9  ad 2c 0b a6 38 d6 00 42  |..Q.,....,..8..B|
000001c0  d3 ff 82 cc dc ff 02 00  00 00 00 78 c7 00 00 cc  |...........x....|
000001d0  dd ff 05 b0 ca ff 02 78  c7 00 ba 25 d2 05 00 00  |.......x...%....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by presence1960 on 2011-01-25
Are you trying to get rid of Ubuntu and have a windows machine or do you want to dual boot?

If you want to get rid of ubuntu you can boot the Ubuntu Live CD and choose try ubuntu. When the desktop loads go System > Administration > Gparted partition Editor. What you want to do is delete all partitions one by one. When delete one partition click Apply (green check mark) before deleting the next one.

Once they are all gone you have two choices: you can leave the entire disk as unallocated space or you can create an NTFS partition to install windows onto. Once you complete this boot the windows install media and install.

If you want to dual boot you post back.

---

### Post by Bluesan on 2011-01-25
A good set of instructions to follow for dual booting is here:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu)

---

### Post by kansasnoob on 2011-01-25
Somewhat guessing here, but looking at this:

```
Drive: sda ___________________ ____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,194,047   104,192,000  83 Linux
/dev/sda2         104,196,094   312,580,095   208,384,002   5 Extended
/dev/sda5         104,196,096   117,268,479    13,072,384  82 Linux swap / Solaris
/dev/sda6         117,270,528   214,926,777    97,656,250  83 Linux
[B][COLOR="Red"]/dev/sda7         214,930,863   312,545,519    97,614,657   7 HPFS/NTFS[/COLOR]
[/B]
```

Are you trying to install XP to sda7 (the NTFS partition)?

If so that won't work because it's a logical partition, you need to create room for a primary partition. (I then prefer leaving that space unallocated).

Look at these instructions I typed for someone else:

[http://ubuntuforums.org/showpost.php?p=10356856&postcount=3](http://ubuntuforums.org/showpost.php?p=10356856&postcount=3)

If you need more personalized/detailed help please post a screenshot of Gparted.

Just out of curiosity why the separate /usr/local:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ab6dd3aa-6800-4ef2-8177-93fb1e08a2c0 /               ext4    errors=remount-ro 0       1
**[COLOR="Red"]# /usr/local was on /dev/sda6 during installation[/COLOR]**
UUID=48617547-fd32-4da6-b84d-81ae2c14bd48 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=24e55012-8bde-42cf-a0c3-7649c4b4a902 none            swap    sw              0       0
```

I've just never seen that before :)

---

### Post by RyanMcD86 on 2011-01-25
oh... the extra partition was in case i wanted to install windows or to backup extra files.

---

### Post by kansasnoob on 2011-01-25
> **RyanMcD86 said:**
> oh... the extra partition was in case i wanted to install windows or to backup extra files.

Which partition? The one that's now /usr/local or the one that's now NTFS?

If you want help we need to know what you have now, what your intent was when you created that, and what your intent is now :D

My previous question about a separate /usr/local still stands. Why?

We're not mind readers.

---

### Post by adrinkrahene on 2011-01-25
It is as presence1960 has said with the partition table you have Linux is 1st
and windows has to write to that space. And that space can not be formated for Linux. 
Which is why windows is loaded on the disk 1st (other than virtual box).

_Notice the star under boot_
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,194,047   104,192,000  83 Linux


IF YOU FIND A WORK AROUND THIS PLEASE POST IT!

---

### Post by RyanMcD86 on 2011-01-25
oh.. i didn't try to partition the "/usr/local". instead i was trying to partition the boot which is "/dev/sda1" ext4 mount point "/"  as for why i added the extra partition. i just thought it would be good to have another partition that was unmounted. do you think its okay to have that one?

---

### Post by kansasnoob on 2011-01-26
I found your PM in my spam this morning:

> I was following your post on how to install windows with ubuntu. I got stuck when i tired to resize the partition. it wont let me.

says
"An error occurred while applying the operations
See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information."

do you know why I cant resize it?

Which partition were you trying to resize?

What did the "details" show?

As I said previously we really need to see a screenshot of Gparted to offer detailed help because it will show the actual partition layout including how much free space each partition has.

An alternative to a screenshot would be the output of the following two commands wrapped in code tags:

```
sudo parted -l
```

```
df -H
```

NOTE: That's a lower case L at the end of the first command, and intentionally a CAP H in the second.

BTW you can't just delete /usr/local, it's part of your Ubuntu install! I just wondered why you'd created a separate one.

---

