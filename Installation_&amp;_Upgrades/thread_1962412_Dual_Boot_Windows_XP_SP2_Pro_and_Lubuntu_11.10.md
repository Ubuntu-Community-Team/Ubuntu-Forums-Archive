---
title: "Dual Boot Windows XP SP2 Pro and Lubuntu 11.10"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by sleepers on 2012-04-21
Hi, I am sleepers and I'm from Indonesia. I have face several problem regarding installing dual boot WIN XP with Lubuntu. After following several thread with similar problem as me, it still no success.

I had an old PC that mainly used for browse internet and standard office work. It had been slow with it task and unresponsive even it used the lightest Windows OS, that is Win XP. So I browse the internet and heard that Lubuntu is great for old PC. My computer specs are :

Pentium 4 2.4 Ghz
256mb RAM DDR
80 GB Hardisk.

The CD-ROM drive is broken, so I had to install Lubuntu with USB disk. After learning how to make USB Lubuntu installer, I eager to install it at my PC. But first, to ensure nothing wrong I formated the PC and re-install Windows XP first. From what I heard, Windows OS must be installed first. Here is the breakdown :

1. Reinstall Windows XP with USB drive.
2. Formated 70GB to NTFS for Windows and let the rest unformated.
3. Install the Windows OS and after it restart without USB to see if nothing wrong with the installation. The PC can reboot and from its hardrive with no problem at all. Restart 3 times to make sure.
4. Boot the Lubuntu OS from USB drive. Partition it 3 with 
[INDENT]a. /dev/sda1 is Windows, nothing changed though[/INDENT]
[INDENT]b. /dev/sda2 is Lubuntu ROOT with ext4[/INDENT]
[INDENT]c. /dev/sda3 is Lubuntu swap[/INDENT]
[INDENT]d. /dev/sda5 is Lubuntu Home with ext4[/INDENT]
5. When the setup asked where I should install the bootloader, I install it at the /dev/sda (default option)
6. Installation run without problem, but after it finish it said "The installation is complete, please click restart now button"
7. I clicked it and wait for half an hour, but it still not restarting. In my screen it said "Waiting for all process to be terminated". After waiting for an hour, patience is lost, I press the power button :p
8. After that, the bootloader show its menu with top 2 is lubuntu and number 3 and 4 for memory test.
9 I picked first option and it load to lubuntu without any problem and LOVE IT !
10. After that, I reboot the computer and this time choose option 5 to load Windows XP from /dev/sda1
11. This time it just blank black monitor.

After that, I tried to boot windows from my USB drive, not from my hardrive. It works and I can get to my Windows Desktop. It seems only want to reboot Windows from my USB Drive, but if I boot it from my Hardisk, it just black blank screen.

Searching and lurking in the forum, some thread suggest that I run windows recovery console command and run fixmbr and fixboot command. But still no sucess.

I opened Linux terminal and typed "sudo grub -update", it detected my Windows OS at /dev/sda1, updated it config file, but i still cant boot into Windows from my Hardisk.

I opened BOOT.INI file from WIndows, and the only OS it boot is Windows.

Can someone tell me what did I do wrong ? Please don't tell to just install Lubuntu as my PC only OS. Because that not solve the problem and my family still not how great is Lubuntu.

Any help will be appreciated :)

---

### Post by mastablasta on 2012-04-21
> **sleepers said:**
> 
Searching and lurking in the forum, some thread suggest that I run windows recovery console command and run fixmbr and fixboot command. But still no sucess.

I opened Linux terminal and typed "sudo grub -update", it detected my Windows OS at /dev/sda1, updated it config file, but i still cant boot into Windows from my Hardisk.



after typing the fixmbr command (which you need to put into windows repair console not ubuntu) have you tried botoing the disk? and then if it boots ok do the grub update. it should work.

make sure the boot order is ok in BIOS.

also if you can get your hands (even on used) DDR ram stick (preferably a 1GB one) it would be great.

edit you can also try running bootinfoscript in Lubuntu so people can help you more easily: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sleepers on 2012-04-21
> **mastablasta said:**
> after typing the fixmbr command (which you need to put into windows repair console not ubuntu) have you tried botoing the disk? and then if it boots ok do the grub update. it should work.

make sure the boot order is ok in BIOS.

also if you can get your hands (even on used) DDR ram stick (preferably a 1GB one) it would be great.

edit you can also try running bootinfoscript in Lubuntu so people can help you more easily: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I will try your suggestion and give you reply after it had done. Thank you.

---

### Post by sleepers on 2012-04-21
@Mastablasta

I had doublechecked the boot priority order at the BIOS. It still point to Hardisk, and the second one is CD-ROM. In my knowledge, this is correct. 

I had redo the fixmbr and fixboot command at WinXP recory console and still cant boot at WIN XP.

About the RAM, even though it is 256mb it still run flawlessly with Lubuntu. Besides 1GB DDR RAM is about twice the price of 1GB DDR3 RAM even though used. At least, in my country Indonesia :(

And the result text are

> 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   143,347,994   143,347,932   7 NTFS / exFAT / HPFS
/dev/sda2         143,349,760   151,162,879     7,813,120  83 Linux
/dev/sda3         151,162,880   151,912,447       749,568  82 Linux swap / Solaris
/dev/sda4         151,914,494   160,086,015     8,171,522   5 Extended
/dev/sda5         151,914,496   160,086,015     8,171,520  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        82F42F5AF42F5029                       ntfs       
/dev/sda2        7bd7a546-5413-4893-a57b-f35868cdf94e   ext4       
/dev/sda3        56801764-d8fd-49e9-bb35-191e336deef7   swap       
/dev/sda5        d18074cc-b0df-44a2-bcbf-87b748b283ca   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader]
Timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows" /noexecute=optin /fastdetect--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7bd7a546-5413-4893-a57b-f35868cdf94e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7bd7a546-5413-4893-a57b-f35868cdf94e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7bd7a546-5413-4893-a57b-f35868cdf94e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82F42F5AF42F5029
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
UUID=7bd7a546-5413-4893-a57b-f35868cdf94e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d18074cc-b0df-44a2-bcbf-87b748b283ca /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=56801764-d8fd-49e9-bb35-191e336deef7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  8f 5e c2 98 68 af e1 8d  b4 44 06 b1 1a 02 45 97  |.^..h....D....E.|
00000010  41 82 08 b7 bc 96 2f 2d  20 47 7e f6 da 6a 07 13  |A...../- G~..j..|
00000020  fb c9 ab a1 d4 a9 af 95  f8 b8 ab 47 20 a5 24 05  |...........G .$.|
00000030  fa e8 9e b2 c2 77 92 e0  bb 21 fe b3 c8 b0 5e 4e  |.....w...!....^N|
00000040  36 85 de 0e 7d 99 bf ea  98 bf ad fc 24 ec d5 15  |6...}.......$...|
00000050  00 0f 32 53 aa 3e a6 92  36 4f ff 22 7c fd 77 b1  |..2S.>..6O."|.w.|
00000060  cc dc 20 65 80 77 d5 df  4b b6 c5 ee 9f 40 32 7c  |.. e.w..K....@2||
00000070  81 27 6e 57 c4 aa e5 dd  fa e0 8f 61 ba cd de bd  |.'nW.......a....|
00000080  9e b3 8f ab 52 a8 89 a5  c1 34 d8 0c 71 d9 90 ce  |....R....4..q...|
00000090  1c a8 71 15 26 67 da f3  30 ff 74 84 6e ae 8a 35  |..q.&g..0.t.n..5|
000000a0  05 fe 1d 62 06 3f b3 f6  3b c5 99 6c 55 81 d3 24  |...b.?..;..lU..$|
000000b0  f3 01 75 c3 49 5f a4 1f  ce 66 eb 1e 1d c7 35 ef  |..u.I_...f....5.|
000000c0  62 c5 68 ac 19 73 16 c8  d4 f9 e3 4d fe 91 04 b3  |b.h..s.....M....|
000000d0  b4 3f 2b 45 fb ca 3a e8  6e 7c 65 51 09 c4 0f d2  |.?+E..:.n|eQ....|
000000e0  c8 6f 38 a9 7c 45 10 39  8f 6d da e6 6d 28 fa f6  |.o8.|E.9.m..m(..|
000000f0  24 f6 dc 6b 85 be c2 f3  6a 50 90 2d 2d 58 03 12  |$..k....jP.--X..|
00000100  f9 9d e4 38 11 81 56 48  d7 cf 22 27 86 ab 91 87  |...8..VH.."'....|
00000110  47 6f 03 2d 04 5f c6 06  fd e4 47 b6 92 c1 e6 22  |Go.-._....G...."|
00000120  68 50 5d cf 2d 90 75 1a  84 c6 ca 53 0d 3f 01 e7  |hP].-.u....S.?..|
00000130  39 04 42 8a d9 bc bf 00  dc e8 be cd be 57 46 7f  |9.B..........WF.|
00000140  76 57 06 5e 30 6e 75 b7  d6 21 78 9a f1 a1 6e a4  |vW.^0nu..!x...n.|
00000150  75 87 ba 57 a0 bf 88 15  d5 89 d6 a9 bb b0 04 b0  |u..W............|
00000160  27 94 dc 3e 09 a3 9c fe  7c 06 22 70 81 b5 49 b7  |'..>....|."p..I.|
00000170  a6 e4 30 d4 ac 61 c1 8a  c4 1c 2a 35 11 c2 2f c5  |..0..a....*5../.|
00000180  d0 5f fd f9 f7 ec 7f 6d  22 ad 61 6c e7 ad ee f4  |._.....m".al....|
00000190  cf 99 ba d5 1d ab 87 dd  b3 1b 70 21 6a 54 be 95  |..........p!jT..|
000001a0  d1 f7 e4 d5 1e 37 70 2b  11 f6 b0 97 42 a8 72 42  |.....7p+....B.rB|
000001b0  99 47 46 76 5f 52 10 c1  a6 d9 d5 9d d9 9e 00 fe  |.GFv_R..........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 7c 00 00 00  |............|...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


---

### Post by oldfred on 2012-04-21
Boot script looks normal to me. Lubuntu found the XP install so boot files are found ok and script shows they are there. 

Your fixBoot should have fixed any issues with NTFS partition boot sector (PBR or BS). 

When you ran fixMBR that should have you booting directly into Windows. Did that work? Grub can only chain load to a working Windows.

Often chkdsk can be required after a resize of a NTFS partition. Did you do that. Sometimes you have to run it multiple times as it only fixes one issue on each run.

If you do run the fixMBR, then you do have to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by km3952 on 2012-04-24
Windows XP only allows 4 changes to the system before it has to be re installed & verified/registered again with MS.

This is likely the cause of your blank screen when attempting to boot into Windows XP.

Only if you have a manufacturers re install disk, do you not have to re register.

Also, if you don't re register, it will die after 30 days. This was the first Windows to do this, to stop illegal copying.

---

### Post by oldfred on 2012-04-24
I never had to reinstall XP, but did have to re-register when I swapped motherboards, rest of system was identical, but it know something changed and wanted to check with Microsoft to see if it was ok for me to keep using it.

---

### Post by sleepers on 2012-04-25
Sorry for the late response, had been busy.

@oldfred
I had done the the fixmbr and fixboot command from the recovery console which i booted from an usb. It still didn't work, and I had done as you suggested to run "chkdsk c: /r" command for 3 times and still no success. The strange thing is I can only boot to windows if I used the Windows Bootloader and boot Windows from my USB. If I used the Grub loader and boot Windows from hardisk, it didn't load. Just black screen with some broken text like "@^#&AS())SU**DAS".

The XP installer is pre cracked and I don't need to register at all.

@km3952
I'm well aware of that, but I don't need to register ever :)

I will try to reinstall grub2 loader as oldfred suggested and will notify you all if anything changes :)

---

### Post by techsupport on 2012-04-25
I re-read this a couple of times.

Why are you installing Windows as a dual boot?

Why don't you just install Ubuntu, use the entire drive for Ubuntu, and install Windows in Virtualbox inside Ubuntu?  That should work. 

Your solution would be to install windows virtually in Virtualbox.

Lubuntu seems to be working great, so just install Virtualbox:

Virtualbox is near the bottom of this list to install from PPA:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

If you don't need to have a dual, then don't dual boot and just install Windows inside Ubuntu Virutalbox.

Hopefully that makes sense?



> **sleepers said:**
> Sorry for the late response, had been busy.

@oldfred
I had done the the fixmbr and fixboot command from the recovery console which i booted from an usb. It still didn't work, and I had done as you suggested to run "chkdsk c: /r" command for 3 times and still no success. The strange thing is I can only boot to windows if I used the Windows Bootloader and boot Windows from my USB. If I used the Grub loader and boot Windows from hardisk, it didn't load. Just black screen with some broken text like "@^#&AS())SU**DAS".

The XP installer is pre cracked and I don't need to register at all.

@km3952
I'm well aware of that, but I don't need to register ever :)

I will try to reinstall grub2 loader as oldfred suggested and will notify you all if anything changes :)

---

### Post by mastablasta on 2012-04-25
> **techsupport said:**
> I re-read this a couple of times.
 

Obviously you didnt' start at the beignning.
 
> 256mb RAM DDR

 
 
that preety much throws out any virtualisation out the window....
 
it's barely enough to run one OS let alone do any virtualisaiton.
now thisi was insreased by 2Gb ram then it would indeed be better to have virtualbox install.

---

### Post by sleepers on 2012-05-03
> **techsupport said:**
> I re-read this a couple of times.

Why are you installing Windows as a dual boot?

Why don't you just install Ubuntu, use the entire drive for Ubuntu, and install Windows in Virtualbox inside Ubuntu?  That should work. 

Your solution would be to install windows virtually in Virtualbox.

Lubuntu seems to be working great, so just install Virtualbox:

Virtualbox is near the bottom of this list to install from PPA:

[http://*********************.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://*********************.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

If you don't need to have a dual, then don't dual boot and just install Windows inside Ubuntu Virutalbox.

Hopefully that makes sense?

First of all, this PC is public family computer that mainly used by my mother for browse the web, email and document processing. With her age and windows fanatics, I'm sure you know why I had to dual boot. She would never agree to be a Linux PC. And virtual box is out of the question.

Second, it said it can be done. But I had little success so far. 

I suspicious that it a bad windows CD due. But consider this thread solved. I had give up about dual boot. I had bought my mother another laptop and I'm gonna used this computer mainly for Linux experiment :) Thank you for all your support so far :D

---

### Post by mips on 2012-05-03
Try leaving 2MB of free space at the beginning of the hard drive before creating the first partition and others. I've experienced a similar problem before and this fixed it for me.

---

