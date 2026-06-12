---
title: "two windows 7 loaders listed in grub.  How do I remove one?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Lyle Lanley on 2010-05-28
Sorry if this isn't the proper place to post this.

I have two listing of windows 7 listed in Grub (I'm not sure why.) and I would like to know how to remove one if I can.  I've searched around, but I can't find any answers to this.

Thanks

---

### Post by darkod on 2010-05-28
Usually one is from your recovery/restore partition. That partition also has boot files to kick off the process, and grub2 detects OSs by boot files. So it 'mistakenly' says it's win7 again.
I wouldn't recommend permanently removing them because that is the way to reach the restore partition if you need it.
There are ways to temporary remove one entry but unless it's a big problem that the entry is thee, you shouldn't bother with it.

---

### Post by Lyle Lanley on 2010-05-28
It's not a problem.  I just wanted to clean up the grub menu.  I don't have a recovery partition on that computer.  I do have a logical partition that I use to store files, but there is not OS on that partition.  Actually, it's set up the same way as my laptop which doesn't have two Windows 7 listings.

---

### Post by darkod on 2010-05-28
That's strange then. There are definitely some boot files (or remains) and they get detected.
If you want to, you can run the boot info script and see what the results say. No need to post them here unless you have questions.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

As for the boot menu, one way is to open /boot/grub/grub.cfg file and copy the whole entry for your win7, like

menuentry {
some lines
}

then paste it in /etc/grub.d/40_custom

That file is for your custom, hand made entries. After you have the win7 entry there, you no longer need automatic detection which will again detect win7. Disable the executive bit from os-prober with:

sudo chmod -x /etc/grub.d/30_os-prober

Recreate new grub.cfg with:

sudo update-grub

In fact, the above procedure is how you can end up with double entry. If there is manual entry in 40_custom but 30_os-prober is not disabled, it will just detect it one more time and you end up with two entries in grub.cfg and in the grub menu.

---

### Post by Lyle Lanley on 2010-05-28
Thanks for all of the quick replies.

I looked at the grub menu, and the listings for Windows 7 is on sda1 and sdb1.  I found that sdb1 is where Windows 7 was installed, and sda1 is my 750GB hard drive that I use for storage.  Obviously I don't need to have my Windows boot loader on the storage drive as well.  I ran the script that was linked in the previous post.  How can I remove the remaining files off of the drive?  

Also, I just realized that it says that grub is installed on sda1 (storage drive).  How can I move everything to the sdb drive (where windows and linux are installed)?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,465,145,343 1,465,143,296   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   167,772,311   167,772,249   7 HPFS/NTFS
/dev/sdb2         167,774,208   871,911,423   704,137,216   7 HPFS/NTFS
/dev/sdb3         871,913,470   976,773,119   104,859,650   5 Extended
/dev/sdb5         871,913,472   972,394,495   100,481,024  83 Linux
/dev/sdb6         972,396,544   976,773,119     4,376,576  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        666C3DD76C3DA2AB                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8949E33949DF45A                       ntfs                                     
/dev/sdb2        3E92895B92891893                       ntfs       Data Files                    
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        20060e27-faf6-4232-b0e8-6f2b89074ded   ext4                                     
/dev/sdb6        c131915d-7f4d-46e5-ad7b-20e9e5232e8c   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=20060e27-faf6-4232-b0e8-6f2b89074ded ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=20060e27-faf6-4232-b0e8-6f2b89074ded ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 20060e27-faf6-4232-b0e8-6f2b89074ded
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 666c3dd76c3da2ab
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set b8949e33949df45a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=20060e27-faf6-4232-b0e8-6f2b89074ded /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c131915d-7f4d-46e5-ad7b-20e9e5232e8c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 459.5GB: boot/grub/core.img
 459.8GB: boot/grub/grub.cfg
 460.3GB: boot/initrd.img-2.6.32-22-generic
 477.9GB: boot/vmlinuz-2.6.32-22-generic
 460.3GB: initrd.img
 477.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  31 36 1c 24 24 29 31 31  31 31 31 31 31 31 31 31  |16.$$)1111111111|
00000010  31 31 31 31 31 31 31 31  31 31 31 31 31 ba ba ba  |1111111111111...|
00000020  ba 31 31 ba ba 31 31 29  5d d3 93 18 6f 93 17 6f  |.11..11)]...o..o|
00000030  d3 6f f7 d2 d6 15 d6 d3  ba d3 5d 29 20 93 ba ba  |.o........]) ...|
00000040  d3 54 22 93 d3 4d 31 31  31 31 31 31 31 31 31 31  |.T"..M1111111111|
00000050  31 31 31 31 31 31 31 31  31 31 31 36 3b 07 f7 c1  |111111111116;...|
00000060  20 19 24 24 29 36 2a 31  fc fc 31 31 31 31 fc fc  | .$$)6*1..1111..|
00000070  1d 31 23 e9 fc ea 23 31  23 ea fc f2 ea fc e9 15  |.1#...#1#.......|
00000080  eb fc f2 1d eb fc fc fc  fc 38 fc fc 4f 31 31 23  |.........8..O11#|
00000090  fc fc 36 31 31 2a fc fc  31 fc fc fc fc 23 31 40  |..611*..1....#1@|
000000a0  fc fc ec 1d 5a fc fc 0c  f2 fc fc fc eb 20 2c e9  |....Z........ ,.|
000000b0  fc ea 29 23 e9 fc ea 23  31 31 3b 07 3b aa 75 29  |..)#...#11;.;.u)|
000000c0  31 31 55 07 31 31 31 31  31 31 31 31 f7 31 31 31  |11U.11111111.111|
000000d0  f7 31 31 31 31 31 31 31  31 31 31 31 36 f7 31 f7  |.111111111116.1.|
000000e0  31 36 f7 31 31 3f f7 36  f7 2a 3f 55 31 31 31 31  |16.11?.6.*?U1111|
000000f0  31 31 31 31 31 4b 55 29  31 4d 4d 31 2a 4d 4b 31  |11111KU)1MM1*MK1|
00000100  29 55 4b 31 29 55 07 31  31 31 31 31 31 31 f7 36  |)UK1)U.1111111.6|
00000110  31 31 31 31 31 31 31 31  31 f7 31 cc cc 3a a6 a6  |111111111.1..:..|
00000120  a6 a6 a6 a6 3a ef a6 a6  ef ef a6 a6 ef a6 a6 ef  |....:...........|
00000130  ef a6 a6 a6 31 31 a6 a6  a6 a6 31 31 a6 a6 a6 a6  |....11....11....|
00000140  a6 a6 a6 a6 31 ef a6 a6  dc ef 2f a6 a6 a6 ef ef  |....1...../.....|
00000150  a6 ef 2f a6 a6 ef dc a6  a6 a6 31 31 31 31 31 31  |../.......111111|
00000160  31 ef a6 a6 52 52 3a 31  31 31 31 31 31 31 31 31  |1...RR:111111111|
00000170  31 31 31 31 31 31 31 29  19 29 31 31 31 36 8a ca  |1111111).)1116..|
00000180  cb f8 20 07 a1 ca ca 75  29 31 36 3b aa ca 4c 31  |.. ....u)16;..L1|
00000190  31 36 21 21 24 29 31 31  31 31 31 31 31 31 31 31  |16!!$)1111111111|
000001a0  31 31 31 31 31 31 31 31  31 31 31 31 ba ba 31 31  |111111111111..11|
000001b0  ba ba 31 ba ba 31 31 2a  f7 d3 84 5b d3 ba 00 fe  |..1..11*...[....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 fd 05 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 38  fd 05 00 d0 42 00 00 00  |.......8....B...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by darkod on 2010-05-28
The easiest to install grub2 to /dev/sdb is to boot ubuntu, and once it is booted just execute:

sudo grub-install /dev/sdb

For deleting the unnecessary win7 boot files, open your /dev/sda1 partition (it should be in Places), and just delete the bootmgr file and the boot folder. BUT BE CAREFUL to delete the correct file/folder, and that you are deleting them from /dev/sda1.

Your ubuntu system also has /boot folder where grub is, so be careful not to delete that.

After that just run:

sudo update-grub

to create updated grub.cfg.

Once all of that is done, it should be fine. It would be better in BIOS to make the 500GB disk as first boot option in hdd order.

---

### Post by Lyle Lanley on 2010-05-28
There is also a file named BOOTSECT.BAK on the sda1 drive.  Is that part of the win 7 boot loader?  Should I delete that as well?

---

### Post by darkod on 2010-05-28
> **Lyle Lanley said:**
> There is also a file named BOOTSECT.BAK on the sda1 drive.  Is that part of the win 7 boot loader?  Should I delete that as well?

If grub2 doesn't report it as boot file, it ignores it. So it wouldn't matter if it stays there.

Also, .BAK are usually backup files, it's probably boot sector backup according to the name.

---

### Post by Lyle Lanley on 2010-05-28
Ok.  I think it's mostly taken care of, but now the script results says that grub is installed on both sda and sdb.  Is there a way to uninstall it from sda? 

BTW, thank you so much for all of your help and quick replies!  I'm still a Linux noob, and this has helped me a great deal.

---

### Post by darkod on 2010-05-28
There is, but it doesn't really matter if it stays on the MBR of the other disk too. Just leave it for now. Later if installing another OS it will get overwritten anyway. :)

---

### Post by Lyle Lanley on 2010-05-28
If you don't mind, I would still like to know how to go about this.  Does it have to do with overwriting the MBR?  

Thanks.

---

### Post by darkod on 2010-05-28
> **Lyle Lanley said:**
> If you don't mind, I would still like to know how to go about this.  Does it have to do with overwriting the MBR?  

Thanks.

Yes, you need to overwrite the MBR of /dev/sda with something, even though you don't need that something. :)

You can also do it from the win7 install dvd but from linux you have more control.

From ubuntu you would have to execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give.

But there is really no need for this, you are just taking risk, if you miss the disk. Instead of "Grub2 is installed on MBR of /dev/sda..." it will say "Lilo is installed in the MBR of /dev/sda...". Something has to be installed.

Using the windows cd/dvd is even riskier because you can't specify on which MBR you want to intervene. If windows writes on the MBR of the other disk, it will destroy the grub2 you need.

---

### Post by Lyle Lanley on 2010-05-28
Ok.  Thank you very much for all of your help!

---

