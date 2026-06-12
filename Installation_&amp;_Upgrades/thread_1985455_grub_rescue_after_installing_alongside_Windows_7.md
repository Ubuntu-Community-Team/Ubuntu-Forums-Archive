---
title: "grub rescue after installing alongside Windows 7"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by ollnixon on 2012-05-23
I installed Ubuntu 12.04 alongside Windows 7, all seemed to go well until the reboot where I received a grub rescue prompt.

Paste from boot repair (before running): [http://paste.ubuntu.com/1002757/](http://paste.ubuntu.com/1002757/)

I have since run boot-repair a number of times from the live cd (the last time was the 1 click repair) and it is currently looking like this: [http://paste.ubuntu.com/1002884/](http://paste.ubuntu.com/1002884/)

When I boot, I receive "Missing operating system". Any help would be much appreciated, it's driving me crazy!

---

### Post by nipunshakya on 2012-05-23
Can you boot to your windows?? If yes, boot to it once, and properly shutdown..... maybe not to hibernate it...??

After a proper shutdown, boot to Live mode and try to reinstall grub
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

the following thread might also help
[http://ubuntuforums.org/showthread.php?t=1976482&page=2](http://ubuntuforums.org/showthread.php?t=1976482&page=2)

See post #17 of that thread... maybe that might help a bit...


Happy Linuxing

---

### Post by lostinspace2011 on 2012-05-23
The only way I can boot windows at the moment is via efi using the "Windows Boot Manager" option. 

Grub seems to be installed on /dev/sdc4 (/boot)
```

root@panda:~# grub-probe -t device /boot/grub
/dev/sdc4

```However during the ubuntu installation I opted to install the boot record on the disk (/dev/sdc) rather then any one of its partitions.

---

### Post by ollnixon on 2012-05-23
I have followed the instructions from the two addresses you mentioned. Grub has been purged and re-installed on sda. I now get:

```
error: file not found.
grub rescue>
```

The current boot info script is here: [http://paste.ubuntu.com/1003112/](http://paste.ubuntu.com/1003112/)

---

### Post by nipunshakya on 2012-05-23
@lostinspace2011 : The bios always tries to find a boot loader and the various files on which the boot loader depends on the first disk in the machine. If that's the disk that was replaced, then loading grub will fail. Same thing might have happened to u as u installed it to a USB Drive. Now, you might want to look at the following links first:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://www.sysresccd.org/Sysresccd-Partitioning-EN-Repairing-a-damaged-Grub](http://www.sysresccd.org/Sysresccd-Partitioning-EN-Repairing-a-damaged-Grub)

Hope u might get a solution out of it..

Happy Linuxing

---

### Post by oldfred on 2012-05-23
Is this an older computer with the BIOS boot limit of 137GB or do you have BIOS in IDE mode that emulates that? 

You should change to AHCI mode, but if Windows 7 does not have the drivers installed it has to have those installed first to keep Windows 7 working.

Part of grub/kernel boot files are above 137GB and the rest are below it.

Another way is just to shrink / (root) so that all of / is inside the 137GB limit. You can use the rest of the drive as /home, /data or a shared NTFS partition for data you might want in both Windows & Linux.

---

### Post by ollnixon on 2012-05-23
The machine is only 18mths old, it is a Dell E6410. 

Within the BIOS:
[LIST]
[*]boot list option is set to legacy (int HDD, USB, CD) (as opposed to UEFI)
[*]SATA operation is AHCI
[/LIST]

---

### Post by oldfred on 2012-05-23
You can try manually booting.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hd0,5)
      linux /vmlinuz root=/dev/sda5 ro
      initrd /initrd.img
      boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If you want to experiment, just shrink sda5 so it is totally inside the 137GB limit. If it works then you can use rest of drive for shared data or /home.

---

### Post by darkod on 2012-05-23
> **oldfred said:**
> You can try manually booting.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hd0,5)
      linux /vmlinuz root=/dev/sda5 ro
      [COLOR=Red]initrd /initrd[/COLOR]
      boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If you want to experiment, just shrink sda5 so it is totally inside the 137GB limit. If it works then you can use rest of drive for shared data or /home.

Shouldn't that be:
initrd /initrd.img

Because only /initrd doesn't exist. Or the command can find it despite that?

---

### Post by oldfred on 2012-05-23
Darko is correct. I will edit original post just for posterity and if someone sees post without reading rest of the thread.

---

### Post by ollnixon on 2012-05-23
I get the error "linux is not a valid command". The machine has previously had Fedora installed (though it creates a slightly different partition layout).

At the rescue prompt, if I "ls (hd0,5)/" The boot folder exists but not boot/grub!

Latest boot info: [http://paste.ubuntu.com/1003547/](http://paste.ubuntu.com/1003547/)

---

### Post by oldfred on 2012-05-23
Is your computer promoting the flash drive to sda. You install showed hd1 but correct UUID. Script when run showed sda or hd0??

---

### Post by YannBuntu on 2012-05-23
**@oldfred:** FYI ollnixon also contacted me directly by email, i advised to use a separate /boot. He told he could solve his problem.

**@ollnixon:** please indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1").

---

### Post by ollnixon on 2012-05-24
Thanks everyone for the help.

Steps I used to fix it:
[LIST=1]
[*]Remove the Ubuntu partitions
[*]Create a new sda3 partition (1GB, ext4, primary, /boot)
[*]Create a swap and / partition in the remaining space
[*]Install Ubuntu to those partitions
[*]It all works perfectly
[/LIST]

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   153,602,047   153,395,200   7 NTFS / exFAT / HPFS
/dev/sda3         153,613,530   155,557,394     1,943,865  83 Linux
/dev/sda4         155,557,456   500,117,503   344,560,048   5 Extended
/dev/sda5         155,557,458   488,392,064   332,834,607  83 Linux
/dev/sda6         488,392,704   500,117,503    11,724,800  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mmcblk0p1   3535-3236                              vfat       
/dev/sda1        C4AAD7EFAAD7DBCC                       ntfs       System Reserved
/dev/sda2        D8F2E4D6F2E4BA40                       ntfs       
/dev/sda3        98a2d872-f115-42ef-9dcc-91b977aee503   ext4       
/dev/sda5        482e7d3b-a404-47ce-b960-6f3759a86c5f   ext4       
/dev/sda6        3f358721-13fc-4d20-8725-529fae640f6c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mmcblk0p1   /media/3535-3236         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda3        /boot                    ext4       (rw)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)


============================= sda3/grub/grub.cfg: ==============================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 482e7d3b-a404-47ce-b960-6f3759a86c5f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos3)'
  search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
  set locale_dir=($root)/grub/locale
  set lang=en_GB
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
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	linux	/vmlinuz-3.2.0-24-generic root=UUID=482e7d3b-a404-47ce-b960-6f3759a86c5f ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/vmlinuz-3.2.0-24-generic root=UUID=482e7d3b-a404-47ce-b960-6f3759a86c5f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	linux	/vmlinuz-3.2.0-23-generic root=UUID=482e7d3b-a404-47ce-b960-6f3759a86c5f ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/vmlinuz-3.2.0-23-generic root=UUID=482e7d3b-a404-47ce-b960-6f3759a86c5f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 98a2d872-f115-42ef-9dcc-91b977aee503
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root C4AAD7EFAAD7DBCC
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root D8F2E4D6F2E4BA40
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

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    2
               =                initrd.img-3.2.0-24-generic                    2
               =                vmlinuz-3.2.0-23-generic                       1
               =                vmlinuz-3.2.0-24-generic                       1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=482e7d3b-a404-47ce-b960-6f3759a86c5f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=98a2d872-f115-42ef-9dcc-91b977aee503 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=3f358721-13fc-4d20-8725-529fae640f6c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  66 61 6c 73 65 28 29 22  2f 3e 0a 09 09 3c 78 73  |false()"/>...<xs|
00000010  6c 3a 70 61 72 61 6d 20  6e 61 6d 65 3d 22 6e 6f  |l:param name="no|
00000020  44 69 76 42 65 66 6f 72  65 22 20 73 65 6c 65 63  |DivBefore" selec|
00000030  74 3d 22 74 72 75 65 28  29 22 2f 3e 0a 09 09 3c  |t="true()"/>...<|
00000040  78 73 6c 3a 70 61 72 61  6d 20 6e 61 6d 65 3d 22  |xsl:param name="|
00000050  6c 65 66 74 50 6f 73 69  74 69 6f 6e 22 20 2f 3e  |leftPosition" />|
00000060  0a 09 09 3c 78 73 6c 3a  70 61 72 61 6d 20 6e 61  |...<xsl:param na|
00000070  6d 65 3d 22 70 61 72 65  6e 74 4d 61 72 67 69 6e  |me="parentMargin|
00000080  4c 65 66 74 22 20 2f 3e  0a 09 09 3c 78 73 6c 3a  |Left" />...<xsl:|
00000090  70 61 72 61 6d 20 6e 61  6d 65 3d 22 66 72 61 6d  |param name="fram|
000000a0  65 41 6c 69 67 6e 65 64  54 6f 50 61 72 61 67 72  |eAlignedToParagr|
000000b0  61 70 68 57 69 74 68 53  76 67 59 22 20 2f 3e 0a  |aphWithSvgY" />.|
000000c0  0a 09 09 3c 78 73 6c 3a  61 70 70 6c 79 2d 74 65  |...<xsl:apply-te|
000000d0  6d 70 6c 61 74 65 73 20  73 65 6c 65 63 74 3d 22  |mplates select="|
000000e0  66 6f 6c 6c 6f 77 69 6e  67 2d 73 69 62 6c 69 6e  |following-siblin|
000000f0  67 3a 3a 6e 6f 64 65 28  29 5b 31 5d 22 20 6d 6f  |g::node()[1]" mo|
00000100  64 65 3d 22 66 72 61 6d  65 46 6c 6f 61 74 69 6e  |de="frameFloatin|
00000110  67 22 3e 0a 09 09 09 3c  78 73 6c 3a 77 69 74 68  |g">....<xsl:with|
00000120  2d 70 61 72 61 6d 20 6e  61 6d 65 3d 22 67 6c 6f  |-param name="glo|
00000130  62 61 6c 44 61 74 61 22  20 73 65 6c 65 63 74 3d  |balData" select=|
00000140  22 24 67 6c 6f 62 61 6c  44 61 74 61 22 2f 3e 0a  |"$globalData"/>.|
00000150  09 09 09 3c 78 73 6c 3a  77 69 74 68 2d 70 61 72  |...<xsl:with-par|
00000160  61 6d 20 6e 61 6d 65 3d  22 70 72 65 76 69 6f 75  |am name="previou|
00000170  73 46 72 61 6d 65 57 69  64 74 68 73 22 20 73 65  |sFrameWidths" se|
00000180  6c 65 63 74 3d 22 24 70  72 65 76 69 6f 75 73 46  |lect="$previousF|
00000190  72 61 6d 65 57 69 64 74  68 73 22 2f 3e 0a 09 09  |rameWidths"/>...|
000001a0  09 3c 78 73 6c 3a 77 69  74 68 2d 70 61 72 61 6d  |.<xsl:with-param|
000001b0  20 6e 61 6d 65 3d 22 70  61 72 65 6e 74 4d 00 fe  | name="parentM..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 2f a7 d6 13 00 fe  |........../.....|
000001d0  ff ff 05 fe ff ff 31 a7  d6 13 7f ea b2 00 00 00  |......1.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
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

### Post by oldfred on 2012-05-24
Glad that worked.

There seems to be some new systems or  a BIOS setting that acts like the odl 137GB limit. Either a /boot or small / (root) and separate /home then do work if fully inside the first 137GB.

---

### Post by YannBuntu on 2012-05-24
**@oldfred:** in ollnixon's case, i wonder if the BIOS could have read the /boot if it had been on a logical partition... ;)

**@ollnixon:** thanks for the feedback!

---

### Post by oldfred on 2012-05-24
It should not make a difference whether logical or primary, it should just be location on drive. I still think it is a BIOS setting, but cannot prove it as some report BIOS settings that seem to be correct and still have the issue.

---

