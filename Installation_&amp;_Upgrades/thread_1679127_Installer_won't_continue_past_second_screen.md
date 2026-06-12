---
title: "Installer won't continue past second screen"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by W-Unit on 2011-01-31
Hello :)

I'm having trouble installing Ubuntu Netbook edition (v10.10) on my (brand new, No other OS installed) Asus Eee PC 1215T.
I've successfully booted from the flash drive and can "Try Ubuntu," and everything works when doing so, however when I try to install it, the installer freezes on the second screen, right after language selection.
To be a little more specific, that's the screen with the checkmarks next to "has at least 2.5 GB available drive space," "is plugged in to a power source," and "is connected to the Internet."

After I hit the "Forward" button on this screen, I just get an infinite wait cursor. I can still freely check and uncheck the boxes, and click the "Quit" button, so it's not entirely frozen, but it just won't progress any further.

I had this *exact* same problem just over a week ago when I tried to install Ubuntu on my desktop, also using the flash drive method. I ended up using the Windows installer to get it installed on my desktop, but as the netbook doesn't have any OS installed, that's not an option this time. What's the deal with this!?!

Thanks!

---

### Post by Rubi1200 on 2011-01-31
Hi,
here is what I suggest:

stop the installation.

go to Applications > Accessories > Terminal on the LiveUSB and post the output of this command:

```
sudo parted -l
```

(lowercase L not 1).

After we see that, we can take it from there.

Thanks.

---

### Post by Ell.aeo on 2011-03-04
I'm having the same problem.  When I enter sudo parted -1 in the terminal, I get this message:


Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  244GB  244GB   primary   ext4            boot
 2      244GB   250GB  6036MB  extended
 5      244GB   250GB  6036MB  logical   linux-swap(v1)


Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xc1ff4a]
  15: /lib/libparted.so.0(+0x424b7) [0xc574b7]
  14: /lib/libparted.so.0(+0x432c7) [0xc582c7]
  13: /lib/libparted.so.0(+0x445bc) [0xc595bc]
  12: /lib/libparted.so.0(+0xf7f1) [0xc247f1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xc28072]
  10: /lib/libparted.so.0(+0x45f53) [0xc5af53]
  9: /lib/libparted.so.0(+0x4614f) [0xc5b14f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xc28e55]
  7: parted() [0x804e389]
  6: parted() [0x804f553]
  5: parted() [0x80517da]
  4: parted() [0x8052e51]
  3: parted(main+0x2e) [0x8052f5e]
  2: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x25fbd6]
  1: parted() [0x804c3f1]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    [http://ftp.gnu.org/gnu/parted/](http://ftp.gnu.org/gnu/parted/)

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    [http://www.gnu.org/software/parted](http://www.gnu.org/software/parted)

for further information.

Your report should contain the version of this release (2.2)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function
probe_partition_for_geom() failed.



I don't know where to go from here--any ideas?

Thanks.

E

---

### Post by Rubi1200 on 2011-03-04
Hi and welcome to the forums Ell.aeo :)

Not sure if this is exactly the same problem and you probably should have started your own thread to deal with this.

That said, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Ell.aeo on 2011-03-08
```
                        

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Jolicloud robby 1.1
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
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   476,606,463   476,604,416  83 Linux
/dev/sda2         476,608,510   488,396,799    11,788,290   5 Extended
/dev/sda5         476,608,512   488,396,799    11,788,288  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6ccca11-2d5b-4b45-b641-9d9b16d7da98   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        94E4-9A20                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Jolicloud, with Linux 2.6.35.8-1-jolicloud-atom' --class jolicloud --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
    echo    'Loading Linux 2.6.35.8-1-jolicloud-atom ...'
    linux    /boot/vmlinuz-2.6.35.8-1-jolicloud-atom root=UUID=e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74 ro   quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35.8-1-jolicloud-atom
}
menuentry 'Jolicloud, with Linux 2.6.35.8-1-jolicloud-atom (recovery mode)' --class jolicloud --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
    echo    'Loading Linux 2.6.35.8-1-jolicloud-atom ...'
    linux    /boot/vmlinuz-2.6.35.8-1-jolicloud-atom root=UUID=e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35.8-1-jolicloud-atom
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=e7e78da6-7aff-4a34-8c6c-5e1d31ce7c74 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6ccca11-2d5b-4b45-b641-9d9b16d7da98 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 236.4GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35.8-1-jolicloud-atom
 236.4GB: boot/vmlinuz-2.6.35.8-1-jolicloud-atom
    .5GB: initrd.img
 236.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  bf a0 9c b3 85 b3 44 8f  09 53 4b 9e df b3 65 0c  |......D..SK...e.|
00000010  29 36 ba cb 17 b3 ef 22  8d 9e 3e 7b 9c 38 7c fc  |)6....."..>{.8|.|
00000020  1e ba 2a 41 46 96 90 13  25 8c bd 02 56 f2 9f 2d  |..*AF...%...V..-|
00000030  6b de 19 e7 8d 48 0d 66  15 4c 64 79 0e 56 2e 2b  |k....H.f.Ldy.V.+|
00000040  cb 48 a5 86 74 b5 49 30  9d 0c da 2d c7 ca 8f 81  |.H..t.I0...-....|
00000050  08 a8 f4 e4 83 ca 23 79  00 f8 c7 6c 89 bd 21 bd  |......#y...l..!.|
00000060  e5 a8 27 d8 37 75 89 4a  89 38 cd 84 54 9a 50 6c  |..'.7u.J.8..T.Pl|
00000070  24 f7 63 23 1a 9f 5a b4  74 fc 8b bc 2f cb 79 14  |$.c#..Z.t.../.y.|
00000080  8d 3d cf 9a aa 37 75 c2  06 70 a9 64 1a be 05 4b  |.=...7u..p.d...K|
00000090  df 2a 8e 04 74 24 c8 82  8a c0 ce c2 1c e1 54 93  |.*..t$........T.|
000000a0  e2 65 c0 2e f2 54 2f fa  40 16 9c 2b 38 9f cd 7d  |.e...T/.@..+8..}|
000000b0  5a 9d 8c e8 ae b3 95 38  67 9b b4 e4 73 61 d5 96  |Z......8g...sa..|
000000c0  07 80 19 f7 28 33 d8 4c  4c 84 bb 3d d1 91 ce 69  |....(3.LL..=...i|
000000d0  b0 b6 85 2a ea b6 db 40  2b f6 56 80 56 a3 19 7e  |...*...@+.V.V..~|
000000e0  1a f0 f7 4c 73 31 88 1c  4c 1e 28 f5 06 00 1e 65  |...Ls1..L.(....e|
000000f0  06 d1 95 2b 49 87 be f3  f3 28 d8 f0 e3 10 3d ab  |...+I....(....=.|
00000100  37 0d 7e 95 ec ac 64 c9  65 43 09 ba f4 42 e3 d9  |7.~...d.eC...B..|
00000110  79 50 db 51 e7 89 5b b3  e1 96 5b 9c 38 01 69 7f  |yP.Q..[...[.8.i.|
00000120  84 44 cf 2e b9 05 8d b6  b0 52 75 e6 b9 bc 39 23  |.D.......Ru...9#|
00000130  25 92 79 f9 ea 16 d7 de  15 a1 fb e4 79 dd b8 54  |%.y.........y..T|
00000140  21 ed 06 79 fa a2 23 3f  54 b0 94 de 78 cf 48 9f  |!..y..#?T...x.H.|
00000150  35 fa 94 82 6e 93 4d d9  b2 a5 e0 21 bf ff 4b 91  |5...n.M....!..K.|
00000160  2a 67 43 d7 c9 dd 43 c2  6e b5 80 fd 52 d7 26 b4  |*gC...C.n...R.&.|
00000170  c2 e1 42 4b 91 62 e0 02  d1 06 21 bc 31 c7 42 97  |..BK.b....!.1.B.|
00000180  be 15 aa a4 4c 14 0d a4  1c c9 5d a8 66 38 fb bc  |....L.....].f8..|
00000190  eb ad a6 b3 79 df ae b7  95 23 e3 0b f0 97 bb bb  |....y....#......|
000001a0  01 56 5b 45 a0 ad a6 46  82 46 4d 3b d4 50 e2 1d  |.V[E...F.FM;.P..|
000001b0  d1 bd e7 20 44 6b d7 5c  21 5b 42 78 16 ce 00 fe  |... Dk.\![Bx....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 b3 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
Netbook Remix was causing too many problems for me, so this is actually from Easy Peasy running off a USB.  If that's a problem, I can re-boot UNR and re-run the code.

Thanks so much for the help!

-Ell

---

### Post by neoroses on 2011-03-08
Are you trying to install it once you have booted in to "try with out touching" if so, why not just try install ubuntu from the boot up menue?...I assume you are using the "usb start up disk creator" to make your bootable usb drive?.

If the above doesn't work i suggest trying to make your drive using [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") as i had problems when using the ubuntu creator for my wifes EEEPC. also you could try the "alternate install cd" image. 

Peace

---

### Post by Rubi1200 on 2011-03-08
Can you describe the problem in more detail please.

The script results look fairly normal and you should be able to boot.

The only thing that stands out is that the grub files are towards the end of the drive. Is your BIOS capable of seeing beyond the first 137GB?

---

### Post by Ell.aeo on 2011-03-16
Hi,

Trying different programs to create the USB sticks fixed the error--I now have everything I need installed.

Thanks for the help.

-Ell

---

