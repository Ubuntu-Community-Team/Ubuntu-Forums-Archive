---
title: "Windows 7 won't start after dual-boot install of Ubuntu 10.04"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by jpjeffery on 2010-09-06
Hi

Not exactly a unique situation this, and the procedure to get here has worked for me in the past but this time, Windows 7 won't start after selection from the Grub menu.

What I did:
[LIST=1]
[*]Install Windows 7 to 'as new' HDD, creating three partitions: 100Gb for W7, 80Gb (unformatted) for Linux and the rest (unformatted) for data
[*]Boot in to Windows 7 to check it's happy. It is, and can see the other two unformatted partitions. Leave them unformatted.
[*]Boot up Ubuntu Alternate CD (as the graphical installer hangs after the Keyboard Layout window) and install Ubuntu to the 100Gb partition (creating a Swap partition from that 100Gb partition).
[*]Reboot laptop, see the correct/expected OS choices offered by the grub menu. Choose Ubuntu.
[*]Ubuntu boots nicely.
[*]Format the remaining partition as FAT so I can see the disk in both Operating Systems.
[*]Go to bed (well, it was 12:30am!)
[*]Boot up laptop in the morning and choose "Windows 7 (loader) (on /dev/sda1)"
[*]Get an error "***Windows failed to start...1. Insert installation disc, 2. Choose language and click 'Next', 3. Click "Repair your computer"...Status: 0xc0000225...Info: the Boot selection failed because a required device is inaccessible."***
[/LIST]

A basic "Repair Your Computer" with the Windows CD hasn't helped. I could re-install Windows 7 and just start again (there's no data on this HDD) but is there a quicker/easier way to resolve this and keep both the Windows 7 and Ubuntu installs?

---

### Post by Rubi1200 on 2010-09-06
Hi and welcome,
the first thing I suggest is to post the results of the bootscript linked to at the bottom of my post.

Do this from the Ubuntu CD in live mode.

The results will give us a better overview of your setup and make offering solutions easier.

Thanks :)

---

### Post by jpjeffery on 2010-09-06
Thanks for the v quick reply. Here are the results from the UK jury:

[FONT="Courier New"]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 377694208.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,894   377,694,207   377,485,314   5 Extended
/dev/sda5         366,000,128   377,694,207    11,694,080  82 Linux swap / Solaris
/dev/sda6             208,896   156,456,959   156,248,064  83 Linux
/dev/sda7         156,459,008   365,991,935   209,532,928  83 Linux
/dev/sda4         377,694,208   781,420,543   403,726,336   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86DCF863DCF84EC5                       ntfs       System Reserved               
/dev/sda2: PTTYPE="dos" 
/dev/sda4        625A-F779                              vfat       Data                          
/dev/sda5        5464fada-a4c5-45c1-954f-5f196ca6adeb   swap                                     
/dev/sda6        d5ec7a43-7c39-4630-bbe9-314b65934d4f   ext4       Linux                         
/dev/sda7        4a6694ae-cb05-4a9d-b14e-97c16f35588f   ext4       home                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d5ec7a43-7c39-4630-bbe9-314b65934d4f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d5ec7a43-7c39-4630-bbe9-314b65934d4f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d5ec7a43-7c39-4630-bbe9-314b65934d4f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86dcf863dcf84ec5
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d5ec7a43-7c39-4630-bbe9-314b65934d4f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4a6694ae-cb05-4a9d-b14e-97c16f35588f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5464fada-a4c5-45c1-954f-5f196ca6adeb none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  73.2GB: boot/grub/core.img
  21.8GB: boot/grub/grub.cfg
  73.3GB: boot/initrd.img-2.6.32-24-generic
  73.2GB: boot/vmlinuz-2.6.32-24-generic
  73.3GB: initrd.img
  73.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  40 0c 19 10 99 14 09 04  99 00 02 12 0b 1b 2f c4  |@............./.|
00000010  dd c4 00 2f fd c4 d4 ed  c4 31 30 01 32 15 14 23  |.../.....10.2..#|
00000020  22 04 07 06 23 22 35 34  36 36 24 13 32 15 14 23  |"...#"5466$.2..#|
00000030  22 04 07 06 23 22 35 34  36 36 24 04 2b 4e 73 9d  |"...#"5466$.+Ns.|
00000040  fe 52 53 3c 15 3a 47 83  02 06 41 4d 70 9e fe 50  |.RS<.:G...AMp..P|
00000050  54 3a 14 3b 46 83 02 07  03 fa 4e 5c 12 09 06 64  |T:.;F.....N\...d|
00000060  21 27 0d 12 fe 7b 4e 5c  12 09 06 64 21 27 0d 12  |!'...{N\...d!'..|
00000070  00 01 00 54 01 1f 04 6f  04 9a 00 1f 00 3d 40 29  |...T...o.....=@)|
00000080  49 13 59 13 02 65 1d 75  1d 85 1d 03 03 18 0d 11  |I.Y..e.u........|
00000090  48 03 00 1d 03 18 09 46  00 56 00 02 00 38 0d 11  |H......F.V...8..|
000000a0  48 06 06 00 11 1f 1b 01  1b 2f 5d cd 39 39 2f 2b  |H......../].99/+|
000000b0  5d 00 2f c4 17 39 2b 5d  31 30 5d 01 26 24 27 26  |]./..9+]10].&$'&|
000000c0  26 35 34 36 33 32 17 17  05 1e 02 15 14 06 07 05  |&54632..........|
000000d0  06 04 23 22 26 35 34 37  36 24 03 73 a8 fe 93 31  |..#"&5476$.s...1|
000000e0  10 17 28 26 1e 57 c5 01  0a 9d 29 11 2a 68 fe bf  |..(&.W....).*h..|
000000f0  d8 fe f0 21 1c 23 58 5c  01 ce 02 e5 5a ad 10 05  |...!.#X\....Z...|
00000100  24 16 2a 35 29 5f 85 50  1b 22 1d 2b 2e 2b 84 59  |$.*5)_.P.".+.+.Y|
00000110  63 3a 28 36 1e 1a b1 00  00 01 00 2f fe 33 04 4c  |c:(6......./.3.L|
00000120  05 b4 00 22 00 4a 40 2b  17 22 27 22 77 22 03 20  |...".J@+."'"w". |
00000130  00 01 52 00 8d 0f 13 14  0f 0f 13 20 13 00 0f 3f  |..R........ ...?|
00000140  1b 01 1b 1b 13 08 0f 00  99 0d 03 99 0b 1b 1d 20  |............... |
00000150  99 16 07 00 3f fd c4 3f  ed d5 ed 30 01 2f cd 33  |....?..?...0./.3|
00000160  33 2f 5d 11 33 11 33 87  10 2b 2b 10 c4 31 01 5d  |3/].3.3..++..1.]|
00000170  01 16 17 17 1e 03 15 14  06 23 22 24 26 35 34 1a  |.........#"$&54.|
00000180  02 36 36 33 32 1e 02 15  14 23 22 26 23 06 00 01  |.6632....#"&#...|
00000190  06 32 5b 97 3d 19 12 08  3c 31 24 fe 5c 36 73 c0  |.2[.=...<1$.\6s.|
000001a0  b3 24 3e 27 6e f2 37 17  67 36 b1 44 5c fe c4 fe  |.$>'n.7.g6.D\...|
000001b0  f4 02 05 0b 04 0c 18 1e  11 21 37 12 21 29 00 fe  |.........!7.!)..|
000001c0  ff ff 82 fe ff ff 02 88  cd 15 00 70 b2 00 00 00  |...........p....|
000001d0  33 0d 05 fe ff ff 01 00  00 00 01 28 50 09 00 00  |3..........(P...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/FONT]

---

### Post by Rubi1200 on 2010-09-06
> Here are the results from the UK jury:Cute!

Well, I don't see any obvious errors in the bootscript except maybe this:

 > [FONT=Courier New]According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 377694208.[/FONT]

The only thing I can think of right now is that maybe you should have run a chkdsk when you were in Windows (just to let it feel good?).

As to resolving this:
My advice is to wait a bit and see if anyone else has some suggestions.

Barring that, I would reinstall the Windows bootloader and then run chkdsk at least twice to see if all is okay.

Assuming it is, then simply reinstall GRUB and you should be back in business with the setup you want.

---

### Post by presence1960 on 2010-09-06
You are indeed missing boot files for windows 7. Windows will never boot in it's current condition.

Here is what mine look like. Note the red:

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Testdisk is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR="Red"]/Windows/System32/winload.exe[/COLOR]
```
You are going to have the boot Windows DVD to use Startup repair. After that completes reboot without the DVD to see if windows boots. If it does you can then reinstall GRUB.

If it doesn't boot, use the DVD to run Start up Repair again.

If you need help reinstalling GRUB post back

---

### Post by jpjeffery on 2010-09-06
> **presence1960 said:**
> You are going to have the boot Windows DVD to use Startup repair.

Already tried that, but will give it another go.

Might have to go the bootsec /fixmbr route...

---

### Post by jpjeffery on 2010-09-06
> **Rubi1200 said:**
> Cute!

I'm here all week. Try the veal!

---

### Post by wilee-nilee on 2010-09-06
I wonder if sda1 is large enough, and a partition has been removed, or overwritten.

---

### Post by oldfred on 2010-09-06
Windows created its standard boot/recovery 100mb partition as sda1 and the install was in sda2. It then looks like (and your initial explanation say) you overwrote the 100GB windows partition when you made the extended partition and never used a 80GB partition for Ubuntu.

---

### Post by presence1960 on 2010-09-06
> **oldfred said:**
> Windows created its standard boot/recovery 100mb partition as sda1 and the install was in sda2. It then looks like (and your initial explanation say) you overwrote the 100GB windows partition when you made the extended partition and never used a 80GB partition for Ubuntu.

Good catch oldfred & wilee-nilee. I didn't notice the size of sda1 in the fdisk output. The windows partition is gone! sda1 is a system reserved boot partition for win 7.

---

### Post by jpjeffery on 2010-09-07
Agreed. Clearly the error means "I can't actually find the Windows install folders anywhere!"

Not sure how I managed that but I'm just starting again, blowing away the partitions and installing Windows from scratch with three partitions (plus the 100Mb one it'll create for me), two of which I'll use later when I install Ubuntu.

---

### Post by jpjeffery on 2010-09-07
All working now. Choice of Windows 7 or Linux Mint 9. I guess the first lot of partitioning wasn't quite right (and or user error!)

Thanks to all for your responses.

---

