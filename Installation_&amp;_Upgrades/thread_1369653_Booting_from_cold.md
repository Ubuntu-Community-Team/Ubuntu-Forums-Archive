---
title: "Booting from cold"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by fnoren on 2010-01-01
I have a problem when booting my computer from cold.
Previously i had Ubuntu and Windows side by side and always arrived at the prompt where to choose os, so no issues there.
Now with only Ubuntu installed, when starting from cold it comes up to the black and white logo which then disappears after 5 seconds, then a small cursor up in the top left corner and then nothing. The hard drive is working all during this process.

If i however do an F12 during startup and accept the first option "1. Normal" it boots without a problem. Likewise I can choose the 2nd option "2. Hard-Disk Drive C:" where I am then also given the alternative to run Ubuntu in Ubuntu, Linux 2.6.31-16-generic, Ubuntu, Linux 2.6.31-16-generic (recovery mode), Ubuntu, Linux 2.6.31-14-generic or Ubuntu, Linux 2.6.31-14-generic, (recovery mode). This also works quite fine.
I can also without problems reboot from the live system.

In bios I have deactivated all other options (such as CD, USB etc) than to boot on the hard drive

I have tried reinstalling the ISO with the same result. The same image worked quite fine with another computer on my network so that should at least not be the problem.

Any advice (understanding that i am still a novice with Ubuntu) is much appreciated.
Fredrik

---

### Post by SecretCode on 2010-01-01
I don't think there's anything wrong with the BIOS options (I presume that's what F12 takes you to). Instead, something is up with the Grub bootloader. Although there is a Grub somewhere on the disk, because you're getting that list of alternative kernels.

I think what we need ... this is the first time I have asked for this :) ... is the output from boot_info_script. Instructions from this thread: [Boot Info Script: How to](http://ubuntuforums.org/showthread.php?t=1291280)

> **louieb said:**
> How to get it - Download it from here. [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

How to run it:  
From a live Ubuntu CD:
Open a terminal window - Applications>Accessories>Terminal 

Type or cut n paste the following. 
```
sudo bash ~/Desktop/boot_info_script*.sh
```[COLOR=Purple]Update Karmic Live CD users [/COLOR]- the default download directory is now Downloads 
```
sudo bash ~/Downloads/boot_info_script*.sh
```

From your Ubuntu hard drive install:
Same as above unless you have changed the Firefox default download location. Then change the **~/Desktop/** part of the command to your download directory. 

You will be asked for a password - your user password. You will not see the cursor move or see any stars as you type - thats the way of the Linux terminal. Type it in and press enter.

Where to find its output: 
The script creates file RESULTS.TXT in same directory it is stored in. ~/Desktop 

Add it to your post:
Open RESULTS.TXT in your favorite text editor - cut and paste - it can be long please use code tags (the # on the tool bar) or add the file as an attachment.

---

### Post by fnoren on 2010-01-01
Thanks for advice, this is what i came up with

                                                                     
                                                                     
                                                                     
                                             
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,830,954    78,830,892  83 Linux
/dev/sda2          78,830,955    80,292,869     1,461,915   5 Extended
/dev/sda5          78,831,018    80,292,869     1,461,852  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="362dd957-7258-42c3-898f-3a596d7d0990" TYPE="ext4" 
sda5: UUID="616bee48-09c9-4c25-bb49-92be6e56bc71" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/olof/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=olof)


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
search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=362dd957-7258-42c3-898f-3a596d7d0990 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=362dd957-7258-42c3-898f-3a596d7d0990 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=362dd957-7258-42c3-898f-3a596d7d0990 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=362dd957-7258-42c3-898f-3a596d7d0990 ro single 
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
if [ ${timeout} != -1 ]; then
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
UUID=362dd957-7258-42c3-898f-3a596d7d0990 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=616bee48-09c9-4c25-bb49-92be6e56bc71 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

---

### Post by SecretCode on 2010-01-01
All that boot info looks fine ... so I looked more closely at your OP. I missed the fact that you actually get the white Ubuntu logo, meaning that the boot process is starting, and grub2 is installed and working fine. (Now you have only one OS, grub doesn't offer the prompt - even though you have multiple kernels.)

I'm not sure why it should work when you boot other ways, though. I would suspect different boot options being passed on the linux boot command line, but I can't see why that would happen.

Try a cold boot with the shift key pressed down (this is supposed to force the grub menu to show).

---

### Post by fnoren on 2010-01-01
Yes holding down shift - that gets me to the same menu as if i chose alt 2 after the F12 exercise; Hard-Disk Drive C:, plus two memory tests (memtest86+) and  (memtest86+, serial console 115200)
Makes any sense?

---

### Post by SecretCode on 2010-01-01
I'm stumped. Everything looks fine?

**Can anyone else help?**

---

### Post by fnoren on 2010-01-01
It is a mind-bender for me at least...

---

### Post by fnoren on 2010-01-04
Re the above, i had friend who is very skilled in Unix (not so much Ubuntu) look at my problem and he picked the following;

    
  ### BEGIN /etc/grub.d/10_linux ###
  menuentry "Ubuntu, Linux 2.6.31-16-generic" {
  recordfail=1
  if [ -n ${have_grubenv} ]; then save_env recordfail; fi set quiet=1 insmod ext2 set root=(hd0,1) search --no-floppy --fs-uuid --set 362dd957-7258-42c3-898f-3a596d7d0990
  linux /boot/vmlinuz-2.6.31-16-generic
  root=UUID=362dd957-7258-42c3-898f-3a596d7d0990 ro quiet splash
   
  Remove quiet and splash and regenerate the bootenvironment.


[FONT=Verdana][SIZE=2]Is this something that might remedy the issue and if so how do I do this in Ubuntu?[/SIZE][/FONT]

---

### Post by SecretCode on 2010-01-04
*Is this something that might remedy the issue *
I don't really see how - what will happen is a lot more messages will appear on the screen

*how do I do this in Ubuntu?*
The quick way to do this is to edit the _grub.cfg_ file on the hard disk, find the line 
menuentry "Ubuntu, Linux 2.6.31-16-generic"
(exactly that) then go 6 or 7 lines down, and delete the text 'quiet splash'. 

I don't have time to check at the moment, but you will need to mount the hard disk from the live CD, and I think you will find the file at _/mount/sda1/boot/grub/grub.cfg_. Edit with _sudo gedit_ .

Save and reboot.

---

### Post by fnoren on 2010-01-04
Thanks, i will give it a go tomorrow
best regards
f

---

### Post by SecretCode on 2010-01-05
> **SecretCode said:**
> I don't have time to check at the moment, but you will need to mount the hard disk from the live CD, and I think you will find the file at _/mount/sda1/boot/grub/grub.cfg_. Edit with _sudo gedit_ .

Save and reboot.

I have a bit more time now ... if you mount the hard disk partition using the "Places" menu it will mount at /media/xyz where xyz is the disk label. The command you would need is
```
sudo gedit /media/xyz/boot/grub/grub.cfg
```

---

### Post by bugs6 on 2010-01-05
im having the same issue the cursor in the top corner of a black screen after the ubuntu symbol though i cant seem to boot ubuntu at all it just freezes on that black screen.

Hope someone figures this out soon

---

