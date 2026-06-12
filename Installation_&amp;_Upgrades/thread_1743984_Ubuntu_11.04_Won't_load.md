---
title: "Ubuntu 11.04 Won't load"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Paul41 on 2011-04-29
I just did a clean install of 11.04. Now when I try to boot the machine I get the following error:

> error: no such device
error: no such disk
error: you need to load the kernel first

Then I am taken to the Grub menu. Selecting anything from the Grub menu brings this error back up.

So now I'm stuck with a computer that won't work. Any ideas how to fix this?

---

### Post by cariboo on 2011-04-30
Grub wasn't installed properly, bott from the live cd and once at the desktop, open a terminal and type the following commands:

[LIST=1]
[*]sudo mount /dev/sdxX /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

where /dev/sdxX = your ubuntu partition, if you don't know what the device label for the partition is type:

```
sudo fdisk -l
```

to find out what partition Ubuntu is using.

Once you have entered the above commands type:

```
grub-install /dev/sda
```

then type:

```
update-grub
```

running the above command you should see a list of your installed operating systems. Once the update-grub command has finished, press Ctrl-D twice, and reboot.

---

### Post by Paul41 on 2011-04-30
I tried this and now I just get a flashing cursor on the upper left corner with a black screen. It's not even trying to boot and I don't ever get the grub menu.

---

### Post by Paul41 on 2011-04-30
I tried to re-install using a new CD and got the same problem. I tried the grub commands again and now it is a endless loop of loading the BIOS splash screen then to the black screen with the flashing cursor. It just keeps looping back and forth between those two.screens.

---

### Post by Rubi1200 on 2011-04-30
Please do the following:

1. post the specifications, especially RAM and graphics card

2. run the boot script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Paul41 on 2011-04-30
4 gb of RAM
Video Card: VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 21319993 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1    29,296,875    29,296,875  83 Linux
/dev/sda2          29,296,876    37,013,671     7,716,796  82 Linux swap / Solaris
/dev/sda3          37,013,672   625,142,447   588,128,776  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fd7a6982-10bb-46be-9b79-59bdb253f0a1   ext4                                     
/dev/sda2        3d13dcef-1b8c-41d9-bada-a585b4022a2d   swap                                     
/dev/sda3        2a9730de-c3a1-4841-8b24-cedd9df04a0c   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fd7a6982-10bb-46be-9b79-59bdb253f0a1 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fd7a6982-10bb-46be-9b79-59bdb253f0a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd7a6982-10bb-46be-9b79-59bdb253f0a1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sda1 during installation
UUID=fd7a6982-10bb-46be-9b79-59bdb253f0a1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=2a9730de-c3a1-4841-8b24-cedd9df04a0c /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=3d13dcef-1b8c-41d9-bada-a585b4022a2d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
  10.9GB: boot/grub/grub.cfg
  10.0GB: boot/initrd.img-2.6.38-8-generic
  10.9GB: boot/vmlinuz-2.6.38-8-generic
  10.0GB: initrd.img
  10.9GB: vmlinuz
```

---

### Post by Rubi1200 on 2011-04-30
Have you tried using nomodeset at boot?

To bring up the GRUB menu, hold Shift down as the computer boots (sometimes needs playing with to get it right).
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Paul41 on 2011-04-30
I am not able to get to the grub menu. It always loops back to the BIOS splash screen before even trying to load grub.

---

### Post by dino99 on 2011-04-30
then its either a bios problem or motherboard battery is powerless

---

### Post by Paul41 on 2011-04-30
> **dino99 said:**
> then its either a bios problem or motherboard battery is powerless

Everything worked fine until installing 11.04 so I don't see how this would be the problem.

---

### Post by Paul41 on 2011-04-30
I'm in now. I left off this line

> grub-install /dev/sda

and after doing that I was able to boot.

---

