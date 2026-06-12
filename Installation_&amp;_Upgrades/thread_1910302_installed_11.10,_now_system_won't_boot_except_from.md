---
title: "installed 11.10, now system won't boot except from live CD"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by over_my_head on 2012-01-16
short version: I have 11.10 installed on my hp pavilion laptop. yesterday, i tried to shut it down from the drop down menu in the upper left corner of the screen. nothing happened. I then shut it down by pressing the actual power button on the laptop. now when i try to boot i get a flashing black screen with the following:

*stopping save kernel messages     [OK]
*starting bluetooth                [OK]
*saned disabled; edit/etc/default/saned   [OK]
*checking battery state.....        [OK]

stopping system v level compatibility


and then it just hangs there with the screen flashing. i can still boot from the live CD, and i tried running the grub repair tool from this thread: [http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub+repair](http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub+repair) but it didn't fix the problem.
although now i can at least get to a command line when i boot from the harddrive but i still can't boot into the installed operating system.

  


more info: (i'm sorry, i'm not that knowledgeable about computers so I sincerely apologize if this is not enough info/too much info/the wrong info)

 I had been running linux 8.10 for a long time, finally decided to upgrade to 11.10. I initially installed 11.10 alongside 8.10 and was dual-booting while i determined that i really wanted to switch to 11.10.
eventually i used the live CD to install 11.10 as the only operating system. I told the system to overwrite the entire harddrive and everything seemed to be working fine. 

the last couple days, i couldn't get the system to shut down from the drop down menu in the upper left corner of the desktop. eventually i just used the power button on the lap top to shut it down. now this. 


help will be greatly appreciated!

---

### Post by over_my_head on 2012-01-17
while booting from the CD i can mount my harddrive but i can't access my files - i'm guessing because i have a username and password set for that. 
if someone knows a way to access my files so that i can back them up to my external hard drive, that would be awesome too!

-----------------------------------
EDITED TO ADD: i realized that i'm not entirely sure what is meant by "live CD" - the CD i'm using to boot from right now is just the CD that I used to install 11.10 after downloading it. sorry if that caused any confusion.
------------------------------------------------


OK, a little more info about the boot issues:

i ran the boot_info_script from a terminal (i booted from CD to get access to the internet etc.)

the terminal gave me this:

```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/boot_info_script060/".

```


the .txt file is as follows:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   484,222,975   484,220,928  83 Linux
/dev/sda2         484,225,022   488,396,799     4,171,778   5 Extended
/dev/sda5         484,225,024   488,396,799     4,171,776  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        82d2fd5f-5671-4fbd-b856-df9ad6a316a3   ext4       
/dev/sda5        cfa11dda-6f8a-4b0b-910f-1ebf2f560240   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/82d2fd5f-5671-4fbd-b856-df9ad6a316a3 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=82d2fd5f-5671-4fbd-b856-df9ad6a316a3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=82d2fd5f-5671-4fbd-b856-df9ad6a316a3 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=82d2fd5f-5671-4fbd-b856-df9ad6a316a3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=82d2fd5f-5671-4fbd-b856-df9ad6a316a3 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82d2fd5f-5671-4fbd-b856-df9ad6a316a3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=82d2fd5f-5671-4fbd-b856-df9ad6a316a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cfa11dda-6f8a-4b0b-910f-1ebf2f560240 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  9a a9 aa a8 ba aa ba a8  aa 9a aa a8 bb a9 aa a8  |................|
00000010  aa a9 aa 98 aa a9 aa 98  aa a9 aa a8 aa a9 aa a8  |................|
00000020  9a a9 9a a8 ba a9 aa a8  a9 a9 aa a8 aa 99 ab b8  |................|
00000030  ab a9 ba b8 aa a9 aa a8  aa b9 aa b8 ab a9 ba a8  |................|
00000040  aa a9 aa 9b d9 bb bc c0  00 00 90 dd 00 0d 00 00  |................|
00000050  00 00 00 b6 ad 00 00 d0  00 d0 b0 94 9a db dd 08  |................|
00000060  00 00 d0 75 97 b8 9b b8  bc bb 8c 77 98 aa cb ab  |...u.......w....|
00000070  bd b0 a0 67 98 aa bc ab  ad bb bd 76 99 bb cc bd  |...g.......v....|
00000080  b0 0b b0 86 99 ba ad dc  0d 00 d0 87 a9 aa cb bb  |................|
00000090  00 dc d0 97 aa ab dd dd  cd d0 d0 87 aa d0 d0 dc  |................|
000000a0  d0 dd c0 77 ca bc dd d0  c0 d0 d0 88 c0 d0 00 d0  |...w............|
000000b0  00 00 d0 a9 00 00 00 c0  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 31 21 82 64 99  5c 26 28 a7 bc 34 3b e5  |...1!.d.\&(..4;.|
000000d0  84 36 dd c1 d4 1a 05 72  b9 41 65 52 f4 ef d6 4c  |.6.....r.AeR...L|
000000e0  79 4c b9 a6 5a 88 27 ac  5c d1 c4 84 91 b5 25 8a  |yL..Z.'.\.....%.|
000000f0  d5 09 2f ae d5 84 08 9e  a0 95 ea 68 4a 6b 92 97  |../........hJk..|
00000100  ee b5 48 c1 46 57 28 98  18 3f 96 5d 26 d7 22 05  |..H.FW(..?.]&.".|
00000110  46 2d d2 74 41 f6 95 88  52 17 5d d2 82 7f 0f 5e  |F-.tA...R.]....^|
00000120  2b 74 01 ac 5a 72 01 a1  d7 da cf b7 57 75 68 24  |+t..Zr......Wuh$|
00000130  78 bb cc 8e 73 27 89 f8  0b 43 14 82 c6 e4 61 5d  |x...s'...C....a]|
00000140  e2 57 e2 83 45 26 0f f5  c1 12 d5 3d 4b 17 27 d1  |.W..E&.....=K.'.|
00000150  54 76 de 86 f7 2e 94 51  30 24 04 bd 2b 52 e9 66  |Tv.....Q0$..+R.f|
00000160  85 68 60 4c e6 b5 b3 30  e1 d5 5c 76 1b e8 bf b0  |.h`L...0..\v....|
00000170  42 0d ed b3 f4 5f b9 f7  99 ae 10 50 2d 5c 26 43  |B...._.....P-\&C|
00000180  42 5d 3a 26 17 73 4d 82  55 5c 8b 52 ad 46 94 c9  |B]:&.sM.U\.R.F..|
00000190  f4 22 63 d2 49 05 9f 93  14 24 9d 02 6b 1a 6e f4  |."c.I....$..k.n.|
000001a0  e4 02 7c 83 09 09 76 6e  2c bb ab 4c 29 f3 8d 6e  |..|...vn,..L)..n|
000001b0  5e 38 29 53 7c 58 83 da  7c d2 ca 13 17 5e 00 fe  |^8)S|X..|....^..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by BC59 on 2012-01-17
> while booting from the CD i can mount my harddrive but i can't access my files - i'm guessing because i have a username and password set for that. 
if someone knows a way to access my files so that i can back them up to my external hard drive, that would be awesome too!

-----------------------------------
EDITED TO ADD: i realized that i'm not entirely sure what is meant by "live CD" - the CD i'm using to boot from right now is just the CD that I used to install 11.10 after downloading it. sorry if that caused any confusion.

Yes it's a live CD.

Boot from it and if you have problem to backup your files run
```
gksu nautilus
```
and try accessing your files through root nautilus.

---

### Post by over_my_head on 2012-01-17
OK, i ran the code you gave me 

I can see all my files! yay! but i still can't access all of them because i don't have "permission" - how do i give it my password?


sorry if i'm missing something obvious here, i'm still not that adept at command line/terminal type stuff. thanks for helping!

---

### Post by BC59 on 2012-01-17
If you are in Live Cd with gksu nautilus, just give your normal password.

---

### Post by over_my_head on 2012-01-17
the thing is, it doesn't seem to be asking for my password. i click on the folder i want to access and it gives me an message saying i don't have the permission necessary to view the folder.
 
i don't see anywhere to enter a password. what am i doing wrong?

---

### Post by BC59 on 2012-01-17
Normally with gksu nautilus you should be able to have ownership of your files.

---

### Post by over_my_head on 2012-01-17
AHA! figured it out... i was just being dense. sorry about that!

i can open the files - still won't let me copy them directly to my external hard drive for some reason...

---

### Post by BlinkinCat on 2012-01-17
You could mark as "solved" with the aid of the thread tools at top of page - :)

Edit - oops, too soon, thought was resolved, sorry about that.

---

### Post by BC59 on 2012-01-17
Try to copy them to another place of your hard drive and then to the external.

---

### Post by BlinkinCat on 2012-01-17
I apologize for jumping in too soon - :(

---

### Post by over_my_head on 2012-01-17
awesome. that is exactly what i needed. once i back-up everything i think i'm going to just re-install the operating system unless someone comes up with a solution for my booting issue in the next few days. 

but thank you SO MUCH for helping me get to my files!!

---

### Post by BC59 on 2012-01-17
To fix the system problem try running this FROM A LIVE CD ONLY:

```
sudo fsck /dev/sda
```

---

### Post by over_my_head on 2012-01-17
Ok, i ran it.... i got the following output:

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```

i'm guesing that means it didn't work???

---

### Post by over_my_head on 2012-01-17
> **BlinkinCat said:**
> I apologize for jumping in too soon - :(

no worries.

hopefully it will be solved soon. :-)

---

### Post by over_my_head on 2012-01-17
i just tried rebooting... i'm still getting the flashing black screen. although i did notice this time that it says something about 
"pipe broken"

i have no idea what that means but hopefully someone else does!

---

### Post by BC59 on 2012-01-17
When you run the command I posted, your hard drive was mounted. Try another time to boot from a Live CD and run the command.

---

### Post by over_my_head on 2012-01-17
i rebooted from the CD and tried running the command again - still getting the same message in the terminal.
:-(

edited to add: when i look at the harddrive with Disk Utility, there's three partitions on my hard drive. (possibly left over from when I was dual booting? but i did eventually install from the CD and told it to overwrite everything....)
the main (248 GB) partition which it says is /dev/sda1 and then a 2GB extended partition /dev/sda2 and a 2GB swap partition /dev/sda5.

should i run the 
fsck /dev/sda command as fsck /dev/sda1 in order to access the information in the main partition?

---

### Post by BC59 on 2012-01-17
Exactly.
you have to run:
sudo fsck /dev/sda1
and then 
sudo fsck /dev/sda2

---

### Post by over_my_head on 2012-01-17
Ok,
i did that and tried rebooting - got the same problem.

here's the output i'm getting in the terminal when i run that code:

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 205146/15138816 files, 12103900/60527616 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

```

---

### Post by BC59 on 2012-01-17
I didn't notice that you have only one partition, it's the sda1.
In any case if you don't find something, a fresh installation is the best solution.

---

### Post by over_my_head on 2012-01-17
well, i didn't exactly solve the issue but i did get back to my old system!!

i was going to do a fresh install but when i looked at the install options one was "update 11.10 to 11.10" so i thought, what the heck, can't screw it up any more than it is. 
and what do you know? after it finished, i was able to access my old installation. at first the mouse wasn't showing up but i used the keyboard to navigate over and run update manager and after reboot i have my mouse back.

i do seem to have lost skype but i will just download it again. 
anyway, THANK YOU to BC59 for your help!
it was a huge relief to get my files backed up and i really appreciate your efforts (and patience!) in trying to get my system working again. 

thanks!!

---

### Post by BC59 on 2012-01-17
Glad to help you!

---

