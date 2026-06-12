---
title: "dual boot but grub not installed in MBR"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by mme oscar on 2012-07-18
Hi all,

I just did a fresh install of Windows 7 and then Ubuntu 12.04 (because of [this problem]("http://ubuntuforums.org/showthread.php?t=2013754")). My problem is that grub did not install in the MBR (Windows starts automatically). I'm able to boot in Ubuntu using the [Ultimate boot CD]("http://www.ultimatebootcd.com/") and "Super Grub 2", which easily finds the grub config file on /dev/sda6.

So I tried the usual

```
sudo update-grub 
sudo grub-install /dev/sda
```

but still nothing. 

I saw several threads about the same subject but they were quite complex cases, whereas I don't see anything special in my config?
and it's not the first time I install an Ubuntu with this kind of config. am I missing something stupid?

Also don't know if that matters but I did the installation using a USB drive (I checked that my hard drive was /dev/sda, anyway that should have worked the second time at least).

Here is the bootinfoscript output:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   122,882,047   122,880,000   7 NTFS / exFAT / HPFS
/dev/sda2         122,882,048   368,642,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda3         368,642,048   625,141,759   256,499,712   5 Extended
/dev/sda5         368,644,096   471,044,095   102,400,000  83 Linux
/dev/sda6         471,046,144   544,774,143    73,728,000  83 Linux
/dev/sda7         544,776,192   618,504,191    73,728,000  83 Linux
/dev/sda8         618,506,240   625,141,759     6,635,520  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        781A64FB3C86B129                       ntfs       
/dev/sda2        7D9A7E49385BFDF9                       ntfs       shared
/dev/sda5        a05e448e-1a28-4939-8fa7-e4fb216f0da7   ext4       data
/dev/sda6        59b6ce17-6b15-4bbc-a70a-5cf6857f09a7   ext4       
/dev/sda7        3634f488-e56a-4df9-866f-509d4744d644   ext4       linux2
/dev/sda8        8aa76b03-2f9a-4bb2-a42a-ade389eaefd4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/shared            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/data              ext4       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/linux2            ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 781A64FB3C86B129
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 /               ext4    errors=remount-ro 0       1
# /media/data was on /dev/sda5 during installation
UUID=a05e448e-1a28-4939-8fa7-e4fb216f0da7 /media/data     ext4    defaults        0       2
# /media/linux2 was on /dev/sda7 during installation
UUID=3634f488-e56a-4df9-866f-509d4744d644 /media/linux2   ext4    defaults        0       2
# /media/shared was on /dev/sda2 during installation
UUID=7D9A7E49385BFDF9 /media/shared   ntfs    defaults,umask=007,gid=46 0       0
# /media/windows was on /dev/sda1 during installation
UUID=781A64FB3C86B129 /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda8 during installation
UUID=8aa76b03-2f9a-4bb2-a42a-ade389eaefd4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 242.835166931 = 260.742275072  boot/grub/grub.cfg                             1
 226.026367188 = 242.693963776  boot/initrd.img-3.2.0-23-generic               2
 226.745834351 = 243.466485760  boot/vmlinuz-3.2.0-23-generic                  1
 226.026367188 = 242.693963776  initrd.img                                     2
 226.745834351 = 243.466485760  vmlinuz                                        1



```

Thanks for your help!

---

### Post by oldfred on 2012-07-18
Boot script looks normal except that you do not have grub2's boot loader in the MBR (and core.img) in / (root).

This command should have installed grub2's boot loader correctly. Did it report any errors?

sudo grub-install /dev/sda

Another bit more complete way:

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And it that does not work, you could try uninstalling & reinstalling. If you can boot you do not need liveCD.

HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


If you prefer a gui, this often helps you find issues and offers repairs.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by mme oscar on 2012-07-18
> **oldfred said:**
> Boot script looks normal except that you do not have grub2's boot loader in the MBR (and core.img) in / (root).

This command should have installed grub2's boot loader correctly. Did it report any errors?


there were no errors:
```

sudo grub-install /dev/sda
Installation finished. No error reported.
```

> 
Another bit more complete way:

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


Yes, this works! except that I had to install the package using

sudo apt-get install grub-pc

and then when I rebooted the grub menu was there.

I'd like to understand what happened: is it normal that this package was not installed? Could it be what caused the problem?

Thank you very much!

---

### Post by oldfred on 2012-07-18
Glad that worked.

Not sure why, did you by any chance have grub legacy installed not grub2 (grub-pc) or even grub-efi? Not sure how it would not have grub2 installed. Both use grub install the same, I think, but I do not know why the original command did not complain either?

---

### Post by efflandt on 2012-07-18
Many people seem to have a similar problem, and when I used "Other" for partitioning during install, it seemed to default to something other than sda.  It might be interesting to run bootinfoscript with the USB you booted from for install attached and see if grub was installed to that.

---

### Post by mme oscar on 2012-07-18
ok, so in order to see what happened I did a second installation on a different partition using exactly the same process. Indeed I select the "Other" partitioning, and this time I carefully checked that the target device for grub was /dev/sda -> at the beginning it was /dev/sdb (not totally sure, the USB drive anyway) but once I had selected the partition it automatically changed to /dev/sda.
However the result was the same: grub was not installed in the MBR (I would have been able to see the difference, simply because I had changed the time out for the one installed earlier).
 
> 
Not sure why, did you by any chance have grub legacy installed not grub2  (grub-pc) or even grub-efi? Not sure how it would not have grub2  installed. Both use grub install the same, I think, but I do not know  why the original command did not complain either?I don't know what are these different versions of grub but here are the grub* packages installed right after the process:
```

erwan@erwan-R530:~$ dpkg --get-selections | grep grub
grub-common                    install
grub-efi                    install
grub-efi-amd64                    install
grub-efi-amd64-bin                install
grub2-common                    install

```> 
  It might be interesting to run bootinfoscript with the USB you booted  from for install attached and see if grub was installed to that.     
and here is the bootinfoscript output with the USB attached:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 11007680 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   122,882,047   122,880,000   7 NTFS / exFAT / HPFS
/dev/sda2         122,882,048   368,642,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda3         368,642,048   625,141,759   256,499,712   5 Extended
/dev/sda5         368,644,096   471,044,095   102,400,000  83 Linux
/dev/sda6         471,046,144   544,774,143    73,728,000  83 Linux
/dev/sda7         544,776,192   618,504,191    73,728,000  83 Linux
/dev/sda8         618,506,240   625,141,759     6,635,520  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        781A64FB3C86B129                       ntfs       
/dev/sda2        7D9A7E49385BFDF9                       ntfs       shared
/dev/sda5        a05e448e-1a28-4939-8fa7-e4fb216f0da7   ext4       data
/dev/sda6        59b6ce17-6b15-4bbc-a70a-5cf6857f09a7   ext4       
/dev/sda7        ae2f5a06-7cf8-4880-94c6-564bc239ffb6   ext4       
/dev/sda8        8aa76b03-2f9a-4bb2-a42a-ade389eaefd4   swap       
/dev/sdb1        E03B-7886                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 781A64FB3C86B129
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
UUID=781A64FB3C86B129 /media/windows ntfs-3g umask=007 0 0
UUID=7D9A7E49385BFDF9 /media/shared ntfs-3g umask=007 0 0
UUID=a05e448e-1a28-4939-8fa7-e4fb216f0da7 /media/data ext4 defaults 0 2
UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 / ext4 defaults 0 1
UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 /media/linux2 ext4 defaults 0 0
UUID=8aa76b03-2f9a-4bb2-a42a-ade389eaefd4 swap swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 242.939407349 = 260.854202368  boot/grub/core.img                             1
 242.939376831 = 260.854169600  boot/grub/grub.cfg                             1
 226.026367188 = 242.693963776  boot/initrd.img-3.2.0-23-generic               2
 226.745834351 = 243.466485760  boot/vmlinuz-3.2.0-23-generic                  1
 226.026367188 = 242.693963776  initrd.img                                     2
 226.745834351 = 243.466485760  vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ae2f5a06-7cf8-4880-94c6-564bc239ffb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 781A64FB3C86B129
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 59b6ce17-6b15-4bbc-a70a-5cf6857f09a7
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=59b6ce17-6b15-4bbc-a70a-5cf6857f09a7 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ae2f5a06-7cf8-4880-94c6-564bc239ffb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8aa76b03-2f9a-4bb2-a42a-ade389eaefd4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 278.156070709 = 298.667806720  boot/grub/grub.cfg                             1
 261.308593750 = 280.577966080  boot/initrd.img-3.2.0-23-generic               2
 273.903060913 = 294.101172224  boot/vmlinuz-3.2.0-23-generic                  1
 261.308593750 = 280.577966080  initrd.img                                     2
 273.903060913 = 294.101172224  vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```I can give you more feedback about my config if you tell me what to do. (and probably only tomorrow because I'm going to bed now!)

---

### Post by oldfred on 2012-07-18
For whatever reason you are getting grub-efi, not the grub2 or grub-pc.

Because you do not have the efi partition nor booting with UEFI grub-efi will not correctly install. It really seems like a bug that it is not correctly identifying UEFI or are you not selecting the BIOS/AHCI/legacy version. It has to be installing the efi version to have grub-efi.

I install with BIOS but gpt partitions with an extra bios_grub partition. And I have grub-pc

```
fred@fred-Precise:~$ dpkg --get-selections | grep grub
grub-common                    install
grub-gfxpayload-lists                install
grub-pc                        install
grub-pc-bin                    install
grub-rescue-pc                    install
grub2-common                    install

```

---

### Post by YannBuntu on 2012-07-19
Hello
This is a severe bug that we should report to GRUB devs.

**@mme oscar:** Please could you create a bug report here ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)), with 
** title *"Ubiquity installs grub-efi on non-GPT disk"
** description :* description of the problem + link to this thread + your [full BootInfo URL]("https://help.ubuntu.com/community/Boot-Info") (created from your Ubuntu CD)
** attached files:* /var/log/installer/syslog and /var/log/installer/partman files which are in your installed Ubuntu.

Then indicate the link to your report here so that we follow it. Thanks!

---

### Post by mme oscar on 2012-07-19
> **YannBuntu said:**
> Hello
This is a severe bug that we should report to GRUB devs.

**@mme oscar:** Please could you create a bug report here ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)), with 
** title *"Ubiquity installs grub-efi on non-GPT disk"
** description :* description of the problem + link to this thread + your [full BootInfo URL]("https://help.ubuntu.com/community/Boot-Info") (created from your Ubuntu CD)
** attached files:* /var/log/installer/syslog and /var/log/installer/partman files which are in your installed Ubuntu.

Then indicate the link to your report here so that we follow it. Thanks!

Done, the bug report is at
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616)

don't know if I should mark this thread as solved now?

---

### Post by darkod on 2012-07-19
Make sure you are not booting the cd/usb in uefi mode. Newer boards with uefi options seem to have all boot devices twice, a "standard" bios mode version and uefi version.

The ubuntu cd/usb can be booted as both, so if in the boot devices list cd-rom (uefi) is before cd-rom (normal), it will boot it in uefi mode in which case it will try to install grub-efi (and it seems it successfully is).
But since you are not using uefi boot and have no uefi system partition, you can't boot like that, it's incomplete.

---

### Post by oldfred on 2012-07-19
If system is working, you can change to "solved".

And thanks for reinstalling and confirming that it was installing grub-efi not grub-pc. Bug report should help developers and knowing the issue will help those of us in the forum suggest the work around to others with the same issue.

---

### Post by YannBuntu on 2012-07-19
> **mme oscar said:**
> Done, the bug report is at
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616)

Thanks!

---

