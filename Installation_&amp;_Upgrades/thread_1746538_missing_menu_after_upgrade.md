---
title: "missing menu after upgrade"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by eddiewar on 2011-05-01
Missing LogIn Menu

I have a computer on which I installed both Ubuntu and Windows XP and was able originally at startup to choose which OS to load. Recently I decided to upgrade the Ubuntu from 10.10 to 11.04 and now the startup menu does not load and I am unable to access WindowsXP.
I have to state that I am a COMPLETE NEWBIE so hopefully if anyone answers this question they will reply in easily understood instructions. 
If it wasn't for the fact that I have a family history program in XP I would just delete the partition and start over.
Although I downloaded and installed Startup manager and it did show the XP system it didn't provide the startup menu..........
I would be very grateful for someone's help - please

---

### Post by garvinrick4 on 2011-05-01
> **eddiewar said:**
> Missing LogIn Menu
 
I have a computer on which I installed both Ubuntu and Windows XP and was able originally at startup to choose which OS to load. Recently I decided to upgrade the Ubuntu from 10.10 to 11.04 and now the startup menu does not load and I am unable to access WindowsXP.
I have to state that I am a COMPLETE NEWBIE so hopefully if anyone answers this question they will reply in easily understood instructions. 
If it wasn't for the fact that I have a family history program in XP I would just delete the partition and start over.
Although I downloaded and installed Startup manager and it did show the XP system it didn't provide the startup menu..........
I would be very grateful for someone's help - please
First try, open a terminal and:
```
sudo update-grub
```
See if that does it and report back, there is a lot of ways and users to get you bootable.

---

### Post by eddiewar on 2011-05-01
> **garvinrick4 said:**
> First try, open a terminal and:
```
sudo update-grub
```
See if that does it and report back, there is a lot of ways and users to get you bootable.

Thanks but that unfortunately did not work :-)

The PC boots and the first screen that appears is autologin screen for 10.10 and then this changes and becomes the 11.04 desktop. still no option to load XP.

---

### Post by garvinrick4 on 2011-05-02
#Hold down shift key while it is booting and will show boot menu entrys.
#Also you can run this in a terminal and will show menuentrys:
```
 
grep menuentry /boot/grub/grub.cfg

```
##Normally it boots straight into a operating system when only one available.

---

### Post by eddiewar on 2011-05-02
Thanks for your reply - appreciated.

However your suggestions did not produce any new results - holding the shift key had no effect at all on the bootup and the "grep menuentry..........." just produced the text of the menu that SHOULD appear at bootup.

What would be the possible result if I just attempt to re-install 10.1 from a live CD?

---

### Post by Dutch70 on 2011-05-02
> **eddiewar said:**
> What would be the possible result if I just attempt to re-install 10.1 from a live CD?

Well, If you choose the partitions that you want to install to manually & select the same ones, it should be fine. Otherwise, you may end up with 2 installs and even bigger problems.

Or...We can take a look at your boot info script to try & see why it's not booting.

From the live cd, run the following command in a terminal.*(copy&paste)*
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

That should put the boot info script in your downloads folder. Cut & Paste it to your desktop, and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info between code tags using the "#" symbol in the tool bar of your next post.

 Again, to put it between code tags, just click the # symbol in the tool bar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

### Post by eddiewar on 2011-05-03
Thanks for your help = hopefully this is what you are asking for :-)

> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cbdc4.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,124,094    78,124,032   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   393,691,135   393,689,088  83 Linux
/dev/sdb2         393,693,182   398,295,039     4,601,858   5 Extended
/dev/sdb5         393,693,184   398,295,039     4,601,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7204447C04444577                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9757a38a-2057-4758-8f47-e60a4605a118   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4293fd01-7e22-42bc-a55a-677b57a81dfc   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
set default="6"
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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro  splash vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro  splash vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 7204447C04444577
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
UUID=4293fd01-7e22-42bc-a55a-677b57a81dfc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-28-generic
    .6GB: boot/initrd.img-2.6.38-8-generic
  94.6GB: boot/vmlinuz-2.6.35-28-generic
   1.9GB: boot/vmlinuz-2.6.38-8-generic
    .6GB: initrd.img
    .6GB: initrd.img.old
   1.9GB: vmlinuz
  94.6GB: vmlinuz.old

---

### Post by Dutch70 on 2011-05-04
Nope!...That is quote tags...[QUOTE][ /QUOTE]

This is code tags...[CODE][ /CODE]

---

### Post by eddiewar on 2011-05-09
**[SIZE="3"]Hopefully I got it right this time :-)[/SIZE]**

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cbdc4.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,124,094    78,124,032   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   393,691,135   393,689,088  83 Linux
/dev/sdb2         393,693,182   398,295,039     4,601,858   5 Extended
/dev/sdb5         393,693,184   398,295,039     4,601,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7204447C04444577                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9757a38a-2057-4758-8f47-e60a4605a118   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4293fd01-7e22-42bc-a55a-677b57a81dfc   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
set default="6"
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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro  splash vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro  splash vga=795  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9757a38a-2057-4758-8f47-e60a4605a118 ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 9757a38a-2057-4758-8f47-e60a4605a118
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 7204447C04444577
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
UUID=4293fd01-7e22-42bc-a55a-677b57a81dfc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-28-generic
    .6GB: boot/initrd.img-2.6.38-8-generic
  94.6GB: boot/vmlinuz-2.6.35-28-generic
   1.9GB: boot/vmlinuz-2.6.38-8-generic
    .6GB: initrd.img
    .6GB: initrd.img.old
   1.9GB: vmlinuz
  94.6GB: vmlinuz.old
```

---

### Post by Hedgehog1 on 2011-05-10
Based on the second script output you have posted, you have a mix of boot loader remnants on your 1st hard drive:

```
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for **cbdc4**.
```

This should be looking for **/boot/grub** instead of **cbdc4**.

Please download the Natty/11.04 ISO and create a LiveCD (or a LiveUSB) with it.

The boot from the LiveCD/LiveUSB, select 'TRY'.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**b1** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

This will (hopefully) reinstall grub properly so you can use both XP and Ubuntu again.


***The Hedge***

:KS

---

### Post by eddiewar on 2011-05-10
Thanks for your suggestions BUT I am sorry to say it didn't change anything.

I carried out your instructions (twice) and each time I received the message "installation finished no errors reported" I completely disconnected the PC from the power before rebooting.
 
Sooooooo it is now up to you guys if you want to continue with trying to solve this - if not I will just reformat and install some other Ubunutu distro.

Regards and again thanks

Edward

---

### Post by Dutch70 on 2011-05-12
If you haven't reinstalled yet, It think the commands you want to run from the live cd/usb are...
```
sudo mount /dev/sdb1 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

That is going to install the boot loader into the MBR of sdb, so you may want to see if someone else has anything to add to this. 

I can tell you that I have 2 hdd's and have the boot loader installed to both. That way if I take one out, I can still boot, but I'll leave that up to you.

---

### Post by eddiewar on 2011-05-14
> **Dutch70 said:**
> If you haven't reinstalled yet, It think the commands you want to run from the live cd/usb are...
```
sudo mount /dev/sdb1 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

That is going to install the boot loader into the MBR of sdb, so you may want to see if someone else has anything to add to this. 

I can tell you that I have 2 hdd's and have the boot loader installed to both. That way if I take one out, I can still boot, but I'll leave that up to you.

Thanks Dutch --

BUT I am sorry to say there has been no change in my situation - still cannot access XP.

I did notice that your instructions were just slightly different to Hedgehog's - you stated ......./dev/sda and he gave ...../dev/sdb but after carrying out both your instructions (very carefully) I still received the same negative result.

My sincere thanks for both of you for trying to help - looks as though I am stuck with this.

Edward

---

### Post by Dutch70 on 2011-05-14
Sorry to hear that Edward. Please refer to post#6 & repost a new boot info script since you've made changes.

---

### Post by eddiewar on 2011-05-15
> **Dutch70 said:**
> Sorry to hear that Edward. Please refer to post#6 & repost a new boot info script since you've made changes.

Thanks Dutch -- BUT this time I was not able to download the bootinfoscript file from sourceforge. Tried three times but received the same result "error 404 ....not found". I cannot understand because this command worked OK the first time you posted it.

Edward

---

### Post by Dutch70 on 2011-05-15
If you had/have an Internet connection, the server may have been down. I just tried it myself & it worked fine.

---

### Post by eddiewar on 2011-05-16
> **Dutch70 said:**
> If you had/have an Internet connection, the server may have been down. I just tried it myself & it worked fine.

Thanks Dutch --

BUT I seem to be digging a deeper hole somehow :-)

I completely shutdown and disconnected the computer before booting with the live CD. When I chose the "Try Ubuntu" option, after some time I received the message "fixing recusive fault but reboot is needed". I could not reboot so had to again completely disconnect the PC.

So now I am unable to boot with the live CD..........

---

### Post by Dutch70 on 2011-05-17
Wow, maybe your cd has gotten dirty or scratched, because it doesn't use your hdd when you're booting from the cd.

---

### Post by eddiewar on 2011-05-18
> **Dutch70 said:**
> Wow, maybe your cd has gotten dirty or scratched, because it doesn't use your hdd when you're booting from the cd.

Well I have finally managed to download the boot_info_script file and place it on the desktop HOWEVER when I run the command sudo bash ~/desktop/boot_info_script*.sh I receive the error message "no such file or directory"

Any further suggestions or have I reached the end of the road?

---

### Post by Dutch70 on 2011-05-18
Well, if you can reinstall without losing anything, that's usually always the best option. I don't know for sure that getting that boot script will tell us anything. Upgrades are just never the way to go IMHO. 

You can also try "renewing your installation" I've never tried it so, I can't tell you how safe it is. This video will show you how.
[[COLOR="RoyalBlue"]http://www.youtube.com/watch?v=QGnsYuWS0xY[/COLOR]]("http://www.youtube.com/watch?v=QGnsYuWS0xY")
You can even use that to go back to an older version. 
I recommend having a separate /home partition so you can always reinstall without losing your data or settings.

As for the boot script, are you copying & pasting the command from my previous post? If not, definitely try that if you want to continue to try & fix it.

---

