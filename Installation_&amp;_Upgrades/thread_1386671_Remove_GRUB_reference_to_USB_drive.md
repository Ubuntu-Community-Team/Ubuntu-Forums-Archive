---
title: "Remove GRUB reference to USB drive"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by tylersontag on 2010-01-21
Alright, so I was trying to load up Ubuntu 9.10 on a thumb drive to load look at the files on a computer with a dead disk drive, I couldn’t boot up on the other computer, but that’s another story (yes the drive was marked as bootable)

When I restart my laptop whose diskdrive I used to install Ubuntu onto the USB drive, I get a GRUB error “No such device” and can load anything unless I plug back in the USB drive. When it is plugged in, the USB boot is the primary (1st in the list) boot. I tried editing the .lst file on my laptop’s drive but it only has its kernels listed. Anyone know how to make my system quit looking for a USB mounted kernel? Or at least not fail if it can’t find one.

---

### Post by kansasnoob on 2010-01-21
Well, I have to make some educated guesses, but most likely the thumb drive install threw it's "grub" on the wrong drive. It's generally easy to fix but to avoid guess work please post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Note: all drives must be plugged in.

---

### Post by djchandler on 2010-01-21
Get a SuperGRUB CD and boot it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Once you are logged onto the hard disk installed os, then you can fix the hard disk mbr and the GRUB menu.

Use Synaptic or apt-get and install GRUB.

---

### Post by darkod on 2010-01-21
> **tylersontag said:**
> Alright, so I was trying to load up Ubuntu 9.10 on a thumb drive to load look at the files on a computer with a dead disk drive, I couldn’t boot up on the other computer, but that’s another story (yes the drive was marked as bootable)

When I restart my laptop whose diskdrive I used to install Ubuntu onto the USB drive, I get a GRUB error “No such device” and can load anything unless I plug back in the USB drive. When it is plugged in, the USB boot is the primary (1st in the list) boot. I tried editing the .lst file on my laptop’s drive but it only has its kernels listed. Anyone know how to make my system quit looking for a USB mounted kernel? Or at least not fail if it can’t find one.

Run the script as kansasnoob said. And you have to be more clear what you actually did because "load up ubuntu" is confusing.

For just looking at files on any disk on the computer, you don't need to install ubuntu anywhere. Just boot with the ubuntu cd or bootable usb stick, select Try Ubuntu option, and you can look at files and copy what you need.

On the other hand, if "load up ubuntu" means you actually installed it on the usb stick, it is quite normal it can't start without it becaue grub config files are on the root partition in /boot/grub. It would be similar if you install windows on one disk and then try to boot the computer without that disk.

---

### Post by presence1960 on 2010-01-21
> **djchandler said:**
> Get a SuperGRUB CD and boot it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Once you are logged onto the hard disk installed os, then you can fix the hard disk mbr and the GRUB menu.

Use Synaptic or apt-get and install GRUB.

super grub disk does not work for grub2. OP before you do that you need to know if you have GRUB Legacy 0.97 or GRUB2.

Besides follow kansasnoob's suggestion. The output from the script will help solve your problem as it contains vital info about your setup & boot process. I am a advocate of the running the script prior to trying to fix boot problems because if you blindly try fixing things you can compound your problem(s)

---

### Post by tylersontag on 2010-01-21
well that output is quite long but ok.

I was trying to basically make a bootable USB stick out of this external USB but the instruction i read basically told me to install it on the the device.  needless to say it didn't work out, but i digress.

OK, my laptop with the drive i want to be booting is gonna be legacy GRUB while the new install on the USB drive is probably GRUB 2, it was off a fresh 9.10 install

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 2837024 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /grub/menu.lst. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 166430805 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             128,520    10,618,964    10,490,445   b W95 FAT32
/dev/sda3    *     10,618,965   228,428,234   217,809,270  83 Linux
/dev/sda4         228,428,235   234,436,544     6,008,310   5 Extended
/dev/sda5         228,428,298   234,436,544     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdba20631

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,444,018,589 1,444,018,527  83 Linux
/dev/sdb2       1,444,018,590 1,465,144,064    21,125,475   5 Extended
/dev/sdb5       1,444,018,653 1,465,144,064    21,125,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0410" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="2B4A-2080" TYPE="vfat" 
/dev/sda3: UUID="77dece63-d920-49c7-8541-85d99bf7e308" TYPE="ext3" 
/dev/sda5: UUID="faa8e05f-a811-4c70-84ec-98cf83afabdc" TYPE="swap" 
/dev/sdb1: UUID="e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649" TYPE="ext4" 
/dev/sdb5: UUID="8ee48cdb-e91a-4f93-99cf-bb13d0208cac" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tag/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tag)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649 type ext4 (rw,nosuid,nodev,uhelper=devkit)


============================= sda2/grub/menu.lst: =============================

; vim:tw=0:noai

; Note: REINSTALL parameter is used by script to add CONFIRMATION PROMPT for reinstall. Do not add this parameter for factory...
title Recovery Mode -- Automatically reinstall and erase hard drive
  root (hd0,1)
  kernel /casper/vmlinuz preseed/file=/cdrom/preseed/dell.seed boot=casper automatic-ubiquity noprompt REINSTALL xforcevesa
  initrd /casper/initrd.gz

title Recovery Mode -- Boot recovery Live Image (Manual Reinstall)
  root (hd0,1)
  kernel /casper/vmlinuz boot=casper preseed/file=/cdrom/preseed/ubuntu.seed xforcevesa
  initrd /casper/initrd.gz

title Go back to normal Hard Drive boot
  rootnoverify (hd0,2)
  chainloader +1

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.gz
    .0GB: vmlinuz

=========================== sda3/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.10, kernel 2.6.28-13-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=77dece63-d920-49c7-8541-85d99bf7e308 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=faa8e05f-a811-4c70-84ec-98cf83afabdc none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

=================== sda3: Location of files loaded by Grub: ===================


   5.4GB: boot/grub/menu.lst
   5.4GB: boot/grub/stage2
   5.4GB: boot/initrd.img-2.6.28-11-generic
   5.4GB: boot/initrd.img-2.6.28-13-generic
   5.4GB: boot/initrd.img-2.6.28-14-generic
   5.4GB: boot/initrd.img-2.6.28-15-generic
   5.4GB: boot/initrd.img-2.6.28-16-generic
   5.4GB: boot/initrd.img-2.6.31-14-generic
   5.4GB: boot/initrd.img-2.6.31-15-generic
   5.4GB: boot/initrd.img-2.6.31-16-generic
   5.4GB: boot/initrd.img-2.6.31-17-generic
   5.4GB: boot/vmlinuz-2.6.28-11-generic
   5.4GB: boot/vmlinuz-2.6.28-13-generic
   5.4GB: boot/vmlinuz-2.6.28-14-generic
   5.4GB: boot/vmlinuz-2.6.28-15-generic
   5.4GB: boot/vmlinuz-2.6.28-16-generic
   5.4GB: boot/vmlinuz-2.6.31-14-generic
   5.4GB: boot/vmlinuz-2.6.31-15-generic
   5.4GB: boot/vmlinuz-2.6.31-16-generic
   5.4GB: boot/vmlinuz-2.6.31-17-generic
   5.4GB: initrd.img
   5.4GB: initrd.img.old
   5.4GB: vmlinuz
   5.4GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-15-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-13-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-11-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=77dece63-d920-49c7-8541-85d99bf7e308 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 77dece63-d920-49c7-8541-85d99bf7e308
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8ee48cdb-e91a-4f93-99cf-bb13d0208cac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by kansasnoob on 2010-01-22
OK this isn't too bad at all, first some observations. This is helpful info:

> my laptop with the drive i want to be booting is gonna be legacy GRUB while the new install on the USB drive is probably GRUB 2

From the Script:

> sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 166430805 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

So we know that your laptops Karmic is on sda3. But the following shows that sda has a grub2 mbr:

> Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=e0eb6b56-60ee-4fcd-887a-5b6ddb1f7649)/boot/grub.

Then the external drive's Karmic is on sdb1 but sdb has a Windows mbr:

> Windows is installed in the MBR of /dev/sdb

But when you say this:

> When I restart my laptop whose diskdrive I used to install Ubuntu onto the USB drive, I get a GRUB error “No such device” and can load anything unless I plug back in the USB drive. When it is plugged in, the USB boot is the primary (1st in the list) boot.

I'm left wondering what you can boot? From the menu entries in the externals grub.cfg file I'd think you can boot both OS's as long as the external is plugged in, eh?

Anyway read these options carefully, paying attention to the **if's**!

It sounds like you can boot into the external drive. If so we'll start by booting into the external drives OS, just to be sure you are where you need to be run:

```
df
```

You'll see an output like this:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
**[COLOR="Red"]/dev/sdb1[/COLOR]**              8586272   3923572   4226536  49% /
none                    993248       308    992940   1% /dev
none                    997888       212    997676   1% /dev/shm
none                    997888        96    997792   1% /var/run
none                    997888         0    997888   0% /var/lock
none                    997888         0    997888   0% /lib/init/rw
none                   8586272   3923572   4226536  49% /var/lib/ureadahead/debugfs
/dev/sdXY            16374584   2930844  12944684  19% /home

```

The only thing we care about is that you've mounted sdb1 as I've highlighted there. Then simply run this command:

```
sudo grub-install /dev/sdb
```

If that returns any errors run:

```
sudo grub-install --recheck /dev/sdb
```

That should be it for giving the external drive it's own mbr. Note: however the system BIOS must be set to boot from USB before the hard drive. Mine is set to boot first from CD ROM, second from USB and then from hard drive.

The next step is to straighten out the legacy grub on sda (your laptops internal drive) so, if you can boot into it, do so. We need a grub shell so run:

```
sudo grub
```

```
root (hd0,2)
```

```
setup (hd0)
```

You should see:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Hopefully you saw the three yes and two succeeded notifications, regardless we need to quit the grub shell so:

```
quit
```

If that appeared to succeed as shown above that should be it. If not then try:

```
sudo grub-install /dev/sda
```

And repeat:

```
sudo grub
```

```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

If for any reason you couldn't boot into the laptops internal you can restore it's grub from an Ubuntu Live CD, just boot to the Live Desktop and do the same thing:

```
sudo grub
```

```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

Anyway, once you have the correct mbr on each drive and the BIOS settings right you should be able to boot the USB drive when it's plugged in and still be able to boot the internal when it's not.

---

### Post by djchandler on 2010-01-23
> **presence1960 said:**
> super grub disk does not work for grub2.

Really?!:confused:

So what are we supposed to do? If I was the OP, after looking at what kansasnoob posted as a possible even if viable solution, I might be thinking that this is getting out of hand. To me it looks more like an incantation ritual than a technical solution. I get the "if that doesn't work, try this" routine, but whatever happened to the "rescue" option on the live CD anyway? Why did it disappear with this release of all things, just when it may be needed more than ever?

Actually, I did get supergrub to recognize a 9.10 install before, although it wasn't a dual boot HD, nor was there an external USB drive involved. It was a "from scratch" install on a bare HD although it was on older "spare" hardware. [Grub-PC, aka Grub2 beta, was on it and I was never able to rescue it]("http://ubuntuforums.org/showthread.php?p=8215058#post8215058"). With no live data at risk, I scraped that install and ended up using that hardware with Debian 5.x and a USB stick just for running Folding@Home.

I'll let the link above do my ranting.

---

### Post by kansasnoob on 2010-01-23
> **djchandler said:**
> Really?!:confused:

So what are we supposed to do? If I was the OP, after looking at what kansasnoob posted as a possible even if viable solution, I might be thinking that this is getting out of hand. To me it looks more like an incantation ritual than a technical solution. I get the "if that doesn't work, try this" routine, but whatever happened to the "rescue" option on the live CD anyway? Why did it disappear with this release of all things, just when it may be needed more than ever?

Actually, I did get supergrub to recognize a 9.10 install before, although it wasn't a dual boot HD, nor was there an external USB drive involved. It was a "from scratch" install on a bare HD although it was on older "spare" hardware. [Grub-PC, aka Grub2 beta, was on it and I was never able to rescue it]("http://ubuntuforums.org/showthread.php?p=8215058#post8215058"). With no live data at risk, I scraped that install and ended up using that hardware with Debian 5.x and a USB stick just for running Folding@Home.

I'll let the link above do my ranting.

The best car I ever owned was a 1970 Chevy Nova. Should the auto makers have stopped making cars in 1971?

---

### Post by presence1960 on 2010-01-23
> **djchandler said:**
> Really?!:confused:

So what are we supposed to do? 

Actually, I did get supergrub to recognize a 9.10 install before, although it wasn't a dual boot HD, nor was there an external USB drive involved. It was a "from scratch" install on a bare HD although it was on older "spare" hardware. [Grub-PC, aka Grub2 beta, was on it and I was never able to rescue it]("http://ubuntuforums.org/showthread.php?p=8215058#post8215058"). With no live data at risk, I scraped that install and ended up using that hardware with Debian 5.x and a USB stick just for running Folding@Home.

I'll let the link above do my ranting.

Read this: [http://www.supergrubdisk.org/forum/index.php?topic=343.0](http://www.supergrubdisk.org/forum/index.php?topic=343.0)

Now I know you are mistaken about supergrubdisk because you made no mention of needing to use a special one for GRUB2. Supergrubdisk2 supports grub2, but as the man says it is sort of alpha- doesn't sound too promising to me.

---

### Post by presence1960 on 2010-01-24
If sda is the internal disk & sdb is external you need to fix GRUB on both disks separately. You want to restore Legacy GRUB 0.97 to sda and put GRUB 2 on sdb. You will need a 9.04 Live CD for Legacy GRUB & a 9.10 Live CD for GRUB2.

Fix legacy GRUB first so you can boot your internal disk. Boot the 9.04 Live CD without the external plugged in. At the menu choose "try ubuntu without any changes". Open a terminal (Applications > Accessories > Terminal) and do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,2)". 
5. Type "root (hd0,2)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Boot into Ubuntu. If that works reboot (with the external plugged in) with the 9.10 Live CD. Again choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```
This will mount the 9.10 / partition. Next from terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB2 on MBR of the external disk. Reboot & go into BIOS and set USB/Removable ahead of hard disk in the device boot order. Save changes to CMOS and continue booting. You should be able to boot from GRUB2 now when the external is plugged in. When the external is unplugged you will boot from Legacy GRUB 0.97.

Boot into Ubuntu from GRUB2 and open a terminal and run ```
sudo update-grub
```
When complete run in terminal ```
sudo dpkg-reconfigure grub-pc
```
Just hit enter until you get to the window where you choose sda or sdb. Use the arrow keys to navigate to sdb, use space bar to select sdb then hit Tab to select OK. Hit enter. This will insure that all updates to GRUB2 go to sdb and not overwrite the GRUB 0.97 on MBR of sda. make sure you do this all or you will lose the ability to boot the internal disk without the external plugged in at the first GRUB2 update.

---

### Post by presence1960 on 2010-01-24
> **djchandler said:**
> 

So what are we supposed to do? If I was the OP, after looking at what kansasnoob posted as a possible even if viable solution, I might be thinking that this is getting out of hand. To me it looks more like an incantation ritual than a technical solution. I get the "if that doesn't work, try this" routine, but whatever happened to the "rescue" option on the live CD anyway? Why did it disappear with this release of all things, just when it may be needed more than ever?

Actually Lance's instructions were very good. I think the only thing left out is you need the 9.04 Live CD for Legacy GRUB and the 9.10 Live CD for GRUB2.

djchandler in response to "what are we supposed to do"? read this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) pay attention to the menu of links on the right of the page. See #11 installing GRUB2 from a Live CD

---

### Post by garvinrick4 on 2010-01-24
> **tylersontag said:**
> Alright, so I was trying to load up Ubuntu 9.10 on a thumb drive to load look at the files on a computer with a dead disk drive, I couldn&#8217;t boot up on the other computer, but that&#8217;s another story (yes the drive was marked as bootable)

When I restart my laptop whose diskdrive I used to install Ubuntu onto the USB drive, I get a GRUB error &#8220;No such device&#8221; and can load anything unless I plug back in the USB drive. When it is plugged in, the USB boot is the primary (1st in the list) boot. I tried editing the .lst file on my laptop&#8217;s drive but it only has its kernels listed. Anyone know how to make my system quit looking for a USB mounted kernel? Or at least not fail if it can&#8217;t find one.

When you installing system onto USB stick there was a page in install about page 8 where 
there is an advanced tab in lower right. When you click that tab it asks you where you want to
install /boot. It has a default of sda and you have to change to your usb what ever sxx that 
If not it loads where it is defaulted.
disk. That is what it looks for boots then loads grub2 at that time when you update and upgrade. That is if you changed the advanced tab to sxx (your usb stick) if not it is going to be loaded onto sda.  There is no way I have found for USB not go to MBR in ext3 or ext4 with persistence. Of course regular USB Live CD install in fat32 gives you 4 gig persistence without going to MBR. Any way no matter what at one time or another grub2 was going to be installed in your MBR. Been there done that with 16 gig sticks. Nice if you are just going to use on your machine and you already have grub2 installed. You got all the fixes from previous posts but will work, just do not use on friends machine without a grub2 or you are going to have one unhappy friend.

---

### Post by presence1960 on 2010-01-24
> **garvinrick4 said:**
> When you installing system onto USB stick there was a page in install about page 8 where 
there is an advanced tab in lower right. When you click that tab it asks you where you want to
install /boot. It has a default of sda and you have to change to your usb what ever sxx that 
If not it loads where it is defaulted.
disk. That is what it looks for boots then loads grub2 at that time when you update and upgrade. That is if you changed the advanced tab to sxx (your usb stick) if not it is going to be loaded onto sda.  There is no way I have found for USB not go to MBR in ext3 or ext4 with persistence. Of course regular USB Live CD install in fat32 gives you 4 gig persistence without going to MBR. Any way no matter what at one time or another grub2 was going to be installed in your MBR. Been there done that with 16 gig sticks. Nice if you are just going to use on your machine and you already have grub2 installed. You got all the fixes from previous posts but will work, just do not use on friends machine without a grub2 or you are going to have one unhappy friend.

The USB install is on a 750 GB USB not a thumb drive. He used the thumb drive to install. refer to the boot info script output.

---

### Post by djchandler on 2010-01-24
Okay, fine you guys are right and I'm wrong on this. Sorry, I have a bit of a problem remembering some things of late, especially when reinforcement of such comes in such a delayed fashion. I've moved on, realizing ubuntu is being geared more for newer hardware. If somebody has older hardware, Ubuntu probably isn't the right choice for that hardware. I have 3 machines now running 9.10, all newer or top drawer hw to begin with.

But I finally got a response to the bug report I filed back a couple of months ago. Here's the body of the email received from launchpad this AM.

```
*** This bug is a duplicate of bug 500791 ***
    https://bugs.launchpad.net/bugs/500791

** This bug has been marked a duplicate of bug 500791
   package grub-pc 1.97~beta4-1ubuntu4.1 failed to install/upgrade: subprocess installed
post-installation script returned error exit status 1

-- 
package grub-pc 1.97~beta4-1ubuntu4 failed to install/upgrade: subprocess installed
post-installation script returned error exit status 1
https://bugs.launchpad.net/bugs/487446
You received this bug notification because you are a direct subscriber
of the bug.

```

To me that means some things should be working, perhaps even as I suggested to the OP, but are not. As I said in my previous post, solving such a problem as the OP's, regardless of the fact that kansasnoob's procedure will (probably) work if the OP can follow his instructions, shouldn't be quite so arcane. This kind of problem has to be fixable by common users using common means without having to enlist code maintainers, developers, etc. or what ever your status, kansasnoob and presence1960, happens to be.

---

### Post by kansasnoob on 2010-01-24
> **djchandler said:**
> Okay, fine you guys are right and I'm wrong on this. Sorry, I have a bit of a problem remembering some things of late, especially when reinforcement of such comes in such a delayed fashion. I've moved on, realizing ubuntu is being geared more for newer hardware. If somebody has older hardware, Ubuntu probably isn't the right choice for that hardware. I have 3 machines now running 9.10, all newer or top drawer hw to begin with.

But I finally got a response to the bug report I filed back a couple of months ago. Here's the body of the email received from launchpad this AM.

```
*** This bug is a duplicate of bug 500791 ***
    https://bugs.launchpad.net/bugs/500791

** This bug has been marked a duplicate of bug 500791
   package grub-pc 1.97~beta4-1ubuntu4.1 failed to install/upgrade: subprocess installed
post-installation script returned error exit status 1

-- 
package grub-pc 1.97~beta4-1ubuntu4 failed to install/upgrade: subprocess installed
post-installation script returned error exit status 1
https://bugs.launchpad.net/bugs/487446
You received this bug notification because you are a direct subscriber
of the bug.

```

To me that means some things should be working, perhaps even as I suggested to the OP, but are not. As I said in my previous post, solving such a problem as the OP's, regardless of the fact that kansasnoob's procedure will (probably) work if the OP can follow his instructions, shouldn't be quite so arcane. This kind of problem has to be fixable by common users using common means without having to enlist code maintainers, developers, etc. or what ever your status, kansasnoob and presence1960, happens to be.

Not that it really matters at this point because the OP quit responding, but things were not that difficult to understand in that situation.

The OP had Ubuntu w/legacy grub on the internal. (S)he installed Ubuntu w/grub2 on the external but let grub2 install to the mbr of the internal drive.

So the legacy grub mbr had to be restored on the internal, and the grub2 mbr had to be installed to the external. No bug to it.

If someone is working with more than one drive they must use the "Advanced" option at the end of the installation to assure that grub (either version) is installed to the mbr of the correct drive.

---

### Post by darkod on 2010-01-24
> **kansasnoob said:**
> 
If someone is working with more than one drive they must use the "Advanced" option at the end of the installation to assure that grub (either version) is installed to the mbr of the correct drive.

I have to add to this: instead of hoping (thinking) that grub will go where they wanted.

---

### Post by djchandler on 2010-01-24
> **kansasnoob said:**
> If someone is working with more than one drive they must use the "Advanced" option at the end of the installation to assure that grub (either version) is installed to the mbr of the correct drive.

That's something that differs significantly from Debian. Ubuntu is not consistent with its upstream distribution in this regard, as Debian *always* asks if you want GRUB installed on the drive where the installation just took place. Ubuntu tries so hard sometimes to make things simple it can sometimes actually complicate things way more than distributions that have a reputation for being much less user friendly. How is the OP or someone of like experience supposed to know when to use the "advanced" option if they are in fact a novice?

As for the more than one drive issue, that certainly complicated matters way beyond anything I've dealt with. You guys were acting properly in correcting me. On top of that, the OP did something most of us would never consider letting happen in the first place. 

Thanks for jumping in and sharing your knowledge.

---

### Post by kansasnoob on 2010-01-24
Well the Debian installer and Ubuntu's Alternate CD's work almost identically. No doubt the Alternate provides more options, such as being able to install lilo as an option.

---

### Post by darkod on 2010-01-24
> **djchandler said:**
> That's something that differs significantly from Debian. Ubuntu is not consistent with its upstream distribution in this regard, as Debian *always* asks if you want GRUB installed on the drive where the installation just took place. Ubuntu tries so hard sometimes to make things simple it can sometimes actually complicate things way more than distributions that have a reputation for being much less user friendly. How is the OP or someone of like experience supposed to know when to use the "advanced" option if they are in fact a novice?

As for the more than one drive issue, that certainly complicated matters way beyond anything I've dealt with. You guys were acting properly in correcting me. On top of that, the OP did something most of us would never consider letting happen in the first place. 

Thanks for jumping in and sharing your knowledge.

The thing is there will always be "problems" and complaints, regardless what you do. This situation is strange for you but on the other hand I've seen the opposite here on this forum. People asking where is my ubuntu. Grub went to the ubuntu disk (which is the correct way in most cases), but they left their windows disk first in boot order and windows boots right away as if you never installed ubuntu. So they don't know if it was installed at all.

I guess because of this fact, windows does similar (not that I like comparing linux to it). It always installs the bootloader to the disk first in boot order. I guess the developers decided if that is the disk you set as first, you want to boot from it, hence that's where the bootloader should go.
On similar note, have you ever seen a message in any windows asking you if you want bootloader installed and on which disk?

And another thing you were right to mention. NOVICES. How would they know about Advanced options? Quite right, but what is a novice to OS installation/partitioning/etc doing installing an OS in the first place?
Not that I'm not encouraging new things, but if you don't get informed in advanced, the fault is all yours, sorry. This forum and all like it don't exist just to come with your problems, but to come asking for information before trying anything. Especially if you're unsure. And there's always google. :)

---

### Post by kansasnoob on 2010-01-24
> if you don't get informed in advanced

+1!

I learned 90% of what I know here:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

At first I thought my brain would explode, but it didn't :P

---

### Post by richardlikeslinux on 2010-01-25
My GRUB/MBR problem may be related, please help - minimal-effort advice most appreciated! I've been using linux for about 10 years but have steered clear of messing with boot loaders!

Brand new Acer AO532h-2Bb netbook with Win XP. Created a bootable 4GB USB thumbdrive with full (not UNR) Ubuntu 9.10. My first mistake was not setting the BIOS to boot off USB, naively assuming all modern netbooks would. Next mistake was running the wubi.exe on the USB from XP, which downloaded 9.10 (rather than installing off USB) & appeared to install OK on the internal HDD. But on reboot, selecting "ubuntu" ends up stuck in a sh:grub> menu. Typing     exit 
gives "no bootable device ...". Boots fine off the USB (now I've set the BIOS) or into XP. 

 If I just install off the USB (an option which *is* presented now I've set BIOS) will it mess things up further?

Diagnostic dumps from the USB OS below & attached (sorry for verbosity). 

Richard.

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   3014148     69622   2787240   3% /
udev                    507908       260    507648   1% /dev
/dev/sdb1              3910112   3852052     58060  99% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                    507908       716    507192   1% /dev/shm
tmpfs                   507908       124    507784   1% /tmp
none                    507908        88    507820   1% /var/run
none                    507908         0    507908   0% /var/lock
none                    507908         0    507908   0% /lib/init/rw

ubuntu@ubuntu:~$ sudo bash /tmp/boot_info_script048.sh
Identifying MBRs...

Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda2/Wubi for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS.txt located in /tmp      ... see attached.

---

### Post by presence1960 on 2010-01-25
> **richardlikeslinux said:**
> **_ minimal-effort advice most appreciated!_** I've been using linux for about 10 years but have steered clear of messing with boot loaders!

So if the fix involves more than minimal effort you don't want to fix it? I saw that and didn't even bother to look at the rest of your info and boot info script results.

---

### Post by darkod on 2010-01-25
Boot into XP and in add/remove programs there will be 'ubuntu' entry (for wubi). Remove (uninstall) as you would any windows app.

This should also remove the ubuntu line from XP bootloader, but sometimes it doesn't. In that case open C:\boot.ini and delete ubuntu line youself.

That will get rid of wubi. From there proceed as you planned, but this time boot from the usb stick.

---

### Post by richardlikeslinux on 2010-01-25
Darkod,

Thanks very much!  XP uninstall worked. The boot loader was still there as you foreshadowed. 

boot.ini (visible only from usb-ubuntu) is below - do I just delete the last line?

Richard

```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

```

---

### Post by richardlikeslinux on 2010-01-26
Confirmed - removed ubuntu ref in boot.ini, then installed from bootable usb. Correct boot loader functioning.

Moral - always check the BIOS boots from USB first before installing from USB.

Richard.

---

