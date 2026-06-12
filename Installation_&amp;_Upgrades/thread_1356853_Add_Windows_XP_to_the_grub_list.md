---
title: "Add Windows XP to the grub list"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by o2mcgovem on 2009-12-16
Hello, 

I've been running Ubuntu 9.10 for about a week now after my friend installed it for me, I'm gonna stay here but I'd like Windows XP available for gaming. I installed XP no problem, then because that install wiped out grub I used the live CD to re-install it. However, now I can't get back to Windows XP. Can anyone help me add XP to the list?

Here's my boot info script:

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1             224,910     4,225,094     4,000,185  82 Linux swap / Solaris
/dev/sda2           4,225,095   199,543,364   195,318,270  83 Linux
/dev/sda3    *    199,543,365   234,420,479    34,877,115   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="364a9761-40ae-4074-b78d-6bec411b87f5" TYPE="swap" 
/dev/sda2: UUID="f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc" TYPE="ext4" 
/dev/sda3: UUID="BE3CDB4A3CDAFBF9" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)


=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST ##

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d7-021b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=f72a0e68-8dc2-47f2-9f40-71db0bbfc3fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=364a9761-40ae-4074-b78d-6bec411b87f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   2.1GB: boot/grub/grub.cfg
   2.1GB: boot/grub/menu.lst
   2.1GB: boot/grub/stage2
   2.1GB: boot/initrd.img-2.6.31-14-generic
   2.1GB: boot/initrd.img-2.6.31-17-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   2.1GB: boot/vmlinuz-2.6.31-17-generic
   2.1GB: initrd.img
   2.1GB: initrd.img.old
   2.1GB: vmlinuz
   2.1GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

```Any help would be much appreciated!

Thanks,
Michael :)

---

### Post by darkod on 2009-12-16
Did you try in terminal:
sudo update-grub

Reboot to see if the grub menu has changed and if there is XP entry whether it's working.

---

### Post by o2mcgovem on 2009-12-16
Thanks for the quick reply.

Nope, nothing seems to have changed...

---

### Post by drs305 on 2009-12-16
Try what darkod suggested. Sometimes Grub 2 doesn't pick up Windows on the initial install but will the first time "sudo update-grub" is manually run after installation.

This is the menu that is currently created for my Windows partition. I've changed the partition to reflect yours, and of course your's would have a different UUID:
> 
menuentry "Microsoft Windows XP Home Edition (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set *ceecff9eecff7f51*
	drivemap -s (hd0) ${root}
	chainloader +1
}



Added: Simultaneous post it appears. You could try adding the above, tailored to your install, in the 40_custom file in /etc/grub.d . Then update-grub and see if the manual entry works.

---

### Post by darkod on 2009-12-16
I noticed you have both menu.lst and grub.cfg. If this was a 9.10 clean install you should have only grub2 and grub.cfg. But I'm not experienced enough to advise whether deleting menu.lst is the right step.

---

### Post by o2mcgovem on 2009-12-16
Okay, I'm kinda new to this. So I'd add...

```

	 	 		 			 				menuentry "Microsoft Windows XP Home Edition (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set **BE3CDB4A3CDAFBF9**
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

...since it says /dev/sda3: UUID="BE3CDB4A3CDAFBF9" TYPE="ntfs" in the boot info thing?

---

### Post by drs305 on 2009-12-16
The existence of both grub.cfg and menu.lst probably reflects an online upgrade in which the original grub files were retained. Once Grub 2 is working the old menu.lst file can be removed but it's existence won't harm anything and I wouldn't recommend removing the menu.lst quite yet.

---

### Post by darkod on 2009-12-16
Yes, add that in the 40_custom file. Full path is /etc/grub.d/40_custom, you can open it for editing with:
sudo gedit /etc/grub.d/40_custom

After that do again
sudo update-grub

---

### Post by o2mcgovem on 2009-12-16
> **darkod said:**
> I noticed you have both menu.lst and grub.cfg. If this was a 9.10 clean install you should have only grub2 and grub.cfg. But I'm not experienced enough to advise whether deleting menu.lst is the right step.

I believe that my friend may have reverted to grub1 after he installed ububtu for me since grub2 is bad. He did mention doing something like this but I can't remember if he actually went through with it since I had no need for dual-booting at the time.

---

### Post by o2mcgovem on 2009-12-16
Okay, I added that block of text to the file you said and it still didn't work. :s

---

### Post by o2mcgovem on 2010-01-05
I fixed this by the way. I just deleted all of the grub files completely and then installed the normal grub (e.g. not grub2 :P) and everything worked fine.

---

