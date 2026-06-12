---
title: "Black screen after install 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Pulka on 2012-04-26
Hi.


Just finished installing 12.04 and after a smooth installation, when restarting i only get a black screen with a blinking slash.

What can i do?

---

### Post by oboedad55 on 2012-04-26
> **Pulka said:**
> Hi.


Just finished installing 12.04 and after a smooth installation, when restarting i only get a black screen with a blinking slash.

What can i do?

Are you at a command prompt? If so you can "sudo apt-get update then sudo apt-get upgrade". Did you choose to install restricted format stuff? I did and it installed the correct Nvidia driver for my card.

---

### Post by Pulka on 2012-04-26
No, it's not a command prompt. Yes, installed restricted format. I have nvidia

---

### Post by oldfred on 2012-04-26
You may need add nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by lihaosky on 2012-04-26
I had the same issue... I upgraded from 11.10 to 12.04 and when I restarted it and got to the login screen, apparently the resolution is wrong and all the icons are crosses... When I logged in, nothing is on the desktop and the screen froze. My mouse cursor is gone and I couldn't switch to tty1 and there is no network connection. Only the clock is going. Don't know what's wrong. 

Linux upgrade is always a pain! Alas!

---

### Post by Pulka on 2012-04-26
I'm sorry but don't know how to do what you said. I don't get to grub, and in BIOS i don' t have those options. I did get them booting foram the cd, but choosing nomodeset didn't work


> **oldfred said:**
> You may need add nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by sfermat on 2012-04-26
same problem, i can't edit grub because i only see a black screen, no console or nothing... (after full instalation, now im on live cd)

---

### Post by gibsonsimswilson on 2012-04-26
I upgrade from 11.10 to 12.04 and all I get is a blank screen and the top menu is hardly visible..

---

### Post by oldfred on 2012-04-26
@lihaosky & gibsonsimswilson
If the solutions here have not worked, please start your own thread as solutions will be different and we cannot work with different solutions and users in one thread and keep it straight which solution is for who.

If you hold shift key down from BIOS until menu appears, do you get grub menu? It may not normally show menu if it has only found one system or you only have Ubuntu installed.

If you do not get menu.

Download this into liveCD and run the boot info script.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Pulka on 2012-04-27
Ok...

tried grub recovery and managed to boot to the freshly installed 12.04.

After that, opened terminal and did

```
sudo update-grub
```

all is well now

thank you all for your help

---

### Post by Pulka on 2012-04-27
Ups...false alarm!


after doing grub update it did find and created the file, mas still the same problem when restarting. Apparently he can't find the grub file

---

### Post by Pulka on 2012-04-27
here's my boot info script:

```


 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 63675297-c4a3-4a84-9326-96276b32eced root 
    set prefix=($root)/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,781,759     1,779,712  83 Linux
/dev/sda2           1,781,760     9,973,759     8,192,000  82 Linux swap / Solaris
/dev/sda3           9,973,760   112,861,183   102,887,424  83 Linux
/dev/sda4         112,861,184   312,580,095   199,718,912  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   5 Extended
/dev/sdb5                 126   156,296,384   156,296,259  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        63675297-c4a3-4a84-9326-96276b32eced   ext4       
/dev/sda2        a9ab7e65-c15a-42ed-a995-11c4a7a3ae4f   swap       
/dev/sda3        5391fa80-4506-4b8c-bcad-5e28fdaaffa5   ext4       
/dev/sda4        4783159a-22f1-450c-bd79-8c8fc6191d5d   ext4       
/dev/sdb5        daa354e7-9112-4fbc-8f54-bd36ad083785   ext3       
/dev/sr0                                                iso9660    CDROM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext4       (rw)
/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)


============================= sda1/grub/grub.cfg: ==============================

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
search --no-floppy --fs-uuid --set=root 5391fa80-4506-4b8c-bcad-5e28fdaaffa5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 63675297-c4a3-4a84-9326-96276b32eced
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 63675297-c4a3-4a84-9326-96276b32eced
	linux	/vmlinuz-3.2.0-23-generic-pae root=UUID=5391fa80-4506-4b8c-bcad-5e28fdaaffa5 ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 63675297-c4a3-4a84-9326-96276b32eced
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/vmlinuz-3.2.0-23-generic-pae root=UUID=5391fa80-4506-4b8c-bcad-5e28fdaaffa5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 63675297-c4a3-4a84-9326-96276b32eced
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 63675297-c4a3-4a84-9326-96276b32eced
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic-pae                2
               =                vmlinuz-3.2.0-23-generic-pae                   1

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
UUID=5391fa80-4506-4b8c-bcad-5e28fdaaffa5 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=63675297-c4a3-4a84-9326-96276b32eced /boot           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=4783159a-22f1-450c-bd79-8c8fc6191d5d /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=a9ab7e65-c15a-42ed-a995-11c4a7a3ae4f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by Bluphx on 2012-04-27
Hey I'm having the same problem, flash between desktop and da darkness in 3d^^ unity is enabled in ccsm. Was having same prob with beta, hoped that official release would fix. Going to backup n try fresh official install..

---

### Post by oldfred on 2012-04-27
Are you booting from sda or sdb?

Your install is in sda, but you have installed grub2 to sdb's MBR. I would suggest having the boot loader on the same drive as the system or sda.

You also have a separate /boot partition in sda1 and your main install in sda3 with /home in sda4.

Try booting from sdb. 

If you can boot then you can reinstall grub to sda.

sudo grub-install /dev/sda

But grub remembers where to reinstall on major updates:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And if you can use Boot-Repair to install grub2's boot loader to sda, but be sure to check the box/partition that you have a separate boot partition.

---

### Post by Pulka on 2012-04-27
\\:D/\\:D/\\:D/

wonderful!!

problem solved!

thank u oldfred

---

