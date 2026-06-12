---
title: "How to safely reinstall Win7 on the machine with Win7 &amp; Ubuntu"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by hoanggeneral on 2010-11-21
Hi all;
I want to reinstall the Win 7 on my desktop which has 2 HDs:

1) 1TB HD with Windows 7 on /dev/sda1
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24281   195034112    7  HPFS/NTFS
/dev/sda2           24281       25980    13643776    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25980      121601   768079872    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

2) 20GB with Ubuntu 10.04:
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2241    17998848   83  Linux
/dev/sdb2            2242        2434     1549313    5  Extended
/dev/sdb5            2242        2434     1549312   82  Linux swap / Solaris

The 1 TB HD was installed with Win 7 before the 20GB HD was installed with Ubuntu 10.04.
I know that if I just format the /dev/sda1 and install a new Win7, the Ubuntu will die. I don't want this happening since I spent a lot of time in building this Ubuntu.
I would be very grateful if any one has solution to safely reinstall the Win7 without any affect on the Ubuntu.
Thank you. :D

---

### Post by wilee-nilee on 2010-11-21
**I would be very grateful if any one has solution to safely reinstall the Win7 without any affect on the Ubuntu.**
Thank you. :D[/QUOTE]

Sorry can't be done, but the good news is just reinstall the grub bootloader to the mbr of the Ubuntu HD. If it is grub2 follow this link. If the Ubuntu HD is a usb external then your okay just unplug it. Or you can unplug the Ubuntu HD from inside the computer.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Really lets have a look at your setup click on the bootscript link in my sig, follow the instructions. Come back to the thread hit the reply then # in the reply panel and paste the text in between the code tags.

---

### Post by sikander3786 on 2010-11-21
> I know that if I just format the /dev/sda1 and install a new Win7, the Ubuntu will die. 

It would only happen if you are sure that Grub is installed to sda.

If Grub is installed on sdb, you can safely re-install Windows on sda HDD, and update-grub later for dual-booting.

It would be better to post the output of bootinfoscript as per instructions here from you existing Ubuntu install.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would give us a better idea of you setup.

Please wrap the output with proper code tags # from post menu.

---

### Post by hoanggeneral on 2010-11-23
Hi there;

Sorry for my late reply. I was too busy yesterday.
This's the content of the file RESULT.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   390,070,271   390,068,224   7 HPFS/NTFS
/dev/sda2         390,070,272   417,357,823    27,287,552   7 HPFS/NTFS
/dev/sda3         417,357,824 1,953,517,567 1,536,159,744   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    35,999,743    35,997,696  83 Linux
/dev/sdb2          36,001,790    39,100,415     3,098,626   5 Extended
/dev/sdb5          36,001,792    39,100,415     3,098,624  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42D8E371D8E36221                       ntfs                                     
/dev/sda2        AC2240C32240946C                       ntfs       Recovery                      
/dev/sda3        CAAE4CFCAE4CE295                       ntfs       resource                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78b999b5-9523-4877-a62b-c70b5ff7fd4e   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        78168c95-4ecf-494b-a146-a49ed097d999   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=78b999b5-9523-4877-a62b-c70b5ff7fd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=78b999b5-9523-4877-a62b-c70b5ff7fd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=78b999b5-9523-4877-a62b-c70b5ff7fd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=78b999b5-9523-4877-a62b-c70b5ff7fd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 78b999b5-9523-4877-a62b-c70b5ff7fd4e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 42d8e371d8e36221
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=78168c95-4ecf-494b-a146-a49ed097d999 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   2.4GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
   3.6GB: boot/initrd.img-2.6.32-25-generic
   2.4GB: boot/vmlinuz-2.6.32-21-generic
   2.9GB: boot/vmlinuz-2.6.32-25-generic
   3.6GB: initrd.img
   2.4GB: initrd.img.old
   2.9GB: vmlinuz
   2.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4c 4b 74 4a 49 72 47 47  75 48 48 76 47 4b 79 49  |LKtJIrGGuHHvGKyI|
00000010  4d 7b 46 4e 79 44 4c 77  42 4b 73 42 4b 73 43 49  |M{FNyDLwBKsBKsCI|
00000020  72 41 47 70 41 45 6e 3e  42 6b 3c 40 69 3b 3f 68  |rAGpAEn>Bk<@i;?h|
00000030  34 39 65 35 3a 66 34 3c  67 33 3b 66 2c 3a 64 2b  |49e5:f4<g3;f,:d+|
00000040  39 63 28 38 62 28 38 62  53 bd ec 5b c5 f4 49 c0  |9c(8b(8bS..[..I.|
00000050  f3 51 c8 fb 40 cf fa 44  d3 fe c3 ff d4 d2 ff e3  |.Q..@..D........|
00000060  ff d8 8b ce 47 00 12 01  00 20 0f 05 02 14 04 09  |....G.... ......|
00000070  1b 0b 28 17 0c 29 18 0d  1b 13 12 1b 13 12 18 16  |..(..)..........|
00000080  11 18 16 11 17 19 0c 17  19 0c 1b 19 07 1b 19 07  |................|
00000090  21 18 0a 23 1a 0c 23 1a  0f 27 1e 13 17 1d 18 0e  |!..#..#..'......|
000000a0  14 0f 12 25 22 36 49 46  50 35 12 36 1b 00 10 09  |...%"6IFP5.6....|
000000b0  00 1f 18 0d 09 17 23 00  0d 19 1f 31 3e 62 74 81  |......#....1>bt.|
000000c0  89 90 89 8b 92 8b 92 8a  72 96 8e 76 96 8c 6d 8c  |........r..v..m.|
000000d0  82 63 8d 88 6f 88 83 6a  88 73 35 5d 48 0a 2b 08  |.c..o..j.s5]H.+.|
000000e0  1a 33 10 22 01 16 35 27  3c 5b 6e a5 84 81 b8 97  |.3."..5'<[n.....|
000000f0  b4 af 86 a6 a1 78 c2 99  96 c4 9b 98 ba a1 85 ca  |.....x..........|
00000100  b1 95 cd b5 53 91 79 17  43 1a 00 3f 16 00 18 2a  |....S.y.C..?...*|
00000110  23 19 2b 24 3a 6d 63 96  c9 bf b3 cc a5 93 ac 85  |#.+$:mc.........|
00000120  c7 ba 8c be b1 83 ca b8  9f c0 ae 95 b2 ac 99 ba  |................|
00000130  b4 a1 b1 af 8d bf bd 9b  af a6 8a b7 ae 92 b6 ac  |................|
00000140  94 bb b1 99 b5 af 9a b2  ac 97 b5 bc a7 bd c4 af  |................|
00000150  d9 e7 cd ee fc e2 ba c2  a3 95 9d 7e c2 b6 92 a8  |...........~....|
00000160  9c 78 cb ad 88 c1 a3 7e  99 97 85 74 72 60 c9 cd  |.x.....~...tr`..|
00000170  c0 f8 fc ef ed f4 ed e3  ea e3 f6 f8 eb ec ee e1  |................|
00000180  fa f4 e1 fa f4 e1 fd f3  df fd f3 df f7 f3 e6 f7  |................|
00000190  f3 e6 f0 f1 ed f1 f2 ee  fb f2 e4 ff f8 ea ff ff  |................|
000001a0  ed f8 ee dc cc c2 aa ae  a4 8c ca be a4 fb ef d5  |................|
000001b0  e5 d7 c0 e0 d2 bb dc c9  ba d7 c4 b5 d3 ba 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 2f 00 00 00  |...........H/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I read the result and understand that the GRUB is on my Windown partition. So that, If I format the sda, I can never boot up into the Ubuntu again.
If I copy the GRUB into a USB and then paste it into its place after I do the formating, will it works?

---

### Post by sikander3786 on 2010-11-23
Reinstall Windows. Once completed that and you are able to boot into Windows successfully, follow this link for re-installing Grub2 from a Live CD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If your Bios gives you the choice to boot from the 2nd HDD, it is recommended that you install Grub to the MBR of sdb this time so if sometime later you've to reinstall Windows or your Grub setup gets messed up (somehow), you'll be able to boot the 2nd operating at least by only switching boot devices in Bios menu.

Your commands for installing Grub to sdb would look like this.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Note, for the 2nd command, it is just sdb and not sdb1.

Then boot Ubuntu from your HDD (you'll need to make Ubuntu HDD (sdb), your first boot device from Bios) and run this command to add Windows to the Grub menu.

```
sudo update-grub
```

Good Luck!

---

### Post by NerdyDavros on 2010-11-23
I just reinstalled my pc with XP the other day and it did remove my grub, but to fix it I did the following steps:[INDENT]1. Download Super Grub Disk 2 from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and burn to a CD, USB or Floppy (size of ISO=1.4MB).
2. Boot your computer with the Super Grub Disk 2 and select "Detect any OS", then select the Linux OS option.
3. Once your Ubuntu has booted, open up Synaptic Package Manager and search for "grub-pc".
4. Right click on "grub-pc" and select "Mark for Reinstallation", then click "Apply" and then click "Apply".
5. Once this package has reinstalled, eject the disk and restart your computer.
[/INDENT]If your computer has any trouble after reinstalling the package, just power down your pc for 10 seconds then start it back up again.

After trying this, I got my grub back and everything is running fine.

---

### Post by hoanggeneral on 2010-11-24
> **sikander3786 said:**
> Reinstall Windows. Once completed that and you are able to boot into Windows successfully, follow this link for re-installing Grub2 from a Live CD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")



It makes sense to me.
I'm so busy during these weeks since it is the weeks of final exam. I have to concentrate on my study
I am going to implement your solution as soon as I finish all my exams. I'll get back to you soon.
Thank for your help.

---

### Post by hoanggeneral on 2010-12-19
> **sikander3786 said:**
> Reinstall Windows. Once completed that and you are able to boot into Windows successfully, follow this link for re-installing Grub2 from a Live CD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If your Bios gives you the choice to boot from the 2nd HDD, it is recommended that you install Grub to the MBR of sdb this time so if sometime later you've to reinstall Windows or your Grub setup gets messed up (somehow), you'll be able to boot the 2nd operating at least by only switching boot devices in Bios menu.

Your commands for installing Grub to sdb would look like this.

```
sudo mount /dev/sdb1 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sdb
```Note, for the 2nd command, it is just sdb and not sdb1.

Then boot Ubuntu from your HDD (you'll need to make Ubuntu HDD (sdb), your first boot device from Bios) and run this command to add Windows to the Grub menu.

```
sudo update-grub
```Good Luck!

Successful completed :D.
Thank you very much for your help. The helping guide is detail ans easy to understand.

-----------------------------------------------------
problem SOLVED.

---

### Post by sikander3786 on 2010-12-19
> **hoanggeneral said:**
> Successful completed :D.
Thank you very much for your help. The helping guide is detail ans easy to understand.

-----------------------------------------------------
problem SOLVED.
You are Welcome :-)

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

