---
title: "Cannot load windows after installing linux"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by Gaeilgeoir on 2012-12-29
I am completely new to linux and need help to get me going. 

I  installed Window 8 pro on a laptop and ended up with two partitions for  C and D. I then shrank the C drive in Computer Management system -  storage- Disk Management. Then I rebooted to the DVD drive with a  Linux Mint iso. 

At the point where it asks "Something else" and you start partitioning then 
I chose to add a primary partition with 60000MB - location as beginning - use as ext4 and Mount point as /. 
I then added a logical partition with 6,000MB for swap - location as beginning. 
Finally  the remainder of the free space I gave to a logical partition -  location as beginning - use as ext4 and mount point as /home.

I  was just about to press install when I noticed a section underneath  refering to something like where to load linux. What linux had  preselected was an attached external usb drive.

I thought that had to be wrong so  I alterred the start partition to sda or sda1 I just cannot remember  which and then pressed install.

The end result is that when linux  finished installing and I went to reboot the option to boot to either  linux or Windows only the option to select Linux works. 
The  option for Windows actually says Windows SDA1. If I press the option  for windows then  I just get a black screen with a blinking curser in the top  left of the screen. 

I attach a printout of the RESULTS.txt file from Boot Info script.

                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 826137592 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 13 Maya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   720,771,071   720,052,224   7 NTFS / exFAT / HPFS
/dev/sda3         720,771,072   837,957,631   117,186,560  83 Linux
/dev/sda4         837,959,678   976,771,071   138,811,394   5 Extended
/dev/sda5         837,959,680   853,581,823    15,622,144  82 Linux swap / Solaris
/dev/sda6         853,583,872   976,771,071   123,187,200  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 1,953,458,175 1,953,456,128   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6C56F6F356F6BCC0                       ntfs       System Reserved
/dev/sda2        ACC4F8EAC4F8B822                       ntfs       
/dev/sda3        516506e6-0984-4bb8-8e05-377767357004   ext4       
/dev/sda5        14aceb0e-de9a-4a47-8b07-e60e4cb0a197   swap       
/dev/sda6        7e315305-12cc-42a0-ac93-cabdfc1dd44a   ext4       
/dev/sdd1        4E1AEA7B1AEA6007                       ntfs       My Passport
/dev/sr1                                                iso9660    Mobile Partner

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sdd1        /media/My Passport       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
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

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'LinuxMint, with Linux 3.2.0-23-generic' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=516506e6-0984-4bb8-8e05-377767357004 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'LinuxMint, with Linux 3.2.0-23-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=516506e6-0984-4bb8-8e05-377767357004 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 516506e6-0984-4bb8-8e05-377767357004
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 8 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 6C56F6F356F6BCC0
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=516506e6-0984-4bb8-8e05-377767357004 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=7e315305-12cc-42a0-ac93-cabdfc1dd44a /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=14aceb0e-de9a-4a47-8b07-e60e4cb0a197 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 343.842609406 = 369.198190592  boot/grub/core.img                             1
 343.842617035 = 369.198198784  boot/grub/grub.cfg                             1
 346.609886169 = 372.169531392  boot/initrd.img-3.2.0-23-generic               1
 349.827865601 = 375.624810496  boot/vmlinuz-3.2.0-23-generic                  1
 346.609886169 = 372.169531392  initrd.img                                     1
 349.827865601 = 375.624810496  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

I really need help to get the installation repaired and windows working.  I have posted here as there may be more users of ubuntu than linux mint and I understand that there are many similarities.  Thanks 

Gearóid
  			  		  		 			 				[Gaeilgeoir]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=103157") 			Level 1
[IMG]http://forums.linuxmint.com/images/ranks/1.gif[/IMG] **Posts:** 1**Joined:** Sat Dec 29, 2012 3:52 am**Location:** Ireland 				
[LIST]
[*]
[*]
[*]
[/LIST]

---

### Post by gnush on 2012-12-29
Redo everything and choose sda instead of sda1.

---

### Post by Gaeilgeoir on 2013-01-01
I tried reinstalling Linux, tried repair in Windows and FIXMBR in windows, but unfortunately to no effect. As there were no files on Windows or Linux I thought maybe it was better to start  all over again. So I rebooted the Linux iso disc in the DVD drive and chose "Try linux2 rather than "install". When Linux had fully loaded I used the partition application tool in Linux iso disk to delete all the partitions, put the Windows 8 disk in the DVD and went to restart. Eurika the windows disk restarted and I was able to reininstall. 

I went to manage disk in windows shrank the disk to create free space of 150gb on C and then put in the LInux iso disk in the DVD drive and restarted. I made sure that no external drive was connected this time and on install when i got to the part where you choose "something else" this time I made sure that Linux had identified SDA (and _**NOT**_ SDA1)as the place where the startup files would be. Then I allocated 60MB to Linux on a primary partition ext4 , 8 GB to swap and the balance to a logical partition /Home. Then I when linux had installed and you get the question to reboot or continue with configuration I chose reboot. The iso disk ejected on reboot and woohoo ! the boot option to boot windows 8 and linux worked. I finished off configuring Windows and then did the same for Linux. Many thanks to everyone who gave advice.

Regards,

Gearóid

---

