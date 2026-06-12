---
title: "Grub2 AGAIN!!!   Multiple drives"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2009-12-07
I've spent days on grub 2 and thought I had a really good grasp, but no!

I have a Dell Dimension desktop with 2 hard drives.  I installed 9.10 as soon as it came out and have been experimenting ever since.  I thought I understood the grub config files and had successfully modified the boot menu.  Amongst other things, I added the text "USE ME" to the default install.

Having finished playing I have tidied up my disks and installed a fresh install of 9.10 on the same disk but different partition; the old 9.10 install remains.

In the new install the only grub change has been to change the boot menu colors; I have not included the text "USE ME" in this install.

When I boot I get the new menu colours but also get the "USE ME" from a previous edit.  This edit is not in my /etc/grub.d files.

The output from update-grub2 is:
 
```
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.31-16-generic 
Found initrd image: /boot/initrd.img-2.6.31-16-generic 
Found memtest86+ image: /boot/memtest86+.bin 
ls: cannot access /media/My: No such file or directory 
Found Microsoft Windows XP Home Edition on /dev/sda1 
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sdb2 
Found Ubuntu 9.10 (9.10) on /dev/sdb3 
done 
```

but the last two lines of the displayed boot menu include the "use me" text and appear to come from the other installs grub.cfg
```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic,    USE ME" {

```

The 8.04 on sdb2 entry is completely lost.

Grub must be sharing information between installs.

Can anyone explain how to get Grub2 to use the new installation files only please?

Grub2 has always been dead slow.  That might be related but I will post the problem as a separate thread.

---

### Post by darkod on 2009-12-07
You said you have two drives. Were you careful where to install the first and second grub2 and which drive are you booting from?
I haven't tried adding 9.10 to existing 9.10 but you might be right. Even if the second grub2 did overwrite the first one, I wouldn't be surprised if it picks up the config file and combine it somehow. Although that would be strange.

---

### Post by darkod on 2009-12-07
In case you want to take a better look in your boot process download the script in my signature and run it. It will create results.txt file with very detailed info about the boot process.
You can also post the content here if you need help with it but please wrap the text in CODE tags to make it easier to read.

---

### Post by PeggySue on 2009-12-07
Hi darkod,

Interesting script!

First I took the defaults foe install and didn't see an option to install Grub to a particular partition.

The script says 
```
 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
```

So grub2 is on the first drive MBR and points to sdb1 UUID...d5e3.  The installs of 9.10 are on sdb1 (new install) and sdb3 (previous install).  That appears to be fine.

The second disk MBR has Grub 1 but appears to point to sdb as well.  That doesn't appear to be so fine!

The boot menu is definitely from the new install (it has the correct menu colors).

Not sure where to go from here.  I can't upload the whole results file; it is 30.1KB.  The limit is 19.5KB.  I will have to have a more thorough read of the results file tomorrow.  Thanks for your help.

---

### Post by darkod on 2009-12-07
So if you try booting from sda where grub2 is, do all menu entries work fine? Is it just USE ME that's making you wonder? Or grub2 menu can't boot some OS?

---

### Post by PeggySue on 2009-12-07
Hi Darko

This is going to sound odd!

Before my original post I opened grub.cfg and used ctrl-f to find the text "use ".  It wasn't there...honest.
Your script says it is there and of course it is.

I have done a reboot and the 8.04 installation is shown on the boot menu but the text "USE ME" is also shown.  I have rechecked and this is definitely not in ANY of the /etc/grub.d files.  It must be coming from a previous install's directory.

In summary all my installations are now visible but the source of the text is unknown.

I will have to figure out what text to use in ${LONGNAME} in my next 30_os-prober change to remove "USE ME".  Should it be the new string including the USE ME or should it be the original longname?  I should be able to figure this out by trial and error.

Thanks.

---

### Post by oldfred on 2009-12-07
Grub2's osprober is good at finding other operating system to list, It must then find your edited version by looking at that install's grub.cfg?

There is a known bug in grub2 that in multidrive installs where the MBR is one drive but Ubuntu is the second drive, grub2 spends an extra 20+ seconds scanning drives. I installed grub2 to my third drive and changed it to boot first and it is a lot quicker.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

My brute force solution is to turn off osprober and copy any useful entries for other systems to 40_custom. Then it is like the old menu.lst that you can edit anything you want in 40_custom. You only need osprober if you add operating systems and want it to make a setting for you.

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

---

### Post by presence1960 on 2009-12-07
> **PeggySue said:**
> Hi darkod,

Interesting script!

First I took the defaults foe install and didn't see an option to install Grub to a particular partition.

The script says 
```
 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3)/boot/grub.
[COLOR="Red"] => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
```

So grub2 is on the first drive MBR and points to sdb1 UUID...d5e3.  The installs of 9.10 are on sdb1 (new install) and sdb3 (previous install).  That appears to be fine.

The second disk MBR has Grub 1 but appears to point to sdb as well.  That doesn't appear to be so fine!

The boot menu is definitely from the new install (it has the correct menu colors).

Not sure where to go from here.  I can't upload the whole results file; it is 30.1KB.  The limit is 19.5KB.  I will have to have a more thorough read of the results file tomorrow.  Thanks for your help.

see the red above. GRUB 0.97 is in sdb and looks in **_boot drive #2_** Boot drive #2 is referring to sda. You probably need to put sda as first in your hard disk boot order so GRUB 2 (GRUB 1.97) will take over when you boot. You keep getting that message you added because GRUB 0.97 is still booting because you have sdb disk as first in hard disk boot order. Go into BIOS and make the sda disk as first in the hard disk boot order. Save changes to CMOS and continue booting. GRUB 2 will then take over instead of GRUB 0.97 (which has your message you added).

Just to be sure can you please post the entire contents of the RESULTS.txt file generated by the script.

P.S,. The option of where to install GRUB is located at the Ready to Install window of the install process. You click advanced and then use the drop down box to select where to install GRUB. See pic below for future reference.

**P.S. #2  you don't have to upload the file produced by the script. open the file and copy all contents by highlighting with your pointer and right click. Choose Copy from context menu that appears. Now come back here and right click and choose Paste from the context menu. Once all text is pasted back here highlight it all again with pointer, then click # in the toolbar at the top. This will put Code tags around the text so it easy to view in here. Click submit and we will have a look.**

---

### Post by PeggySue on 2009-12-07
I like the idea of turning off OS-prober but first I will try and make it work as intended.

My BIOS doesn't allow me to specify drives as in sda or sdb.  I am running a Dell Dimnesion 8300 with A07 BIOS.  I get options:
Drive Configuration:  The Primary master is just HARD DRIVE not sda etc.
Hard Drive Sequence: is System BIOS Drives or USB
Boot Sequence: is Floppy, CD then Hard Disk.

Would physically swapping the drives over be as good?

This is my results.txt:  (sda and sdb are 160GB WD Hard Drives, sdc is WD 320 GB USB "My Book")  (sdb1 is my new 9.10 install, sdb2 is my 8.04 install, sdb3 is my previous 9.10 install.  sda has Windows XP on sda1, my /home and some swap space.)

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa19fa19f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,027,704    78,027,642   7 HPFS/NTFS
/dev/sda2          78,027,705   303,467,849   225,440,145  83 Linux
/dev/sda3         303,467,850   312,576,704     9,108,855   5 Extended
/dev/sda5         303,467,913   312,576,704     9,108,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcaf7caf7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,027,704    78,027,642  83 Linux
/dev/sdb2          78,027,705   195,221,879   117,194,175  83 Linux
/dev/sdb3         195,221,880   292,961,339    97,739,460  83 Linux
/dev/sdb4         292,961,340   312,496,379    19,535,040   5 Extended
/dev/sdb5         292,961,403   312,496,379    19,534,977  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6e23

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BE7C3B1D7C3AD03F" TYPE="ntfs" 
/dev/sda2: UUID="eda15923-9024-441a-ac0b-419ddae669e4" TYPE="ext3" 
/dev/sda5: UUID="68144d8d-bff8-4026-a9dc-e6a84d7f6db7" TYPE="swap" 
/dev/sdb1: UUID="4f7d2b45-eda2-4a42-a656-92d8a112d5e3" TYPE="ext4" 
/dev/sdb2: UUID="1e263d9f-8195-4c98-b0b5-b81b03c084f9" TYPE="ext3" 
/dev/sdb3: UUID="7b243d97-6ae2-4709-8426-7717d45824fe" TYPE="ext4" 
/dev/sdb5: UUID="36159729-7060-432b-abd1-8ce0ec926fc5" TYPE="swap" 
/dev/sdc1: LABEL="My Book" UUID="6B7A-040B" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda2 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/BE7C3B1D7C3AD03F type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/1e263d9f-8195-4c98-b0b5-b81b03c084f9 type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb3 on /media/7b243d97-6ae2-4709-8426-7717d45824fe type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


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
search --no-floppy --fs-uuid --set 4f7d2b45-eda2-4a42-a656-92d8a112d5e3
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
set menu_color_normal=light-cyan/dark-gray
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4f7d2b45-eda2-4a42-a656-92d8a112d5e3
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4f7d2b45-eda2-4a42-a656-92d8a112d5e3
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set be7c3b1d7c3ad03f
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 1e263d9f-8195-4c98-b0b5-b81b03c084f9
	linux /boot/vmlinuz-2.6.24-25-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
	initrd /boot/initrd.img-2.6.24-25-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 1e263d9f-8195-4c98-b0b5-b81b03c084f9
	linux /boot/vmlinuz-2.6.24-25-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
	initrd /boot/initrd.img-2.6.24-25-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic, USE ME (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 7b243d97-6ae2-4709-8426-7717d45824fe
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=7b243d97-6ae2-4709-8426-7717d45824fe ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 7b243d97-6ae2-4709-8426-7717d45824fe
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=7b243d97-6ae2-4709-8426-7717d45824fe ro single
	initrd /boot/initrd.img-2.6.31-16-generic
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
UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=eda15923-9024-441a-ac0b-419ddae669e4 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=68144d8d-bff8-4026-a9dc-e6a84d7f6db7 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=36159729-7060-432b-abd1-8ce0ec926fc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdb2/boot/grub/menu.lst: ===========================

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-24-generic
#quiet

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
#initrd		/boot/initrd.img-2.6.24-24-generic

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-23-generic
#quiet

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
#initrd		/boot/initrd.img-2.6.24-23-generic

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
#initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.3 LTS, memtest86+
#root		(hd1,1)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition  MAPS AND PHOTOS
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-17-generic (on /dev/sda2) 8.04 Old (upgraded system)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-17-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro single 
#initrd		/boot/initrd.img-2.6.20-17-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.20-16-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro single 
#initrd		/boot/initrd.img-2.6.20-16-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro single 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, memtest86+ (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition Very Old Windows System
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sdb3) 7.04 Development
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb3)
#root		(hd1,2)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro single 
#initrd		/boot/initrd.img-2.6.20-16-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
#title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb3)
#root		(hd1,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb3)
#root		(hd1,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro single 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
#title		Ubuntu, memtest86+ (on /dev/sdb3)
#root		(hd1,2)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb2 :
UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=68144d8d-bff8-4026-a9dc-e6a84d7f6db7 none swap sw 0 0
# Entry for /dev/sdb5 :
UUID=e2068918-3db6-4299-8243-69dca387f64c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sdb2: Location of files loaded by Grub: ===================


  39.9GB: boot/grub/menu.lst
  39.9GB: boot/grub/stage2
  39.9GB: boot/initrd.img-2.6.24-19-generic
  39.9GB: boot/initrd.img-2.6.24-19-generic.bak
  39.9GB: boot/initrd.img-2.6.24-21-generic
  39.9GB: boot/initrd.img-2.6.24-21-generic.bak
  39.9GB: boot/initrd.img-2.6.24-22-generic
  39.9GB: boot/initrd.img-2.6.24-22-generic.bak
  39.9GB: boot/initrd.img-2.6.24-23-generic
  39.9GB: boot/initrd.img-2.6.24-23-generic.bak
  39.9GB: boot/initrd.img-2.6.24-24-generic
  39.9GB: boot/initrd.img-2.6.24-24-generic.bak
  39.9GB: boot/initrd.img-2.6.24-25-generic
  39.9GB: boot/initrd.img-2.6.24-25-generic.bak
  39.9GB: boot/vmlinuz-2.6.24-19-generic
  39.9GB: boot/vmlinuz-2.6.24-21-generic
  39.9GB: boot/vmlinuz-2.6.24-22-generic
  39.9GB: boot/vmlinuz-2.6.24-23-generic
  39.9GB: boot/vmlinuz-2.6.24-24-generic
  39.9GB: boot/vmlinuz-2.6.24-25-generic
  39.9GB: initrd.img
  39.9GB: initrd.img.old
  39.9GB: vmlinuz
  39.9GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root=(hd1,3)
search --no-floppy --fs-uuid --set 7b243d97-6ae2-4709-8426-7717d45824fe
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
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic,    USE ME" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 7b243d97-6ae2-4709-8426-7717d45824fe
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7b243d97-6ae2-4709-8426-7717d45824fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 7b243d97-6ae2-4709-8426-7717d45824fe
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7b243d97-6ae2-4709-8426-7717d45824fe ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
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
menuentry "/dev/sda1 Windows XP MAPS AND PHOTOS (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set be7c3b1d7c3ad03f
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set eda15923-9024-441a-ac0b-419ddae669e4
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=eda15923-9024-441a-ac0b-419ddae669e4 ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.04.1, memtest86+ (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set eda15923-9024-441a-ac0b-419ddae669e4
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4f7d2b45-eda2-4a42-a656-92d8a112d5e3
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 4f7d2b45-eda2-4a42-a656-92d8a112d5e3
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4f7d2b45-eda2-4a42-a656-92d8a112d5e3 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 1e263d9f-8195-4c98-b0b5-b81b03c084f9
	linux /boot/vmlinuz-2.6.24-25-generic root=UUID=1e263d9f-8195-4c98-b0b5-b81b03c084f9 ro quiet splash
	initrd /boot/initrd.img-2.6.24-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=7b243d97-6ae2-4709-8426-7717d45824fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=68144d8d-bff8-4026-a9dc-e6a84d7f6db7 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=e2068918-3db6-4299-8243-69dca387f64c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  99.9GB: boot/grub/grub.cfg
  99.9GB: boot/initrd.img-2.6.31-16-generic
  99.9GB: boot/vmlinuz-2.6.31-16-generic
  99.9GB: initrd.img
  99.9GB: vmlinuz
```

---

### Post by darkod on 2009-12-07
> **PeggySue said:**
> I like the idea of turning off OS-prober but first I will try and make it work as intended.

My BIOS doesn't allow me to specify drives as in sda or sdb.  I am running a Dell Dimnesion 8300 with A07 BIOS.  I get options:
Drive Configuration:  The Primary master is just HARD DRIVE not sda etc.
Hard Drive Sequence: is System BIOS Drives or USB
Boot Sequence: is Floppy, CD then Hard Disk.


I am not familiar with Dell BIOS but see if you can change the value of Drive Configuration. They would never be called sda and sdb in any BIOS, but usually it would show the model and size (in your case both internal are same :) ). Just see if that value can be changed and set it to the other one, because you only have 2 drives. It could be called Primary Slave, Secondary Master, or what ever. Look around it.

PS. If you have a manual or a PDF of it for the computer it will probably have more instructions on the BIOS and the settings.

---

### Post by presence1960 on 2009-12-07
> **darkod said:**
> I am not familiar with Dell BIOS but see if you can change the value of Drive Configuration. They would never be called sda and sdb in any BIOS, but usually it would show the model and size (in your case both internal are same :) ). Just see if that value can be changed and set it to the other one, because you only have 2 drives. It could be called Primary Slave, Secondary Master, or what ever. Look around it.

I hear you, both drives are 160 GB so for lack of a better term I used sda, sdb. It is up to the OP to determine which of the drives is which in BIOS.

I would put the sdb disk as first in boot order and install GRUB 2 to MBR of that disk. There has to be a way to alter the order of disk booting whether it be in BIOS ( which is in 99% of cases) or if there are 2 IDE disks either with jumpers or cable select settings. Unfortunately we are not there, the OP must figure this out.

---

### Post by oldfred on 2009-12-07
I looked at Dell's site if it is a Dimension 8300 it is using Cable select. the only way to switch drives to to switch the connectors.

---

### Post by darkod on 2009-12-07
> **oldfred said:**
> I looked at Dell's site if it is a Dimension 8300 it is using Cable select. the only way to switch drives to to switch the connectors.

Not even to make Slave first in BIOS? Geeees, I'm glad I don't have Dell. :)

---

### Post by PeggySue on 2009-12-08
I have triple checked by BIOS and it is not possible to swap the drives.  I can see the disk ID's but there is no option to change their boot priority.

I tried physically swapping the drives over but the BIOS boots from the other disk and that is grub1.  It says 
loading Stage 1.5     then
Grub Loading... please wait
Error 17

Also I'm still trying to get rid of the "USE ME" text in grub.cfg.  I have tried all combinations of text in 30_os-prober but can't change the text in grub.cfg.  I have even added the device text eg.  (/dev/sdb3) to no avail.

I am about to give up on Grub 2.  It is clearly not fit for purpose, it is still beta release after all.  But this is also a problem.  The forum in undecided as to the best way to revert to grub 1 and I can't just ditch Ubuntu, I have persuaded too many people to switch over and they need support.   Very embarrassing!!

Does anyone have any words of inspiration before I do something drastic please?

---

### Post by phillw on 2009-12-08
Hi,

If you head over here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  It contains all about re-installing Grub2, re-configuring it, having 2 drives, removing grub v1.97 and reverting back to grub v0.97 etc. etc. etc.

Regards,

Phill.

---

### Post by PeggySue on 2009-12-08
Thanks phillw.  The revertion to Grub 1 in this link would appear to be my best option.  It looks too simple to be true!!

My Dell is a Dimension 8300 and I tried swapping the drives as per my last post.  I realise now I should have tried setting the jumpers to master/slave rather than cable select.

Thank you to everyone who has helped here.  Your time is appreciated and I'm sorry I let you down by chickening out!

---

### Post by PeggySue on 2009-12-08
A final word.

I have reverted to Grub 1.  The phillw link above is as simple as it looks.  I'm now back to a menu.lst that is so easy to edit; I love it.  Grub2 was a good idea but it just isn't simple enough for the intermediate user.  Goodness knows how beginers are going to get on.

The reboot time is also spectacular.  What more can you ask for?

---

### Post by presence1960 on 2009-12-08
For future reference here is how you change the boot order of your hard disks from the manual for your machine. I got it on Dell website. There has to be a way to change boot order on a computer, it is just a matter of figuring out to do it on each model computer. Scroll down to red for permanent changes to disk order, the top half deals with changes for one boot only.

```
 w w w. d e l l . c o m | s u p p o r t . d e l l . c o m
                                                             Changing Boot Sequence for the Current Boot
                                                             You can use this feature, for example, to tell the computer to boot from the CD drive so  that you can run the Dell Diagnostics on the ResourceCD, but you must set the computer to boot from the hard drive when the diagnostic tests are complete.
                                                              
                                                             
                                                                  Turn on (or restart) your computer.
                                                               1
                                                                  When F2 = Setup, F12 = Boot Menu appears in the upper-right corner of the
                                                               2
                                                                  screen, press <F12>.
                                                                  If you wait too long and the operating system logo appears, continue to wait until you
                                                                  see the Microsoft Windows desktop. Shut down your computer (see page 27) and
                                                                  try again.
                                                                  The Boot Device Menu appears, listing all available boot devices. Each device has a
                                                                  number next to it.
    At the bottom of the menu, enter the number of the device that is to be used for the
 3
    current boot only.
[COLOR="Red"]Changing Boot Sequence for Future Boots
    Enter the system setup program (see page 107).
 1
    Use the arrow keys to highlight the Boot Sequence menu option and press <Enter>
 2
    to access the pop-up menu.
    NOTE: Write down your current boot sequence in case you want to restore it.
    Press the up-and down-arrow keys to move through the list of devices.
 3
    Press the spacebar to enable or disable a device (enabled devices have a checkmark).
 4
    Press plus(+) or minus (-) to move a selected device up or down the list.
 5[/COLOR]

```

---

### Post by PeggySue on 2009-12-09
Thanks for taking the time to look this up but it doesn't change the sequence from one drive to the other, only to choose floppy, HDD etc..

I had to update the BIOS to be able to boot from USB so the manual might not be valid for A07 BIOS.

I have three options:

The Boot Sequence Menu allows you to prioritize Floppy, CD or Hard Drive.

The Hard Disk Drive Sequence allows you to prioritize BIOS devices and USB (That's all BIOS devices grouped on one line.)

Finally the Drive Configuration shows the master and slave with the disk IDs but doesn't allow you to swap them over.

I'll stick with GRUB 1 for now because it is usable by the intermediate user.  It took less than 20 mins to set up a 7 partition, dual drive system.  I'm sure someone will make a GRUB 2 GUI manager, like the Fedora Boot Manager, when GRUB 2 is stable.  When that day comes I'll try again.

---

