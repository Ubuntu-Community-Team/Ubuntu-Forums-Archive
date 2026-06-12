---
title: "GRUB2 problems after cleanish install"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by lamadog on 2009-11-23
Hi!

I'm having problems with GRUB after a cleanish install (format and reinstall for /, old /home kept). As far as I can tell GRUB 2 has installed itself in the wrong MBR and is conflicting with GRUB 1 (from the right MBR) at startup, giving me GRUB state 1.5 error 2 at startup.

My setup is one HD (obviosly treated as hd0 by the BIOS) with Windows on it and 2 more HDs sharing an LVM volume for /home and a normal ext3 drive on the first one for /

Here is the result of the boot info bash script floating around: 

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d49b8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,080    50,781,464    11,711,385  82 Linux swap / Solaris
/dev/sda3          50,781,465   488,392,064   437,610,600  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a5c353a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x002f002e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sdc2          61,432,560   398,283,479   336,850,920   f W95 Ext d (LBA)
/dev/sdc5          61,432,623   398,283,479   336,850,857   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="39fccedc-0ddc-499f-a5d2-cd47fe5b558b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="dd1e43fa-c489-4e50-917c-a38328554029" TYPE="swap" 
/dev/sda3: UUID="Zmo6vM-D2px-c3rt-yeDC-4Clb-kGbM-s9ipH8" TYPE="LVM2_member" 
/dev/sdb1: UUID="HQQKJl-wPyK-7x2O-er2B-h38q-ULEY-bHEVjm" TYPE="LVM2_member" 
/dev/sdc1: UUID="17B8EB0841E2837F" TYPE="ntfs" 
/dev/sdc5: UUID="083CA2C63CA2ADDE" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 39fccedc-0ddc-499f-a5d2-cd47fe5b558b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 39fccedc-0ddc-499f-a5d2-cd47fe5b558b
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=39fccedc-0ddc-499f-a5d2-cd47fe5b558b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 39fccedc-0ddc-499f-a5d2-cd47fe5b558b
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=39fccedc-0ddc-499f-a5d2-cd47fe5b558b ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 17b8eb0841e2837f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=39fccedc-0ddc-499f-a5d2-cd47fe5b558b /               ext3    errors=remount-ro 0       1
/dev/mapper/vg-lvol0 /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=dd1e43fa-c489-4e50-917c-a38328554029 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic-pae
    .0GB: boot/vmlinuz-2.6.31-14-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

I've tried booting up the Live CD and fixing it a few times now, but can't seem to get anywhere. Reconfiguring grub-pc gives the following error for all disks I mark for installation of GRUB2:

```
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for /boot/grub.

```

No luck doing it with chroot either. Any ideas?

---

### Post by phillw on 2009-11-23
If you have upgraded 9.04 --> 9.10 and HAVE NOT updated grub, then you're still on grub legacy.

If you are running a fresh install of 9.10, then you're on Grub2

To recover Grub under Grub2 then you will need step 12 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Step 12 also links to a more in depth one, covering UID's etc for recovery that way.

As always, post back if you are still having problems.

Regards,

Phill.

---

### Post by lamadog on 2009-11-23
Thanks! Nr. 12 on that list fixed it.

- Daniel

---

