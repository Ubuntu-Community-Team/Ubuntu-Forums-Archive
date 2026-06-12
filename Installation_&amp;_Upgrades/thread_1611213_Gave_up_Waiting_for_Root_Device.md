---
title: "Gave up Waiting for Root Device?"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Asylum- on 2010-11-01
I Recently installed Ubuntu 10.10 Net book version on my Net book ( Duh) Its a Toshiba Nb205 with a 160 gb Hdd. 

It booted fine off the flash drive, I tested the sound ( No other linux system works with my speakers, but thats another thread.... )

I hit install Ubuntu.
Go through all the steps everything works fine! 
I wipe my whole hard drive for ubuntu,  Nothing else on it anyways.


I shut down the machine, remove the flash drive, and I reboot the machine.

I get the boot loader screen, select Ubuntu 10.10

It black screens with a _ flashing in the upper left screen, and then i get a message on the screen:

" Gave up waiting for root device. Common problems:
- boot args (Cal /proc/cmdline)
- check rootdelay= ( Did the system wait long enough?)
blah.
blah..

It then says ALERT! /dev/disk/by-uuid/8c8e4fa4-55ed-4c12-9fe2-a0b9cd7c78 does not exsist (What????)

Then drops to shell and i don't know where to go from there..

I'm basically new to linux, I've been dabbling for about 2 months.

---

### Post by drs305 on 2010-11-01
As a quick first step, at the grub prompt with the first entry highlighted, press "e". That should display the menuentry and allow you to edit it.

Cursor to the start of the "search" line. Hold down the DEL key and remove the entire line.

Next move to the linux line. It will look something like this:
> linux    /vmlinuz **root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed** ro quiet splash

Change the "root=UUID=<uuid>" part of the line so it looks like below. You will need to know the Ubuntu partition. If Ubuntu is the only thing on the drive, it should be /dev/sda1. If it's not change it.
> 
linux	/vmlinuz **root=/dev/sda1** ro quiet splash

Make the change, then press CTRL-x and see if it boots.

If you still have problems, it's possible the bootloader is still looking for the flash drive for boot information.  Please boot to the LiveCD and run the boot info script found in the link below. Post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Asylum- on 2010-11-01
Removed the First line as stated

Next line after linux it has /boot/vmlinuz-2.6-35-22-generic

Does that need to remain? 

Tried it with and without.
> Boot a command list

error: hd1, msdos1 cannot get C/H/S values
error: You need to load the kernel first

Press any key..

and then i get another screen with initrd  something or another on it.. Will try second suggestion Now..

---

### Post by drs305 on 2010-11-01
Right before you press CTRL-x you menu should look "something" like this. The values will be different and you may not have all the same lines, but that's ok.

> 
recordfail
insmod ext2
set root='(hd0,1)'
linux	/vmlinuz root=/dev/sda1 ro  quiet splash
initrd	/initrd.img


However, if you are getting CHS error messages, sda1 may not be your Ubuntu partition. If it doesn't work this time, it would probably be best just to run the boot info script so we aren't guessing.

---

### Post by Asylum- on 2010-11-01
Alright, Tried it as above, Errors...

Booting the Live USB now..

Heres the Results of the Boot Info Script

[PHP]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1002 MB, 1002438144 bytes
32 heads, 63 sectors/track, 971 cylinders, total 1957887 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            129     1,957,535     1,957,407   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6092-56D9                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        6230c607-6f86-4e62-b155-911db1ab94e0   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
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
    search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78 ro single 
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
    search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8c8e4fa4-55ed-4c12-9fe2-a0b9cd0c7c78 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6230c607-6f86-4e62-b155-911db1ab94e0 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
  90.3GB: boot/grub/grub.cfg
  47.9GB: boot/initrd.img-2.6.35-22-generic
 146.1GB: boot/vmlinuz-2.6.35-22-generic
  47.9GB: initrd.img
 146.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 11  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 81 00 00 00  |........?.......|
00000020  1f de 1d 00 70 07 00 00  00 00 00 00 02 00 00 00  |....p...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d9 56 92 60 4e  4f 20 4e 41 4d 45 20 20  |..).V.`NO NAME  |
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
00000100  7d 00 66 b8 f0 dd 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

Unknown BootLoader  on sdb2

00000000  77 7d 5f 15 3c 84 7b 1e  16 2b 0c fb 6b f9 67 4c  |w}_.<.{..+..k.gL|
00000010  68 2e 0b 2b 79 3b 4f e3  43 25 1b 19 ad 06 ca 72  |h..+y;O.C%.....r|
00000020  c9 b5 d7 32 ca e1 8a 01  a4 bc ef 45 7e b5 c7 e8  |...2.......E~...|
00000030  c6 68 f5 ad 70 50 51 d9  4a b0 1a 88 a2 03 08 b0  |.h..pPQ.J.......|
00000040  cf 2d e0 81 c2 4f 60 cd  43 18 ed d1 82 bb 8d 29  |.-...O`.C......)|
00000050  10 98 10 67 dc 8a 48 70  d4 e9 c5 cd 7b 66 b8 56  |...g..Hp....{f.V|
00000060  47 4e d9 6f f1 fc cd 9b  1e 4f 4a ba d9 c5 4d f6  |GN.o.....OJ...M.|
00000070  32 e1 9c b5 f1 c1 96 77  4e 0e ad 77 75 47 9c d7  |2......wN..wuG..|
00000080  5c 84 eb 68 ed 9b 8c 68  8a 0f 8a 36 a0 1e 17 ba  |\..h...h...6....|
00000090  33 e1 6a 66 13 06 ac fa  04 35 0c 06 b8 f4 67 53  |3.jf.....5....gS|
000000a0  7c d0 f6 40 60 07 dd 4d  67 34 54 20 20 39 8a 6d  ||..@`..Mg4T  9.m|
000000b0  0c d2 77 96 7a 2a ba 45  88 87 2a c5 14 d1 8f 05  |..w.z*.E..*.....|
000000c0  c0 6c 28 97 ff ea 16 a9  99 a5 b5 6f 19 a2 6a 3b  |.l(........o..j;|
000000d0  45 3b 88 c9 94 5a ee cd  79 42 c7 73 3c ab 73 92  |E;...Z..yB.s<.s.|
000000e0  ac a3 1b f4 16 14 db 8a  7c ec cb a2 d7 1e 94 10  |........|.......|
000000f0  2f 92 a8 be 28 5b a3 e0  82 05 88 a0 e1 31 58 0c  |/...([.......1X.|
00000100  12 4a 3e 34 9d 1a 69 ff  c9 9f fb 2d e8 22 ed be  |.J>4..i....-."..|
00000110  50 ba 8f be 60 d4 ff f9  92 bd 81 a8 b9 73 87 3f  |P...`........s.?|
00000120  11 e1 4a 9d 6e 73 7e 98  12 6f 87 9a 37 2e aa d7  |..J.ns~..o..7...|
00000130  79 7d 47 6f f6 7b 58 1a  e9 80 5c c8 7c c2 24 60  |y}Go.{X...\.|.$`|
00000140  3c 79 68 42 4e 03 b1 62  b3 d1 3d 18 1b 58 ac 9b  |<yhBN..b..=..X..|
00000150  9d c3 9d 78 e3 3a ac b6  02 cc 37 cb 6a 10 69 68  |...x.:....7.j.ih|
00000160  b4 0e cd 8e 4c 0d 06 70  4b cf 03 60 a2 57 93 cf  |....L..pK..`.W..|
00000170  e8 2e d4 c9 0b 54 e7 b3  12 ab 51 ed b6 a8 fe 92  |.....T....Q.....|
00000180  e8 f1 8f dc 5f 74 6c 72  27 30 e6 ca 5a 1e 8b c5  |...._tlr'0..Z...|
00000190  e1 61 51 99 25 06 78 1f  6f 14 99 d0 85 46 96 59  |.aQ.%.x.o....F.Y|
000001a0  26 90 8c 65 27 78 92 f2  b3 75 99 55 30 6e 3c 11  |&..e'x...u.U0n<.|
000001b0  f0 65 58 47 ce 2d 1d 3c  94 e9 e4 b3 7a 50 00 fe  |.eXG.-.<....zP..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[/PHP]

---

### Post by drs305 on 2010-11-01
The results.txt info looks normal.

From the LiveCD, try running the following to rewrite to the sdb MBR. Do not put the partition number in the second command:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
This should rewrite the sdb MBR and point Grub to the Grub files in sdb1.

Reboot and make sure the BIOS points to the hard drive and not your flash drive. 

If this fails to fix the problem, try booting the CD again and purge/reinstall grub2 via the chroot procedure outlined in this thread:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
The procedure is fairly straightforward, just make sure you have an Internet connection before purging the grub packages.

---

### Post by Asylum- on 2010-11-01
Edit: Same error.. Thought it was gonna work, and it froze, rebooted and got the Alert error again... FML.

---

### Post by biggy007 on 2010-11-02
I have exactly the same problem using the same netbook, I am a complete novice and hope you guys can find a solution...
 
ps sorry for jumping in on your thread but it is exactly the same as mine .

---

### Post by drs305 on 2010-11-02
> **Asylum- said:**
> Edit: Same error.. Thought it was gonna work, and it froze, rebooted and got the Alert error again... FML.

Does the system boot if you keep the USB drive connected at boot?

---

### Post by Asylum- on 2010-11-02
No, i'm 99% Sure i get the same error, I am away from the Netbook atm, at School and thought i would get on to check it.

---

### Post by drs305 on 2010-11-02
This is an easy trial. I don't know what could be causing it, but if the partition isn't being found quickly enough the error message could be triggered. Try adding a delay before the kernel accesses the partition by adding "rootdelay=90" to the linux line.

At boot, highlight the first option, press "e", cursor to the end of the "linux" line and add **rootdelay=90** after "quiet splash". In fact, you could even remove "quiet splash" and just replace it with the rootdelay entry.

There was also an old bug which caused the same error message. You could go through this thread:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix")

---

### Post by MartijnB on 2010-11-02
I have the exact same problem with my Toshiba nb200-10z and leaving the usb drive in does not work:(. I hope someone will be able to help us.

---

### Post by MartijnB on 2010-11-02
the rootdelay didn't work but the next time I pushed 'e' the rootdelay=90 was gone:S. I don't know wheither thats always the case(im very new the linux).

---

### Post by drs305 on 2010-11-02
> **MartijnB said:**
> the rootdelay didn't work but the next time I pushed 'e' the rootdelay=90 was gone:S. I don't know wheither thats always the case(im very new the linux).

Thanks for checking anyway. The advantage & disadvantage of manually editing Grub menu during boot is that the change is not persistent. It will be gone the next time you boot (as you found out).

If a change works, once you boot you have to edit the correct Grub2 file, save it and run "sudo update-grub" to make the change stick. Kernel option changes to the "linux" line are made to the /etc/default/grub file, normally to the *GRUB_CMDLINE_LINUX_DEFAULT=* line.

---

### Post by biggy007 on 2010-11-02
So where does that leave us?
Is it a Toshiba netbook problem?

---

### Post by drs305 on 2010-11-02
> **biggy007 said:**
> So where does that leave us?
Is it a Toshiba netbook problem?

I'm not a netbook user so I don't know if it's a netbook issue or not. The OP, and I presume you other netbook users, are installing via USB so there's also the possibility that there is a problem with the Grub files being divided between the flash drive and the main system. 

Reinstalling or purging/reinstalling normally would clear the last issue but apparently didn't for the OP.

Another option would be to try installing the normal version of Ubuntu rather than the netbook version. I know some users prefer the normal version and it works fine on netbooks.

If you can get to the Grub2 menu, and can download and access ISO files, I wrote a guide on how to install Ubuntu by mounting an ISO and installing Ubuntu.Initially I wrote it with netbook users stuck at the grub rescue prompt, but anyone can use it from a grub command line.  Here is the link for that thread:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by Quackers on 2010-11-02
biggy007 and MartijnB, do you have other operating systems on your netbook or just Ubuntu?

---

### Post by MartijnB on 2010-11-02
I believe i have the normal ubuntu version installed(got it from a friend). and yes I still have win7 proffesional installed.

---

### Post by biggy007 on 2010-11-02
I only have ubuntu now.
netbook version

---

### Post by Asylum- on 2010-11-02
I had Linux Mint and Win7 Starter on mine for a long time, and it worked fine, Decided to try Ubuntu, and then started having this issue.

I was able to get the netbook started last night after i got off my main desktop to watch a movie with the first suggestion you did, I ran any and all updates i could once i got it booted, but then restarted it and got an error. Ill Install 10.10 regular now and see what errors i get. I've not had good luck with it after wiping the hard drive the first time...

---

### Post by jrace1 on 2010-11-04
I was having the same problem with my gateway netbook. I added the rootdelay=90 just like drs305 said and it booted just fine. My question is how do I make this permanent? I am somewhat familor with ubuntu but haven't had to dive this deep into it before. Thanks!

---

### Post by jrace1 on 2010-11-04
I went into the /etc/default/grub file but I don't understand where to add the "rootdelay=90" to help make this fix permanent.

---

### Post by jrace1 on 2010-11-04
Never mind figured it all out :)

---

### Post by Asylum- on 2010-11-04
Still having the issue with a fresh install of 10.10 Desktop.

Not sure. Download Mint 8 Right now.. Gonna see if that works.

---

### Post by Asylum- on 2010-11-05
[http://ubuntuforums.org/showthread.php?t=1397193&page=5](http://ubuntuforums.org/showthread.php?t=1397193&page=5)
 
Check Post 42. 
 
I'll be trying this when i get home. Came accross this somehow.. not sure. 
 
Also Posting this so i can find it when i get home. :)
 
Also 
 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)
 
Once again, mostly for me. But its a good post for help.

---

### Post by jrace1 on 2010-11-05
You might try Mint Debian edition. I used it for awhile when I was trying to get Ubuntu to work on my Gateway Netbook. Just a thought. Wish I could help more.

---

### Post by drs305 on 2010-11-05
> **Asylum- said:**
> 
I'll be trying this when i get home. Came accross this somehow.. not sure. 


Post #11 above...  ;-)

---

### Post by Asylum- on 2010-11-05
Lol Whoops. I never did try that. I was gonna But forgot.. you'd been pointing at it the whole time..

---

### Post by foontas on 2010-12-15
Hello!

did this get solved for anyone?
I installed 10.04 on this old desktop and then upgraded to 10.10
but with both installations I had this "Gave up waiting for root device" error, although mine was a little less incapacitating. 

When faced with the error, all I had to do was press the reset button on the tower and the desktop would get to the grub screen and all is good from there. although in 10.04 it didn't even stop at the grub screen (I didn't know about grub before 10.10). 

I tried the solutions above:

I changed my UUID stuff to sda2 (that's the boot partition apparently) although i only did this at the grub screen (pressing "e") as I didn't not know how to do this in the grub file, but i figured it was loading correctly before and after the alteration that it isn't necessary.

I also added "rootdelay=90" after "quiet splash" in the grub file (removing "quiet splash" gave me a bit of a fright when i booted it up)

but neither of these made a difference and the error kept repeating. I can still boot to 10.10

I have run the boot info script and can post the results if you'd like to see them.

thanks for reading! (post got kinda long)

---

### Post by drs305 on 2010-12-16
foontas,

Yes, we need to see the contents of RESULTS.txt.

Open a new post, click on the # icon in the post's menubar. This will create 'code' tags. Paste between the two 'code' tags.

---

### Post by shawnat88 on 2010-12-17
I also have a Toshiba NB205 that can't boot. I'm able to get in using my usb but can't boot from the hard drive. I get the same error message. I'll post back if any of the suggestions above work out for me. 


[PHP]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        34a9baf7-10a2-4552-8398-c9dcc398bc6e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        fbf8ec82-c2c9-48da-9f54-1d115ff1537e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0218-BE80                              vfat       PENDRIVE                      
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
search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
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
    search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=34a9baf7-10a2-4552-8398-c9dcc398bc6e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=34a9baf7-10a2-4552-8398-c9dcc398bc6e ro single 
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
    search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 34a9baf7-10a2-4552-8398-c9dcc398bc6e
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=34a9baf7-10a2-4552-8398-c9dcc398bc6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fbf8ec82-c2c9-48da-9f54-1d115ff1537e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
 146.1GB: boot/grub/grub.cfg
 146.7GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
 146.7GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  7b 0a 1b 74 a9 30 59 8e  68 56 b3 ac aa 44 57 56  |{..t.0Y.hV...DWV|
00000010  a3 af 02 cf 32 34 d1 46  47 ff 01 f1 39 6f 8a ea  |....24.FG...9o..|
00000020  8d ec 89 15 3b dd 21 d9  de 9b 67 ba 6a dd 62 42  |....;.!...g.j.bB|
00000030  ff e1 e2 e4 11 1e 74 65  6d 34 5a 5c b5 84 4d e4  |......tem4Z\..M.|
00000040  2c 6f c2 e4 df b8 e0 db  73 d0 9d e9 47 1d 2a 8b  |,o......s...G.*.|
00000050  4d e0 e6 9e 68 4f 23 2d  ef 79 9f 9c df 54 63 73  |M...hO#-.y...Tcs|
00000060  a8 4d b7 b8 38 a2 79 c9  64 2b 44 32 46 78 4d 7d  |.M..8.y.d+D2FxM}|
00000070  e6 19 ea 9c b0 0b e6 77  fd d5 bd 5e 9c 07 a6 f7  |.......w...^....|
00000080  a9 ec 79 d3 e6 c9 fa 7b  9e 5c aa 2a dc 26 49 14  |..y....{.\.*.&I.|
00000090  14 02 de 1d 50 49 34 29  b6 67 af 13 2d f4 e8 75  |....PI4).g..-..u|
000000a0  a5 b1 36 75 4f 0e 7c 16  19 d6 34 c7 64 2f c3 b5  |..6uO.|...4.d/..|
000000b0  d5 c4 54 09 66 8a 06 9d  02 23 5a d1 06 00 d8 13  |..T.f....#Z.....|
000000c0  ef 51 c4 76 ef fa 96 38  fb bd 61 5d 8b 5c 4a 29  |.Q.v...8..a].\J)|
000000d0  78 d4 13 f0 98 d8 ca e8  60 a7 e9 7f ae e3 9b a7  |x.......`.......|
000000e0  2c fb f7 ef 63 31 19 ad  68 f7 07 15 90 7f a4 2f  |,...c1..h....../|
000000f0  68 88 f5 a2 83 6f 9a 2f  0e ff 05 ff 30 53 53 b1  |h....o./....0SS.|
00000100  ca 98 fd 89 ba e5 d3 0f  f2 4d e6 4e c3 ff 3d 0f  |.........M.N..=.|
00000110  e8 c2 00 45 65 37 3f 9f  2f 05 fe c2 db 2c 8b 8c  |...Ee7?./....,..|
00000120  b0 ce 77 21 50 d5 6c 2e  2a 6c 00 61 ba 2b 67 63  |..w!P.l.*l.a.+gc|
00000130  0e 87 b4 45 15 cb fd 0e  68 63 d5 5c 28 67 13 ee  |...E....hc.\(g..|
00000140  4b b5 c5 95 4e 01 80 f8  c6 7e 3b 0b 78 6d 7c 58  |K...N....~;.xm|X|
00000150  f4 9c 23 67 3d 7f 79 b0  bf ff 0b 5e 05 44 62 f3  |..#g=.y....^.Db.|
00000160  e2 66 ee ad 2b 8e 4a af  ce ed 61 8c d6 6a 46 46  |.f..+.J...a..jFF|
00000170  65 f8 9c d9 1a 98 b3 07  7d c1 c8 c3 d8 f7 eb 19  |e.......}.......|
00000180  43 23 60 66 ff fe bd bb  c1 25 50 32 d2 29 ad 70  |C#`f.....%P2.).p|
00000190  10 34 a9 a2 8c e0 5f 9a  54 8b 78 24 aa fc 8a 49  |.4...._.T.x$...I|
000001a0  74 e2 ff 12 c4 53 37 9f  dc 40 27 21 57 17 ff df  |t....S7..@'!W...|
000001b0  70 7d bb 3f c3 00 57 4e  d4 57 79 09 ba 3b 00 fe  |p}.?..WN.Wy..;..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 40 00  |.X.SYSLINUX...@.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 00 20 00 00  |........?.... ..|
00000020  00 90 77 00 00 1e 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 80 be 18 02 54  72 61 6e 73 63 65 6e 64  |..)....Transcend|
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
00000100  7d 00 66 b8 98 01 16 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

 [/PHP]

---

### Post by shawnat88 on 2010-12-17
I purged and reinstall grub and then set "root=/dev/sda1 rootdelay=90" and erased the "search" line at boot. My problem now is that it's horrible slow unless I hold a key, such as backspace, down throughout the boot and login process. Even after login some processes run slow unless I hold down a key.

---

### Post by shawnat88 on 2010-12-17
Everything is running perfectly for me now. I appended "nohz=off" after "rootdelay=90" hit ctrl-x and was at my login screen in seconds. Setting the rootdelay may no longer be necessary but if it's not broken why fix it.

---

### Post by gamergu on 2010-12-22
can you help me when i turned on ubuntu 10 for the first time it said gave up waiting for root device
then it said /dev/sdb 1 does not exist dropping to a shell
then it shows the busybox   so can you please help i just want to use ubuntu!!!!!

---

### Post by drs305 on 2010-12-22
> **gamergu said:**
> can you help me when i turned on ubuntu 10 for the first time it said gave up waiting for root device
then it said /dev/sdb 1 does not exist dropping to a shell
then it shows the busybox   so can you please help i just want to use ubuntu!!!!!

gameguru,

Welcome to the Ubuntu forums.

If you want to try to fix this by yourself, try this guide. Although it's for users stuck at the grub rescue prompt, you can press "c" at the menu to get to the grub prompt and use the same procedures. If you don't see a Grub2 menu, hold down the SHIFT key during boot until it appears:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

If you would like help, we need to see the status of your boot files. If you can boot the LiveCD, download and run the boot info script and post the contents of the RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by rafiwiener on 2010-12-28
i have the same error with server edition can u help me please
this is ny result file
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 512 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/mapper/isw_ccfciecagj_Volume0 and 
    looks at sector 512 of the same hard drive for core.img, but core.img can 
    not be found at this location.

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

isw_ccfciecagj_Volume01: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_ccfciecagj_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ccfciecagj_Volume03: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,039,743 3,907,039,743  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1             512         2,047         1,536 Bios Boot Partition
/dev/sda2           2,048 3,749,037,055 3,749,035,008 Linux or Data
/dev/sda3   3,749,037,056 3,907,039,231   158,002,176 Linux Swap

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             44    15,679,439    15,679,396   b W95 FAT32


Drive: isw_ccfciecagj_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_ccfciecagj_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_ccfciecagj_Volume01                  1 3,907,039,743 3,907,039,743  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_ccfciecagj_Volume01            512         2,047         1,536 Bios Boot Partition
/dev/mapper/isw_ccfciecagj_Volume02          2,048 3,749,037,055 3,749,035,008 Linux or Data
/dev/mapper/isw_ccfciecagj_Volume03  3,749,037,056 3,907,039,231   158,002,176 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_ccfciecagj_Volume0: PTTYPE="gpt" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        7822-4045                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
error: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
error: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_ccfciecagj_Volume0

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Server" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Install in expert mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed priority=low --
	initrd	/install/initrd.gz
}
menuentry "Install Ubuntu Enterprise Cloud" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/cloud.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
	initrd	/install/initrd.gz
}
menuentry "Rescue a broken system" {
	set gfxpayload=keep
	linux	/install/vmlinuz  rescue/enable=true --
	initrd	/install/initrd.gz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 2c 00 00 00  |........?...,...|
00000020  a4 3f ef 00 7a 07 00 00  00 00 00 00 02 00 00 00  |.?..z...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 45 40 22 78 4e  4f 20 4e 41 4d 45 20 20  |..)E@"xNO NAME  |
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
00000100  7d 00 66 b8 54 24 40 00  66 ba 00 00 00 00 bb 00  |}.f.T$@.f.......|
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

Unknown BootLoader  on isw_ccfciecagj_Volume01


Unknown BootLoader  on isw_ccfciecagj_Volume02


Unknown BootLoader  on isw_ccfciecagj_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory
```

---

