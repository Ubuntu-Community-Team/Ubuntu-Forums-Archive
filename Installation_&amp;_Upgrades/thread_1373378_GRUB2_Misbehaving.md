---
title: "GRUB2 Misbehaving"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by boosterjet on 2010-01-05
I have a two hard drive set-up with Windows XP on a 160GB and just recently installed Ubuntu on the second 80GB drive. I did post this problem on the general help forum but no one has been able to come up with an answer to my problem of getting Windows as my first boot priority. After a lot more reading I think my GRUB is not working properly. After many attempts at reconfiguring it will not change from the the first boot preference of "linux,etc". Below you can see a copy of my GRUB menu and I have tried to make it boot 2nd Linux and Mem on start up. The config file will show the selected item as boot preference- up-date- nothing changes. The GRUB update file does not even recognise Windows. For your info here is my GRUB index 

                                 john@john-desktop:~$ grep "menuentry" /boot/grub/grub.cfg  
 menuentry "Ubuntu, Linux 2.6.31-16-generic" {  
 menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {  
 menuentry "Ubuntu, Linux 2.6.31-14-generic" {  
 menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {  
 menuentry "Memory test (memtest86+)" {  
 menuentry "Memory test (memtest86+, serial console 115200)" {  
 menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {  
 john@john-desktop:~$  
 

 To show that the config file has properly been edited this was one attempt-



                                  # If you change this file, run 'update-grub' afterwards to update  
 # /boot/grub/grub.cfg.  
 

 GRUB_DEFAULT="Microsoft Windows Home Edition (on /dev/sda1)"  
 #GRUB_HIDDEN_TIMEOUT=0  
 GRUB_HIDDEN_TIMEOUT_QUIET=true  
 GRUB_TIMEOUT=10  
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`  
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
 GRUB_CMDLINE_LINUX=""  
 

 # Uncomment to disable graphical terminal (grub-pc only)  
 #GRUB_TERMINAL=console  
 

 # The resolution used on graphical terminal  
 # note that you can use only modes which your graphic card supports via VBE  
 # you can see them in real GRUB with the command `vbeinfo'  
 #GRUB_GFXMODE=640x480  
 

 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux  
 #GRUB_DISABLE_LINUX_UUID=true  
 

 # Uncomment to disable generation of recovery mode menu entrys  
 #GRUB_DISABLE_LINUX_RECOVERY="true"
  
 

And after update the update file


                                  john@john-desktop:~$ gksu gedit /etc/default/grub  
 john@john-desktop:~$ sudo update-grub  
 Searching for GRUB installation directory ... found: /boot/grub  
 Searching for default file ... found: /boot/grub/default  
 Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst  
 Searching for splash image ... none found, skipping ...  
 Found kernel: /boot/vmlinuz-2.6.31-16-generic  
 Found kernel: /boot/vmlinuz-2.6.31-14-generic  
 Found GRUB 2: /boot/grub/core.img  
 Found kernel: /boot/memtest86+.bin  
 Updating /boot/grub/menu.lst ... done  
 

As you can see no mention of Windows and it won't change the initial boot anyway.


Any suggestions. Many thanks John :confused:

---

### Post by kansasnoob on 2010-01-05
In one place you mention grub.cfg and in another you mention menu.lst so you might have mixed legacy grub and grub2 files/directories. If "update-grub finds a menu.lst in /boot/grub then grub.cfg will not update properly.

In order to save us loads of time please post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by boosterjet on 2010-01-05
Okay, I'll go off and do that, however, my release is less than a week old and shows Grub version 1.97~beta4 so I'm sure it is Grub2.

---

### Post by kansasnoob on 2010-01-05
> **boosterjet said:**
> Okay, I'll go off and do that, however, my release is less than a week old and shows Grub version 1.97~beta4 so I'm sure it is Grub2.

But this shows a menu.lst:

> john@john-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
**[COLOR="Red"]Updating /boot/grub/menu.lst ... done[/COLOR]** 

I don't know why it would be borked for sure.

One common way I've noticed is that people try to follow old guides where you have to go to a grub shell, but "sudo grub" says grub not installed. Then people install the package grub and later find out they borked things.

---

### Post by boosterjet on 2010-01-05
OK here goes there is a lot here 

  	 	 	 	 	 	  ============================ Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=39d07360-f5a2-4abe-a10e-a041151af2f8)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

   File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

   File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                      /boot/grub/core.img

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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5f2d5f2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1f4c1f4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   153,693,854   153,693,792  83 Linux
/dev/sdb2         153,693,855   156,296,384     2,602,530   5 Extended
/dev/sdb5         153,693,918   156,296,384     2,602,467  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="D060C9B760C9A516" TYPE="ntfs" 
sdb1: UUID="39d07360-f5a2-4abe-a10e-a041151af2f8" TYPE="ext4" 
sdb5: UUID="aa4c32e7-186e-49fc-90b0-a1f1abce32e8" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


================================ sda1/boot.ini: ================================

[boot loader]
 timeout=30 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39d07360-f5a2-4abe-a10e-a041151af2f8

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		39d07360-f5a2-4abe-a10e-a041151af2f8
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 39d07360-f5a2-4abe-a10e-a041151af2f8
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 39d07360-f5a2-4abe-a10e-a041151af2f8
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 39d07360-f5a2-4abe-a10e-a041151af2f8
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 39d07360-f5a2-4abe-a10e-a041151af2f8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 39d07360-f5a2-4abe-a10e-a041151af2f8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d060c9b760c9a516
	drivemap -s (hd0) ${root}
	chainloader +1
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
UUID=39d07360-f5a2-4abe-a10e-a041151af2f8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=aa4c32e7-186e-49fc-90b0-a1f1abce32e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

---

### Post by kansasnoob on 2010-01-05
You see sdb1 shows both a grub.cgf and a menu.lst:

> Boot files/dirs: /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
/boot/grub/core.img

So I'm assuming from your first post you can still boot into Karmic, yes? If I'm mistaken this won't work, it'll require different steps.

If you can boot into your installed Karmic first run this command:

```
grub-install -v
```

If it shows "grub-install (GNU GRUB 1.97~beta4)" then run the following commands (if it shows "0.97" stop and tell me!):

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo update-grub
```

Then follow the appropriate steps in this guide to change default, etc:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2010-01-05
Sheesh! I was asleep at the wheel! I left out:

```
sudo apt-get install --reinstall grub-pc
```

I've fixed that now but I hope I didn't get you unbootable in the meanwhile :(

BTW if I did make you unbootable I can fix it, just boot the Live CD and shout at me very, very loudly!

---

### Post by boosterjet on 2010-01-05
It's showing 0.97??

---

### Post by kansasnoob on 2010-01-05
> **boosterjet said:**
> It's showing 0.97??

Ah, so you did get reverted to legacy grub at some point. We can easily fix it!

I'm almost glad, did you read about my screw-up???????

Give me a few minutes to type and proofread everything, I'll be right back but I want to triple check myself.

That's my second major goof today!

---

### Post by boosterjet on 2010-01-05
Hope it's a KISS solution.

---

### Post by kansasnoob on 2010-01-05
OK here we go, from terminal in your installed Karmic:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Note: The Boot Info Script shows "Grub 1.97 is installed in the MBR of /dev/sda" so we're just making sure it's still put in the same place!

Of course as I said before look at the following guide for info regarding how to change default, etc:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by boosterjet on 2010-01-05
This is what i got from the first try 

john@john-desktop:~$ sudo mv /boot/grub boot/grub_backup
[sudo] password for john: 
mv: cannot move `/boot/grub' to `boot/grub_backup': No such file or directory
john@john-desktop:~$

---

### Post by kansasnoob on 2010-01-05
> **boosterjet said:**
> This is what i got from the first try 

john@john-desktop:~$ sudo mv /boot/grub boot/grub_backup
[sudo] password for john: 
mv: cannot move `/boot/grub' to `boot/grub_backup': No such file or directory
john@john-desktop:~$

Copy-n-paste commands, look mine is on top yours on the bottom:

sudo mv /boot/grub /boot/grub_backup
sudo mv /boot/grub boot/grub_backup

See where you left out a /

Just copy-n-paste please!

---

### Post by kansasnoob on 2010-01-05
BTW for the few changes you want to make, once we have /boot/grub fixed try just installing Startup Manager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup Manager.

It'll let you change a few simple things like default boot, timeout, etc.

---

### Post by boosterjet on 2010-01-05
OK heres what happened. I'm not game to leave the OS in case I can't get back

john@john-desktop:~$ sudo mv /boot/grub /boot/grub_backup
john@john-desktop:~$ sudo mkdir /boot/grub
john@john-desktop:~$ sudo apt-get --purge remove grub grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu linux-headers-2.6.31-14 libinklevel5 blt python-tk lesstif2 tcl8.5
  tk8.5 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4,461kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 138976 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
john@john-desktop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-ieee1275 grub-efi-ia32 grub-efi-amd64 grub-coreboot
E: Package grub-pc has no installation candidate
john@john-desktop:~$ sudo update-grub
sudo: update-grub: command not found
john@john-desktop:~$ sudo grub-install /dev/sda
sudo: grub-install: command not found
john@john-desktop:~$

---

### Post by boosterjet on 2010-01-05
I have startup manager, wouldn't work before

---

### Post by kansasnoob on 2010-01-05
> **boosterjet said:**
> OK heres what happened. I'm not game to leave the OS in case I can't get back

john@john-desktop:~$ sudo mv /boot/grub /boot/grub_backup
john@john-desktop:~$ sudo mkdir /boot/grub
john@john-desktop:~$ sudo apt-get --purge remove grub grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu linux-headers-2.6.31-14 libinklevel5 blt python-tk lesstif2 tcl8.5
  tk8.5 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4,461kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 138976 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
john@john-desktop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-ieee1275 grub-efi-ia32 grub-efi-amd64 grub-coreboot
E: Package grub-pc has no installation candidate
john@john-desktop:~$ sudo update-grub
sudo: update-grub: command not found
john@john-desktop:~$ sudo grub-install /dev/sda
sudo: grub-install: command not found
john@john-desktop:~$

OK this is a problem:

> john@john-desktop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-ieee1275 grub-efi-ia32 grub-efi-amd64 grub-coreboot
E: Package grub-pc has no installation candidate

Must need to update the package list so run:

```
sudo apt-get update
```

Then:

```
sudo apt-get install grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

**I'll hang right here with you until you're done!**

---

### Post by boosterjet on 2010-01-05
No good  - here's the result

john@john-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
john@john-desktop:~$ sudo apt-get install grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-pc grub-ieee1275 grub-emu grub-efi-ia32 grub-efi-amd64 grub-coreboot
E: Package grub-common has no installation candidate
john@john-desktop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by boosterjet on 2010-01-05
Sorry missed the bottom bit 

Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-ieee1275 grub-efi-ia32 grub-efi-amd64 grub-coreboot
E: Package grub-pc has no installation candidate
john@john-desktop:~$ sudo update-grub
sudo: update-grub: command not found
john@john-desktop:~$ sudo grub-install /dev/sda
sudo: grub-install: command not found
john@john-desktop:~$

---

### Post by kansasnoob on 2010-01-05
You have a problem with software sources which explains lots of things. It looks like you're on the Australian server maybe?

Go to System > Administration > Software Sources:

[ATTACH]142621[/ATTACH]

Make sure that's set to Main Server and all 4 of those repos are checked like mine! Also click on the other Softawre tab and make sure the Partner repo is checked. Then click on the Updates tab and make sure the top 2 boxes (security and recommended updates are checked).

When you click on Close another Window will popup, be sure to click on reload and wait till it's done!

Then repeat the steps in post #17.

---

### Post by kansasnoob on 2010-01-05
BTW don't try to reboot until we get this straightened out!

If we must we'll download the .debs of grub-pc (which is grub2) and grub-common.

I noticed people having trouble with the Australian server during Karmic development. You'd think they'd get that fixed.

---

### Post by boosterjet on 2010-01-05
Yeah, I downloaded the file direct from Ubuntu Home so you would expect it to be right. The System has been working fine my only problem has been not able to change the default boot.

---

### Post by kansasnoob on 2010-01-05
> **boosterjet said:**
> Yeah, I downloaded the file direct from Ubuntu Home so you would expect it to be right. The System has been working fine my only problem has been not able to change the default boot.

But when you run apt-get update it's not finding the proper packages. Do what I said with software sources and also make sure the cdrom box is unchecked.

Believe me, the packages grub-pc and grub-common should be there.

---

### Post by kansasnoob on 2010-01-05
Oh and when you choose your locale during installation it determines which server to use.

---

### Post by boosterjet on 2010-01-05
Sorry, my abject apologies, completely missed your post at 20. Did all that and it looks like things happened 

john@john-desktop:~$ sudo apt-get update
[sudo] password for john: 
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                         
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
john@john-desktop:~$ sudo apt-get install grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu linux-headers-2.6.31-14 libinklevel5 blt python-tk lesstif2 tcl8.5 tk8.5 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu
The following NEW packages will be installed:
  grub-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 994kB of archives.
After this operation, 2,417kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub-common 1.97~beta4-1ubuntu3 [994kB]
Fetched 994kB in 4s (210kB/s)       
Selecting previously deselected package grub-common.
(Reading database ... 138779 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu3) ...

john@john-desktop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu linux-headers-2.6.31-14 libinklevel5 blt python-tk lesstif2 tcl8.5 tk8.5 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  grub-pc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 434kB of archives.
After this operation, 1,753kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub-pc 1.97~beta4-1ubuntu3 [434kB]
Fetched 434kB in 4s (103kB/s)   
Preconfiguring packages ...
Selecting previously deselected package grub-pc.
(Reading database ... 138819 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up grub-pc (1.97~beta4-1ubuntu3) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

john@john-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
john@john-desktop:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
(hd0)    /dev/sda
(hd1)    /dev/sdb
john@john-desktop:~$

---

### Post by kansasnoob on 2010-01-05
You know maybe the problem with software sources was just because the Live CD was still in the CD ROM??????????

Maybe?

Grub apps don't exist on the CD.

---

### Post by boosterjet on 2010-01-05
No way, safely tucked away. I'll now see if I can change the default boot. First go will be with the startup manager. Thanks a million for all your time to date. I will return with the good or bad news.

---

### Post by boosterjet on 2010-01-05
Everything works fine. Again many thanks -  John

---

### Post by kansasnoob on 2010-01-05
That looks good except for this:

> W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

Make sure the Karmic CD is not in the drive and that the cdrom box is unchecked in Software Sources.

You notice grub2 found everything now:

> john@john-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
**Found Microsoft Windows XP Home Edition** on /dev/sda1
done
john@john-desktop:~$ sudo grub-install /dev/sda
Installation finished. **No error reported.**
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
(hd0) /dev/sda
(hd1) /dev/sdb

It looks good to me, I'll almost bet Startup Manager would work better now, but you'll have to reinstall it.

Hey, you're a grub pro now!

You can probably change back to the Australian server if you wish (depending on your ISP, some are picky about long distance downloads, etc). Just check out that cdrom thing, it can mess you up for updates and such.

It's shower time for me, I've been wrestling goats most of the day and I smell so bad the dogs don't even like me :P

---

### Post by kansasnoob on 2010-01-05
Oh and please mark this solved. It can be helpful to others with similar problems.

And thanks right back at you. I learned a few things too. Like I'll have people check their package list before beginning.

---

### Post by daltore on 2010-01-06
If you still haven't gotten Windows as your default boot, I may know why.  In /etc/default/grub, you had default boot listed like this:

GRUB_DEFAULT="Microsoft Windows Home Edition (on /dev/sda1)" 

Should it not be like this?:

GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)" 

Typos can make a big difference in computer language.  On the other hand, I only realised Ubuntu 9.10 didn't use the old version of Grub tonight, so I could be wrong.

---

