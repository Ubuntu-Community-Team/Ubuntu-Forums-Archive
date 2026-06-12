---
title: "Lost windows boot option after altering partitions"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by jtward on 2011-11-17
Hi,
I recently installed Windows 7 and Ubuntu 11.10 (both x64) onto my PC. I moved some partitions around (using gparted on a Ubuntu 11.10 CD) and now there's no option to boot to Windows 7 from grub. Running repair from the Windows CD doesn't help, and it can't see that there's a copy of Windows installed.

Here's the fdisk -l:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ba654c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1007224831   503611392   83  Linux
/dev/sda2      1024002048  1953521663   464759808    7  HPFS/NTFS/exFAT
/dev/sda4      1007224832  1024002047     8388608   82  Linux swap / Solaris

Partition table entries are not in disk order
```

and here's the grub.cfg after an update-grub:

```
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
  set locale_dir=($root)/boot/grub/locale
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=932f8069-9114-4f3a-80b9-c5d124c537b9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=932f8069-9114-4f3a-80b9-c5d124c537b9 ro recovery nomodeset 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 932f8069-9114-4f3a-80b9-c5d124c537b9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
```

Any suggestions?
Cheers, James

---

### Post by BillyBoa on 2011-11-17
Well give a try to Boot-Repair

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```

Seems it repairs Ubuntu and Windows bootsectors

---

### Post by darkod on 2011-11-17
Are you sure win7 is on /dev/sda2?

What was on /dev/sda3 which is now missing?

---

### Post by jtward on 2011-11-17
@BillyBoa: Well give a try to Boot-Repair
I've run the default repair which didn't help. In the advanced settings, I only get the option to boot to sda1 by default. However, if I select to restore MBR, it gives me the option to boot to the sda2 partition. I'm not sure if it knows whether there's anything there or not though.

@darkod: Are you sure win7 is on /dev/sda2?
Yes, positive. I haven't touched sda2 since installing win7

What was on /dev/sda3 which is now missing?
That's where ubuntu was originally installed to; I copied the partition, removed the old partition and expanded the new partition to fill the space.

---

### Post by jtward on 2011-11-17
> **jtward said:**
> I've run the default repair which didn't help.
The output can be found at [http://paste.ubuntu.com/741621/](http://paste.ubuntu.com/741621/)

---

### Post by darkod on 2011-11-17
One of the partition which is now gone had the win7 boot files. On sda2 you have only one boot file and the other two are missing.

Be careful using other tools, like Boot-Repair because it can complicate things. If all is in order with win7, the ubuntu cd is enough. But all is not in order with win7.

What I would do:
1. Boot with the ubuntu cd in live mode and open Gparted.
2. Select /dev/sda2, right-click and select Manage Flags. Turn on the Boot flag.

Then boot with the win7 dvd and try the Repair This Computer. Hopefully it will work.

If it doesn't, I'm not sure how to put back win7 boot files when they are missing.

---

### Post by mattzab on 2011-11-18
I'm having this same problem after using Clonezilla to copy windows from a partition on one HDD to a new HDD. It copied over fine, just now when I try to select windows with Grub it just gives me a blank screen with an underscore blinking at the top left of the screen.

I tried repairing using my backup win7 disc but no dice.

Any other ideas?

---

### Post by darkod on 2011-11-18
> **mattzab said:**
> I'm having this same problem after using Clonezilla to copy windows from a partition on one HDD to a new HDD. It copied over fine, just now when I try to select windows with Grub it just gives me a blank screen with an underscore blinking at the top left of the screen.

I tried repairing using my backup win7 disc but no dice.

Any other ideas?

Do you also have ubuntu on the new HDD? Is that why you are using grub?

Win7 disc can't repair grub, you can only use it to reinstall windows bootloader to the MBR of the disk, but that will leave ubuntu unbootable.

Are you sure all boot files were on the partition you cloned? Remember that win7 sometimes has a small System Reserved partition and this holds part of the boot files. Without them it can't boot on the new disk.

That could be a reason why ubuntu can't detect it. Otherwise if the cloning was made successfully, all you need on the new disk is boot ubuntu and run

sudo update-grub

to detect win7.

---

