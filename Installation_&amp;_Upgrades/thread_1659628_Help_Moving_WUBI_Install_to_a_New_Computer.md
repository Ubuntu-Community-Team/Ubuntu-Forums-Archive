---
title: "Help Moving WUBI Install to a New Computer"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by sosukeinu on 2011-01-04
Hello, I recently installed Ubuntu 10.10 via WUBI on a netbook. After spending countless hours configuring it just how I want it, I decided to move the install to a different computer (one with a little more power). I backed up the entire install using heliode's guide here: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) I backed up in bzip2 and I excluded the /host directory because i wouldn't be needing that nasty windows installation. The system worked fine after restoring it, but now I think I either need to move my GRUB partition, or reconfigure it. When I try to boot i get a screen that says:
error: no such device: d0b2140db213f726.
error: no such partition.
error: no such disk.
error: you need to load the kernel first.
failed to boot both default and fallback entries.
Press any key to continue...

After pressing any key, I get the GRUB menu, but selecting any of the choices gets me the same error. Any help would be appreciated. Thank you.

---

### Post by dino99 on 2011-01-04
if you are looking for a serious experience, better to make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by drs305 on 2011-01-04
Since you mention getting rid of Windows, is this now a full install on its own partition?

Please boot the LiveCD and run the boot info script from the following link. Post the contents of the RESULTS.txt and we can take a look at the boot files and give you informed guidance.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by sosukeinu on 2011-01-04
i was just hoping to forgo all of the configuration i'd done on the other machine. lots of servers, etc. that i finally have working just the way i want. :(

---

### Post by sosukeinu on 2011-01-04
> **drs305 said:**
> Since you mention getting rid of Windows, is this now a full install on its own partition?

Please boot the LiveCD and run the boot info script from the following link. Post the contents of the RESULTS.txt and we can take a look at the boot files and give you informed guidance.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
will get you the boot info.

---

### Post by sosukeinu on 2011-01-04
Here is boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,603,135   112,601,088  83 Linux
/dev/sda2         112,605,182   117,209,087     4,603,906   5 Extended
/dev/sda5         112,605,184   117,209,087     4,603,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        763b61ce-472d-4491-b24d-ee31c66e3540   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3baf1be8-1003-44d3-a89b-fa0b31cb0695   swap                                     
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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d0b2140db213f726
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d0b2140db213f726
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d0b2140db213f726
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d0b2140db213f726
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2488d71188d6e07a
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4a14d76314d75095
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
  10.8GB: boot/grub/grub.cfg
   8.3GB: boot/initrd.img-2.6.35-22-generic
   8.3GB: boot/initrd.img-2.6.35-23-generic
  11.0GB: boot/vmlinuz-2.6.35-22-generic
  11.0GB: boot/vmlinuz-2.6.35-23-generic
   8.3GB: initrd.img
   8.3GB: initrd.img.old
  11.0GB: vmlinuz
  11.0GB: vmlinuz.old

```

---

### Post by drs305 on 2011-01-04
It appears your Wubi has been extracted to its own partition.

I haven't done this before so we'll make backups of the changes and I'll assume you are accessing the files from the LiveCD:

```
sudo mount /dev/sda1 /mnt
sudo cp /mnt/etc/fstab /mnt/etc/fstab.bak
gksu gedit /mnt/etc/fstab /mnt/boot/grub/grub.cfg
```

Change this part of fstab:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

to:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=763b61ce-472d-4491-b24d-ee31c66e3540  /   ext4   errors=remount-ro 0  1
UUID=3baf1be8-1003-44d3-a89b-fa0b31cb0695  none   swap   0  0

Save the file.

Add this with the "### BEGIN /etc/grub.d/10_linux ###" section of grub.cfg:
> menuentry "Ubuntu, Linux 2.6.35-23-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 763b61ce-472d-4491-b24d-ee31c66e3540
	set root=(hd0,1)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}

Save the file and do NOT update grub.
Reboot. 

If it successfully boots, run "sudo update-grub" to make the grub.cfg change permanent and reflect the current system configuration.

---

### Post by sosukeinu on 2011-01-04
Works a treat! Thank you. This is why I love the Ubuntu community, fast and helpful answers! Should I, or rather, can I delete all of the other menu entries in the grub.cfg? also, I noticed the filesystem is set to ntsf, since it was installed with WUBI next to windows. Should I be concerned with this, or just leave it as it is? Thank you very much for your help

---

### Post by drs305 on 2011-01-04
> **sosukeinu said:**
> Works a treat! Thank you. This is why I love the Ubuntu community, fast and helpful answers! Should I, or rather, can I delete all of the other menu entries in the grub.cfg? also, I noticed the filesystem is set to ntsf, since it was installed with WUBI next to windows. Should I be concerned with this, or just leave it as it is? Thank you very much for your help

If you run "sudo update-grub" it should eliminate the Windows entries since os-prober won't find it installed any longer.


If you don't want to see the recovery mode option, you can disable it in /etc/default/grub by uncommenting (removing the # symbol) this line:
```
**[COLOR="DarkRed"]#[/COLOR]**GRUB_DISABLE_LINUX_RECOVERY="true"
```
I don't mind not seeing recovery modes but many users like having a quick way to get to the recovery mode. It's up to you.

The menu also displays an older kernel. It's not a bad idea to have a 'backup' kernel in case the current one fails during an update. If you don't want to see the extra kernel, there are some ways to hide the output from the menu but they are a bit convoluted. If you remove the kernel you won't see it in the menu. I'd recommend leaving this second entry as insurance. You could also just create a custom menu and make it look exactly as you want.

The NTFS reference I assume regards the "insmod ntfs" module. I'd just leave it...

After making any or all of these changes, run "sudo update-grub" to make sure they are incorporated in the menu.

---

### Post by sosukeinu on 2011-01-04
Thank you. You've been more than helpful.

---

