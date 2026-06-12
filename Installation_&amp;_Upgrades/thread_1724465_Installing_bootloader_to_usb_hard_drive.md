---
title: "Installing bootloader to usb hard drive"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Fr0stbyte on 2011-04-08
I am trying to install Ubuntu to an external usb hard drive (WD Elements SE). I am also choosing to install the grub bootloader to this disk (/dev/sdb) because I do not want anything modified on the internal drive.

The installation appears to go okay, but when I try to boot to the usb drive, I get the error, "no boot sector on usb device" and it immediately falls back to my interal drive.

I have tried this installation with both 10.10 (amd64) and 11.04 (amd64). How can I fix this?

---

### Post by oldfred on 2011-04-08
Plug external in and run this script. Did you use manual install, to get the combo box on which drive to install grub2's bootloader onto. It likes to default to sda otherwise.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Fr0stbyte on 2011-04-08
> **oldfred said:**
> Plug external in and run this script. Did you use manual install, to get the combo box on which drive to install grub2's bootloader onto. It likes to default to sda otherwise.

Yes, I used manual install and picked /dev/sdb in the combo box. I will run the script and post my results in a little while.

---

### Post by Fr0stbyte on 2011-04-08
Here are my results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   974,673,919   974,671,872   7 HPFS/NTFS
/dev/sda2    *    974,673,920   976,771,071     2,097,152   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   199,999,487   199,997,440  83 Linux
/dev/sdb2         200,001,534   207,998,975     7,997,442   5 Extended
/dev/sdb5         200,001,536   207,998,975     7,997,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        F4701A5A701A23C0                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d011d3e4-abd4-4a12-9c46-063b1af4e447   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        915d239f-033c-472a-9962-ddf7a2182400   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
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
	search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d011d3e4-abd4-4a12-9c46-063b1af4e447 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d011d3e4-abd4-4a12-9c46-063b1af4e447 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d011d3e4-abd4-4a12-9c46-063b1af4e447
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set f4701a5a701a23c0
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
# / was on /dev/sdb1 during installation
UUID=d011d3e4-abd4-4a12-9c46-063b1af4e447 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=915d239f-033c-472a-9962-ddf7a2182400 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
  47.3GB: boot/vmlinuz-2.6.35-22-generic
   1.0GB: initrd.img
  47.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 30 b6 ca 00 00 00 00  00 50 b7 ca 00 00 00 00  |.0.......P......|
000000c0  00 a0 b8 ca 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200

Unknown BootLoader  on sdb2

00000000  a4 1c 08 11 aa c1 18 bf  0f 02 b4 d3 95 bc b0 21  |...............!|
00000010  f1 33 8d 2e 95 84 9f 7e  7f c2 46 2d 42 40 1f 80  |.3.....~..F-B@..|
00000020  1e 83 83 e4 9b 79 fd 5a  6c 90 11 61 21 c0 69 46  |.....y.Zl..a!.iF|
00000030  c9 e5 d6 d0 a5 6b fc e6  ea 1e b4 ae be 63 df c7  |.....k.......c..|
00000040  19 5c 33 17 27 b9 06 44  ee 13 2d 58 70 2d e4 cf  |.\3.'..D..-Xp-..|
00000050  ad 2e 0c eb 0b 66 12 85  d5 7f e4 ef 77 03 13 01  |.....f......w...|
00000060  5e 78 89 1c 27 ed dc 7d  91 d1 49 ed 4c 54 10 b0  |^x..'..}..I.LT..|
00000070  c8 c6 00 d3 3a b8 c6 6f  0f d8 c3 e8 bb d5 76 96  |....:..o......v.|
00000080  11 ad 19 1e a3 61 51 45  07 16 c6 2d a0 fa 22 3b  |.....aQE...-..";|
00000090  a3 aa 6a cc 60 e9 91 6b  18 da bd 3c ad 80 a8 b7  |..j.`..k...<....|
000000a0  b9 12 bb d2 11 51 43 f6  98 1b 5b a0 5a 3d d5 f1  |.....QC...[.Z=..|
000000b0  d8 32 e2 32 7d 59 3f 78  7f 5e db 02 bb 7d 73 eb  |.2.2}Y?x.^...}s.|
000000c0  c4 2a 37 10 d7 46 bd 0e  d0 67 88 1c d9 da 1b fa  |.*7..F...g......|
000000d0  51 3d fb f7 ee 95 9b 89  be f3 88 85 bf 31 90 a1  |Q=...........1..|
000000e0  ba ca f0 2a 7e 3f 82 78  dc be b2 30 99 43 82 1a  |...*~?.x...0.C..|
000000f0  81 f6 f8 c4 ad 7c d7 6e  cd 59 c2 3f 3e 55 8c 9c  |.....|.n.Y.?>U..|
00000100  f6 73 5a 3c bd 73 0f c6  a2 4f 47 00 f3 84 bd 99  |.sZ<.s...OG.....|
00000110  5e 95 5a 95 8d 51 bc e9  9f 0c ba c5 12 88 9f 05  |^.Z..Q..........|
00000120  8d 70 89 eb 3d 67 df 27  fc 54 8e 19 6c 7b 49 16  |.p..=g.'.T..l{I.|
00000130  41 09 7e cc e0 4a 50 0e  59 60 7e 57 67 06 aa 42  |A.~..JP.Y`~Wg..B|
00000140  6e 8d 7f ee d2 11 ea f3  c7 de 46 90 98 6b 67 2c  |n.........F..kg,|
00000150  7d 9e c3 ce 3e 7c d3 85  5e 42 06 14 d8 46 55 5b  |}...>|..^B...FU[|
00000160  27 cb 9f ef d1 b0 03 c0  0f 4f e8 dd 2b e3 f8 68  |'........O..+..h|
00000170  cc 92 03 7d a7 4e 8c b6  52 c3 41 dd a0 6a ac dc  |...}.N..R.A..j..|
00000180  d5 31 55 49 d6 35 6f 24  52 fb 14 b0 78 3b 89 e5  |.1UI.5o$R...x;..|
00000190  db c3 91 b9 98 53 f9 24  ba 51 47 70 cd bc 42 8c  |.....S.$.QGp..B.|
000001a0  f1 94 55 a7 60 3d b0 12  e7 6d 22 ec 93 2e 0d 50  |..U.`=...m"....P|
000001b0  04 6b ee 9e 1c fc 85 2c  e7 4c 8e 83 d3 7f 00 fe  |.k.....,.L......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Fr0stbyte on 2011-04-08
Okay, I am not sure why, but after running that script, Ubuntu is now booting from my external drive. Did that script change anything?

---

### Post by oldfred on 2011-04-08
Script would not have changed anything.

Can you boot windows ok. It shows sda1 as NTFS in one place and unknown file system in another. That may mean you need to run chkdsk.

---

### Post by Fr0stbyte on 2011-04-08
> **oldfred said:**
> Can you boot windows ok. It shows sda1 as NTFS in one place and unknown file system in another. That may mean you need to run chkdsk.

Windows boots. The unknown file system is because of Bitlocker, that is okay.

It doesn't look like it was the script that fixed the problem. I played around with it more and it looks like the bootloader will come up on a cold boot of the system, but on a warm reboot I will get the "no boot sector" error. I can also sometimes get it to work on a warm boot by fiddling with the USB connections. 

If you can offer any suggestions as to alleviate this problem, I would love to hear them, but in the end, I can live with having to do a cold boot for it to work. Thanks for the help!

---

### Post by oldfred on 2011-04-08
Interesting. I thought warm boot would be independent but maybe your warmboot and bitlocker are related somehow. On a cold boot, it does not see the bitlocker since BIOS goes to the external first.

---

### Post by ItalOz on 2012-06-10
I had the same issue,
I usually install the new ubuntu on a external HD to give it a try and see if there are any issues.
Then I copy the old ubuntu on the external drive and check I can boot from there. When I did this everything was working.

So I already had booted from that disk and I knew it was working (just like the original post I suppose) then I plug it in again after a few days and it is not working "no boot sector on usb device"

Finally after reading this post I turned the computer off completely as well as the external drive.

Turned on again an everything worked as usual 

"cold boot" was the solution for me then...

...and now let's try 12.04! :P

---

### Post by oldos2er on 2012-06-10
Old thread closed.

---

