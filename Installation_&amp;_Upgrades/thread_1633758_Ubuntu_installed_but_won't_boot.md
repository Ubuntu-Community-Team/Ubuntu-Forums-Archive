---
title: "Ubuntu installed but won't boot"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by shinigami82654 on 2010-11-29
I completely switched from Windows XP to Ubuntu Netbook 10.10 on my AOA 110. I had to use a live usb and everything worked correctly in the installation (I think...) but when I rebooted it all that happens is the acer boot screen and then the blinking text-mode cursor (of death) immediately after that.
 
I've tried pressing shift to load grub (read it on another post) but it does nothing.
 
Edit: I can boot from the live usb when I hit Run without installing but when I select help it says no init found. Try passing init =bootarg

---

### Post by mörgæs on 2010-11-30
Hi, welcome to the forum.

Yes, adding boot arguments (after pushing F6) might be the solution:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by lpbryan on 2010-11-30
I'm having the same problem on the same machine: after installing Ubuntu (and removing Windows XP) from a USB to my Acer AOA110, when I turn on the netbook I see the Acer logo and then a black screen with blinking white cursor. I pressed F2 and set it to boot from the hard drive instead of USB, but nothing happens and I can't type anything or press any buttons (other than F2 or F10 to get to BIOS)

I looked at the link you posted ([https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)) but I am brand new to this and very confused. Much of what is on that page doesn't really make sense to me; I see the list of common boot options, but I don't really know what any of them mean, so I don't know what to try typing after the boot prompt!

Second question about the LiveCDBootOptions: won't anything I do there only temporarily affect the way it boots from the USB?

I'm so very confused and appreciate any help I can get!

---

### Post by Quackers on 2010-11-30
Please boot from the Ubuntu Live cd and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by drs305 on 2010-11-30
> **lpbryan said:**
> I looked at the link you posted ([https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)) but I am brand new to this and very confused. Much of what is on that page doesn't really make sense to me; I see the list of common boot options, but I don't really know what any of them mean, so I don't know what to try typing after the boot prompt!

Second question about the LiveCDBootOptions: won't anything I do there only temporarily affect the way it boots from the USB?

I'm so very confused and appreciate any help I can get!

Sorry the page is confusing. The options aren't explained on the page but can be found with Google. I was one of the authors and the pages aren't meant to be all-inclusive. The supervisors of the official documentation prefer for us not to have links to outside sites in the official docs.

Added:
For example, here is a link to a page about the nomodeset option: [_http://linux.derkeiler.com/Mailing-Lists/Fedora/2010-06/msg00050.html_]("http://linux.derkeiler.com/Mailing-Lists/Fedora/2010-06/msg00050.html")
End Add.

For video problems, which are often indicated by the blinking cursor, the 'nomodeset' option sometimes works (especially with nvidia cards).

Yes, the changes made by the F6 key are temporary. If you find an option that works, you would need to add it to the end of the "linux" line in /etc/default/grub after you have accomplished a boot to the normal installation.

---

### Post by lpbryan on 2010-11-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

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
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
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

Disk /dev/sdb: 4076 MB, 4076863488 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7962624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,962,569     7,962,507   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   FC30-3DA9                              vfat                                     
/dev/sda1        1f37dc04-5f0e-4da6-87cd-699631960f66   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0a81ad06-75b9-4374-bcd7-d6a3dc0190aa   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C48A-1314                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/FC30-3DA9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
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
    search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1f37dc04-5f0e-4da6-87cd-699631960f66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1f37dc04-5f0e-4da6-87cd-699631960f66 ro single 
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
    search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 1f37dc04-5f0e-4da6-87cd-699631960f66
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a81ad06-75b9-4374-bcd7-d6a3dc0190aa none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.35-22-generic
   2.5GB: boot/vmlinuz-2.6.35-22-generic
   1.6GB: initrd.img
   2.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b7 fe 89 78 bc 58 f6 b4  3b e9 10 f5 94 e6 34 d2  |...x.X..;.....4.|
00000010  44 80 91 ea 8d 4c db 24  f9 1d 6b 59 b1 ac e4 97  |D....L.$..kY....|
00000020  fe 8e 24 39 56 9b 75 9f  aa be 56 3d e6 e5 e2 74  |..$9V.u...V=...t|
00000030  c6 3c ba db 77 04 a3 36  ad 5f 0e ed f3 56 9b 63  |.<..w..6._...V.c|
00000040  55 b2 24 aa fe 72 e8 de  2a c1 af 13 e9 b2 e1 e4  |U.$..r..*.......|
00000050  08 47 5d 3b f1 38 1f a4  e3 6d 60 62 81 10 15 63  |.G];.8...m`b...c|
00000060  1e 5e 41 bc 92 e2 cd 27  a2 20 22 a7 89 7a ce 1b  |.^A....'. "..z..|
00000070  66 56 14 f3 b7 7e 84 59  35 c5 9a 4f 7b 43 c4 06  |fV...~.Y5..O{C..|
00000080  21 9a cb df cc 1a 18 c4  14 34 13 4d 6a 8b 7d 44  |!........4.Mj.}D|
00000090  b5 7a be de 04 b0 a1 25  47 84 56 49 df e0 a1 9e  |.z.....%G.VI....|
000000a0  a8 c2 31 8b f6 10 2f a2  78 8b 5d 98 1b 53 5c 6b  |..1.../.x.]..S\k|
000000b0  8a 10 e2 26 14 d7 9d 1b  84 e8 29 42 5f cf 76 7f  |...&......)B_.v.|
000000c0  f0 1b fc 51 13 ac 55 5a  67 bc 71 72 4e e7 19 b8  |...Q..UZg.qrN...|
000000d0  52 6d ab 40 b6 53 f8 7a  b3 ad 44 49 57 4b cf 67  |Rm.@.S.z..DIWK.g|
000000e0  c3 da ed b2 01 c0 1a 10  3b fc ff cb 08 60 cd 77  |........;....`.w|
000000f0  da 9e 8f 37 a7 84 6c c1  da 7c 2d bb 95 70 9b 4a  |...7..l..|-..p.J|
00000100  1a 92 ac 4c c3 3c e1 cd  ee be 19 cf 39 c5 da f1  |...L.<......9...|
00000110  7c 3f 04 5a 4f d2 23 95  da cd f5 12 10 ff 84 5a  ||?.ZO.#........Z|
00000120  9e d2 bc 0c 98 a1 74 a7  11 fe 85 88 ef 93 c6 74  |......t........t|
00000130  a2 89 af 93 26 9e af 03  b3 52 4f 2e d1 2f 93 66  |....&....RO../.f|
00000140  c4 57 f5 7d 9b dc 57 0d  bd 5f 07 6f c3 bd ba b6  |.W.}..W.._.o....|
00000150  06 6e 3e 86 5b 92 ad 87  e6 a2 4d d7 ac 30 d3 6c  |.n>.[.....M..0.l|
00000160  ac dd ca 52 f6 30 6b da  e1 d0 e4 06 ff c8 8f 73  |...R.0k........s|
00000170  8f 47 d1 54 90 a5 8c f6  84 d2 d6 17 ef 91 94 66  |.G.T...........f|
00000180  64 a3 35 07 b1 20 9e af  b1 ca cf a3 86 c1 dd 03  |d.5.. ..........|
00000190  ae cc 19 d5 5c 31 ae a1  62 4d 56 ef 12 f0 70 13  |....\1..bMV...p.|
000001a0  a2 3e 78 a8 29 5d c4 1e  36 d5 78 a7 3a 81 3b a9  |.>x.)]..6.x.:.;.|
000001b0  2c 27 42 bf 97 8c 35 dc  69 07 80 27 d9 58 00 c8  |,'B...5.i..'.X..|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  8b 7f 79 00 51 1e 00 00  00 00 00 00 02 00 00 00  |..y.Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 14 13 8a c4 55  4e 54 49 54 4c 45 44 20  |..)....UNTITLED |
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
00000100  7d 00 66 b8 9a e4 2d 00  66 ba 00 00 00 00 bb 00  |}.f...-.f.......|
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

 
```

---

### Post by Quackers on 2010-11-30
The first thing I notice is that there is no bootloader installed in /dev/sda. Grub should be there.
If you boot from the live cd/usb and choose "try ubuntu" and when the desktop appears make sure you have an internet connection.
Then please open up a terminal and copy/paste these lines into the terminal, pressing enter after each line.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then please reboot and report what happens.

---

### Post by drs305 on 2010-11-30
lpbryan,

You don't have Grub2 (or any bootloader) installed in the MBR.

Boot to the LiveCD Desktop, open a terminal (Applications, Accessories, Terminal), and run the following commands. When using "sudo", you will be asked for your password. You won't see it as you type.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you don't add the partition number in the second command.


Edit: Well, that was a waste of time since *Quackers* is already on it!

---

### Post by lpbryan on 2010-11-30
Thanks both of you.  the "ubuntu@ubuntu" lines are what I typed as suggested by you, and the other lines are the responses I got. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sdal /mnt
mount: special device /dev/sdal does not exist
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda

/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).

```

They don't look promising... should I reboot anyway? And if so, should I  reboot from the USB again or try to boot from the hard drive?

Side question: is grub an Ubuntu thing or something that my computer would have already had on it (it came with Windows XP installed, and the reason I decided to change to Ubuntu is that WinXP was so horribly slow and wasn't working well for the previous owner)

---

### Post by Quackers on 2010-11-30
That should be sda1 not sdal
It is usually safer to copy/paste the commands into the terminal :-)

---

### Post by lpbryan on 2010-11-30
> **Quackers said:**
> That should be sda1 not sdal
It is usually safer to copy/paste the commands into the terminal :-)

Well whaddaya know... when I actually type it in properly it actually works. 

Thanks to Quackers and drs, I now have a functioning netbook! Thank you thank you thank you!!!

---

### Post by Quackers on 2010-11-30
Oh Happy Day! :-)
Nice one! Enjoy!

You're welcome.

Please mark the thread as solved using the Thread Tools near the top of the board.

---

### Post by shinigami82654 on 2010-12-02
Ah. I figured out my problem. I used unetbootin instead of the one ubuntu suggests. I'm thinking things didn't transfer correctly and screwed it up. It works now however.

---

### Post by mmh101 on 2011-05-31
Hi, just ran into the same problem as OP. Ubuntu won't reboot and I'm using dual system. (windows vista.)

here's the results file:
thanks if advance.


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
    Operating System:  
    Boot files:        /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     20,466,810   166,761,929   146,295,120   6 FAT16
/dev/sda3         166,802,895   312,576,704   145,773,810   7 NTFS / exFAT / HPFS
/dev/sda4         312,578,046   321,671,167     9,093,122   5 Extended
/dev/sda5         312,578,048   320,102,399     7,524,352  83 Linux
/dev/sda6         320,104,448   321,671,167     1,566,720  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        628CCBE816D9B5D2                       ntfs       PQSERVICE
/dev/sda2        D20C15E70C15C6FF                       ntfs       ACER
/dev/sda3        0618E70318E6F11B                       ntfs       DATA
/dev/sda5        3416395c-6eaf-4ac5-b310-9778cce5ab32   ext4       
/dev/sda6        b1f5358d-0d67-47c6-8d6a-38886c9da1fb   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
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
    search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3416395c-6eaf-4ac5-b310-9778cce5ab32 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3416395c-6eaf-4ac5-b310-9778cce5ab32 ro single 
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
    search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3416395c-6eaf-4ac5-b310-9778cce5ab32
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 628CCBE816D9B5D2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root D20C15E70C15C6FF
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
UUID=3416395c-6eaf-4ac5-b310-9778cce5ab32 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b1f5358d-0d67-47c6-8d6a-38886c9da1fb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 149.221855164 = 160.225746944  boot/grub/core.img                             1
 151.745838165 = 162.935853056  boot/grub/grub.cfg                             1
 149.826389313 = 160.874860544  boot/initrd.img-2.6.38-8-generic               1
 150.467102051 = 161.562820608  boot/vmlinuz-2.6.38-8-generic                  1
 149.826389313 = 160.874860544  initrd.img                                     1
 150.467102051 = 161.562820608  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by drs305 on 2011-05-31
> **mmh101 said:**
> Hi, just ran into the same problem as OP. Ubuntu won't reboot and I'm using dual system. (windows vista.)

here's the results file:
thanks if advance.

Generally we prefer you start your own thread so the issues, which may appear identical, don't get confused. Since the OP seems to have finished with this thread, we'll continue here unless he starts posting to it again.

In your case, please enter the BIOS setup as the computer boots and check the reported drive size. All of your Grub files are beyond the 137GB limit for older BIOS's and it's possible Grub can't find the necessary boot files. If your BIOS does show a drive size of approximately 137GB, see if there is an option to enable LBA or something like 'large' drives.

If it reports the correct drive size, try holding down the SHIFT key to see if the Grub menu appears. If it does and you can make a selection, do you end up at a blinking cursor in the upper left of a black screen?

---

### Post by mmh101 on 2011-05-31
as i hit post i realized i should have posted a new thread. Sorry. :)

i'll go ahead and try this and report back.

---

### Post by mmh101 on 2011-05-31
ok I rebooted and went into set up menu looked all over the place and couldn't find the bios size.
i have a AMD Athleon 64 processor 3800+

is there another way ?

---

### Post by drs305 on 2011-05-31
> **mmh101 said:**
> ok I rebooted and went into set up menu looked all over the place and couldn't find the bios size.
i have a AMD Athleon 64 processor 3800+

is there another way ?

At the grub prompt (you can get to it with 'c' if you get the menu):
```
ls # You should see the drives and partitions
ls (hd0,5)/ # Do you see vmlinuz and initrd.img ?
ls (hd0,5)/boot  # Do you see vmlinuz-2.6.38-8-generic and initrd.img-2.6.38-8-generic files?
ls (hd0,5)/boot/grub # Do you see a lot of *.mod files
```
This should tell us if Grub can see the boot files or not.

---

### Post by mmh101 on 2011-05-31
Ok, at work so will get back as soon as I can.

---

### Post by mmh101 on 2011-05-31
ok went back and rebooted and got set up menu. this machine is using the **Phoenix Award Bios CMOS** setup, and seems like it's not able to get into nto bios settings and look around and not able to use the 'c' prompt.

all i get is pre-set settings ?

---

### Post by drs305 on 2011-05-31
> **mmh101 said:**
> ok went back and rebooted and got set up menu. this machine is using the **Phoenix Award Bios CMOS** setup, and seems like it's not able to get into nto bios settings and look around and not able to use the 'c' prompt.

all i get is pre-set settings ?

Those commands aren't executed in BIOS. They would be executed at the grub prompt (if you get one). The grub prompt is probably where the system stops once the boot fails. Or try holding down the SHIFT key during boot to display the Grub menu, then press 'c'.  Sorry for the confusion. The only reason at this point to enter BIOS is to check the ***drive size***, then exit and continue the boot.

---

### Post by mmh101 on 2011-05-31
oh ok i'll give that a shot. thanks.

---

### Post by mmh101 on 2011-05-31
ok here's what happened. as it rebooted i held down the 'shift', didnt work and it went back to what it always does which is for a split second saw loading then it said 'input not supported'. now this happened first time i rebooted then 15 seconds later ubuntu came on.

but ever since, all that happens is it says 'input not supported' then goes to black screen with nothing happening.

so not able to get into Grub menu.

---

### Post by oldfred on 2011-05-31
Computers do not like inconsistencies. One place says FAT16 and the other is NTFS. Should be NTFS in both.

/dev/[COLOR=Red]sda2[/COLOR]    *     20,466,810   166,761,929   146,295,120   6 [COLOR=Red]FAT16[/COLOR]
[COLOR=Red]
sda2[/COLOR]: _____________

    File system:       [COLOR=Red]ntfs[/COLOR]
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


Vista would not work from FAT16 anyway, so it looks like somehow partition table got messed up.

I would back up partition table using liveCD:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Then see if System, Administration, Disk Utility, click on sda2 will let you change it. If not testdisk or even just editing the PT.txt with 7 for NTFS in place of the 6 and reloading it.

---

### Post by mmh101 on 2011-05-31
ok i'll try that. i guess if i screw up just pop in cd from Cdlive? (beginner in computers.)

i did compress the windows partition by 20 mb before installing nubutu according to instructions from someone on internet. maybe that had something to do with it.

---

### Post by mmh101 on 2011-06-01
i have a question. what about if i just reinstall ubuntu and at the prompt just format entire drive. i'm thinking that would solve the problem ?

---

### Post by mmh101 on 2011-06-01
anybody have an answer for this ?
thanks in advance.

old fred said:
> Vista would not work from FAT16 anyway, so it looks like somehow partition table got messed up.then i said:
> what about if i just reinstall ubuntu and at the  prompt just format entire drive. i'm thinking that would solve the  problem ?

---

### Post by mörgæs on 2011-06-01
Yes, most likely. If you don't need Windows, installing Ubuntu on the entire drive will give you a new boot loader and get rid of FAT 16 (but I am not saying this is the only way of solving the problem).

You don't have to format the drive before. It is done automatically in the process.

---

### Post by drs305 on 2011-06-01
> **mmh101 said:**
> anybody have an answer for this ?
thanks in advance.

old fred said:
then i said:

Yes, you could do that, but you are reinstalling for a reason that might be able to be fixed with two commands. If you would rather reinstall and start fresh, that is certainly your choice.

As *oldfred* mentioned:
> 
Backup partition table to text file & save to external device.
**sudo sfdisk -d /dev/sda > PT.txt**

... even just editing the PT.txt with 7 for NTFS in place of the 6 and reloading it. 


You would change the entry for sda2. Change the 6 to a 7 (or 07 or 06, if that is how it is written), save the file, and then import it back with sfdisk.

---

### Post by mmh101 on 2011-06-01
ok great. thanks for the responses. if i do decide to keep windows i'll post back with results.

---

### Post by skale1 on 2012-09-13
same problem.....

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 74990016 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1476064 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        212,992    41,172,991    40,960,000   7 NTFS / exFAT / HPFS
/dev/sda2          41,172,992   137,850,879    96,677,888  83 Linux
/dev/sda3         137,850,880   242,708,479   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda4         242,708,480   976,771,071   734,062,592   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3926 MB, 3926949888 bytes
16 heads, 16 sectors/track, 29960 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,669,823     7,661,760   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4860444660443CC6                       ntfs       RECOVERY
/dev/sda2        8745c230-1e20-4972-9550-ea43537e2104   ext4       
/dev/sda3        F04AFF964AFF5834                       ntfs       
/dev/sda4        AA56A09256A06135                       ntfs       
/dev/sdb1        0CFC-B2E2                              vfat       KINGSTON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=8745c230-1e20-4972-9550-ea43537e2104 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=8745c230-1e20-4972-9550-ea43537e2104 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8745c230-1e20-4972-9550-ea43537e2104
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4860444660443CC6
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8745c230-1e20-4972-9550-ea43537e2104 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-29-generic               1
               =                boot/vmlinuz-3.2.0-29-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

