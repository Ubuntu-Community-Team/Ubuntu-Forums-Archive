---
title: "Ubuntu 10.10 Update Manager  Grub2 Configuration Error"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by kw1502 on 2011-06-18
I&#7743; running Ubuntu 10.10 32 bit and Grub2. When running the update manager, I get the following  message while it is configuring grub-pc:

[INDENT]The Grub boot loader was previously installed to a disk that is no longer present, or whose normally unique identifier has been changed for some reason. It is important to make sure that the installed Grub stays in sync with other components such as grub.cfg...[/INDENT]

I change my hardware, including hard disks, frequently so that is likely the cause. My computer still boots but I like to fix this if possible.  My disk partitions are:
[INDENT]/dev/sda1	/boot
/dev/sda2	/
/dev/sda3	/home[/INDENT]

What do I need to do to correct this problem?

---

### Post by Rubi1200 on 2011-06-18
Hi,
please post the results of the boot info script (can also be run from within a working install):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2011-06-18
Post boot script but also post this:

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by kw1502 on 2011-06-18
Here is the info requested: from the boot info script and sudo debconf-show grub-pc. Thanks for you help.

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 1b3df142-1a77-4ad5-99db-f267fa6bf77e root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       905,215       903,168  83 Linux
/dev/sda2             905,216   700,905,471   700,000,256  83 Linux
/dev/sda3         700,905,472 1,945,702,399 1,244,796,928  83 Linux
/dev/sda4       1,945,702,400 1,953,525,167     7,822,768   5 Extended
/dev/sda5       1,945,704,448 1,953,523,711     7,819,264  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,953,523,711 1,953,521,664   5 Extended
/dev/sdb5               4,096 1,238,538,239 1,238,534,144   7 NTFS / exFAT / HPFS
/dev/sdb6       1,238,540,288 1,933,043,711   694,503,424   7 NTFS / exFAT / HPFS
/dev/sdb7       1,933,045,760 1,953,523,711    20,477,952   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0f366b32-5b5e-4201-a9c2-4f2b5b6d560d   ext2       
/dev/sda2        c3b130f4-873b-4e95-9b8f-f99425540227   ext3       
/dev/sda3        3a81f209-a980-4b4b-9c51-56da3e488574   ext3       
/dev/sda5        bf508821-6b3c-4276-887f-21535151db95   swap       
/dev/sdb5        0B9FCE50790316D6                       ntfs       Bckups
/dev/sdb6        6760282F62CF4E0E                       ntfs       Vault
/dev/sdb7        6022E3AE777339CA                       ntfs       Pgfile

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext2       (rw)
/dev/sda2        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda3        /home                    ext3       (rw,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set c3b130f4-873b-4e95-9b8f-f99425540227
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
set locale_dir=($root)/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=c3b130f4-873b-4e95-9b8f-f99425540227 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=c3b130f4-873b-4e95-9b8f-f99425540227 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
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

   0.018620491 = 0.019993600    grub/core.img                                  2
   0.006352425 = 0.006820864    grub/grub.cfg                                  1
   0.038414955 = 0.041247744    initrd.img-2.6.35-28-generic-pae              49
   0.026894569 = 0.028877824    vmlinuz-2.6.35-28-generic-pae                 22

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set c3b130f4-873b-4e95-9b8f-f99425540227
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
set locale_dir=($root)/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=c3b130f4-873b-4e95-9b8f-f99425540227 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=c3b130f4-873b-4e95-9b8f-f99425540227 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0f366b32-5b5e-4201-a9c2-4f2b5b6d560d
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=c3b130f4-873b-4e95-9b8f-f99425540227 /               ext3    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=3a81f209-a980-4b4b-9c51-56da3e488574 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=bf508821-6b3c-4276-887f-21535151db95 none            swap    sw              0       0
10.57.59.2:/home/shared	/media/MyDocuments	nfs	user,auto,rsize=8192,wsize=8192,timeo=14,rw,soft,intr	0	0
10.57.59.2:/backups/AVFiles/Ken	/mnt/MyAV	nfs	user,auto,rsize=8192,wsize=8192,timeo=14,rw,soft,intr	0	0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.449284554 = 0.482415616    boot/grub/core.img                             2
   0.437016487 = 0.469242880    boot/grub/grub.cfg                             1
   0.469079018 = 0.503669760    boot/initrd.img-2.6.35-28-generic-pae         49
   0.457558632 = 0.491299840    boot/vmlinuz-2.6.35-28-generic-pae            22
   0.469079018 = 0.503669760    initrd.img                                    49
   0.457558632 = 0.491299840    vmlinuz                                       22

=============================== StdErr Messages: ===============================

unlzma: Decoder error


sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
* grub-pc/install_devices_empty: true
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
* grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10


```

---

### Post by oldfred on 2011-06-18
Have you tried booting from sda?

The grub2 in sdb is looking for UUID 1b3df142-1a77-4ad5-99db-f267fa6bf77e which does not exist. It is looking for a Natty install as it has grub 1.99, but you show only 10.10 with a boot partition in sda1 and the install in sda2. Did you install Natty & uninstall it?

The sudo debconf-show grub-pc, I think only showed the liveCD version. The hard drive info is buried in /var/cache/debconf/config.dat which also has a lot of other info.

---

### Post by kw1502 on 2011-06-18
I only boot from sda. Must have installed Natty on sdb and uninstalled.
Is the solution to uninstall Grub2 from sdb? If so, how do I do that?

---

### Post by oldfred on 2011-06-18
As long as you do not boot from sdb, it does not matter. I prefer to keep the boot loader for a system on the same drive as the system.

When you install a new system on sdb then you can install that boot loader to the MBR of sdb.

You can zero it out, but you have to use dd and dd's nickname is Data Destroyer as it is easy to mistype and then everything goes south.

You can install your grub2 boot loader if you want. From Your Ubuntu
But I would not use it to boot, just use the one on sda.

sudo grub-install /dev/sdb

---

