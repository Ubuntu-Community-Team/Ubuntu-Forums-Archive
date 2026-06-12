---
title: "Installed 11.04 and can only boot to Vista"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by campbuds on 2011-08-06
I installed ubuntu 11.04 and after install no grub menu shows up. It just boots to Vista. I cannot get into ubuntu at all.

How do I fix this?

---

### Post by oldfred on 2011-08-06
Did you do an install to partitions or a wubi install inside the Windows NTFS partition?

From Ubuntu liveCD post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by campbuds on 2011-08-06
It is installed on a separate partition.

---

### Post by Furball588 on 2011-08-06
> **campbuds said:**
> It is installed on a separate partition.

and probably on a different drive...

If so, have you changed the boot order to see if booting to the other device pops grub?

---

### Post by campbuds on 2011-08-06
A different drive letter but on the same physical hard drive. It is just a separate partition

---

### Post by campbuds on 2011-08-06
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

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

/dev/sda1               2,048    15,691,775    15,689,728  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     15,691,776   142,588,159   126,896,384   7 NTFS / exFAT / HPFS
/dev/sda3         142,589,950   625,141,759   482,551,810   5 Extended
/dev/sda5         142,589,952   620,967,935   478,377,984  83 Linux
/dev/sda6         620,969,984   625,141,759     4,171,776  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3E30F8B630F875ED                       ntfs       Recovery
/dev/sda2        16BCF9A6BCF98093                       ntfs       
/dev/sda5        129afdb6-5b57-4645-be27-0f56563e75e0   ext4       
/dev/sda6        092fe884-ea19-43fd-97af-53c24df45107   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.pam                                     0

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=129afdb6-5b57-4645-be27-0f56563e75e0 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=129afdb6-5b57-4645-be27-0f56563e75e0 ro single 
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 129afdb6-5b57-4645-be27-0f56563e75e0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E30F8B630F875ED
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 16BCF9A6BCF98093
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=129afdb6-5b57-4645-be27-0f56563e75e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=092fe884-ea19-43fd-97af-53c24df45107 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.153347015 = 75.326582784   boot/grub/core.img                             1
  68.144531250 = 73.169633280   boot/grub/grub.cfg                             1
  69.312500000 = 74.423730176   boot/initrd.img-2.6.38-8-generic               2
  70.152648926 = 75.325833216   boot/vmlinuz-2.6.38-8-generic                  1
  69.312500000 = 74.423730176   initrd.img                                     2
  70.152648926 = 75.325833216   vmlinuz                                        1


```

---

### Post by Furball588 on 2011-08-06
Then I'd say grub wasn't written to the MBR for what could be a few reasons...

Give this a look

[http://ubuntuforums.org/showpost.php?p=10871917&postcount=1](http://ubuntuforums.org/showpost.php?p=10871917&postcount=1)


I guess I should ask if you made any changes to the default options as to where to install grub (or even LILO)?

---

### Post by campbuds on 2011-08-06
I made no changes, I just did a standard install

---

### Post by jayadeep on 2011-08-06
please see that you have given a swap memory space for ubuntu.....then it may work

---

### Post by oldfred on 2011-08-06
I think you just need to install grub2's boot loader to the MBR of sda. Not sure how a standard install did not install a boot loader. Do you have a BIOS that locks the MBR, a few systems have a way to write protect the MBR?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


You can also download liveCDs like these to boot into Ubuntu and then install grub from inside Ubuntu easily.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Install once booted:
sudo grub-install /dev/sda
sudo update-grub

---

### Post by campbuds on 2011-08-06
Tried a reinstall and now I have grub.

not sure what happened but all is well

---

