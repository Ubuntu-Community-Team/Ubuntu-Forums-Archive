---
title: "reinstall without data loss"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by nategerr on 2009-12-23
Well, I really screwed up this machine of mine. I was innocently playing around with the  resolution and now can't see anything past the splash screen. to make matters worse, I sudoed the hell out of my menu.lst file too. I've decided that going with a fresh install is the easiest, surest way of solving all my problems and upgrading from Jackalope to Koala in one fell swoop. Will this new version of Ubuntu preserve my data files? Ive tried copying them off the computer while booting from the cd but I don't have permission to copy or back up anything. if there is a command in the terminal to copy these to a usb storage device could someone please let me know?

---

### Post by mörgæs on 2009-12-23
Data in /home will be lost, unless /home sits on a partition separate from the rest of the system.

Am I getting this right: When you boot from the live cd, you can't write to the USB drive?

---

### Post by taurus on 2009-12-23
Just run nautilus with root privilege from the LiveCD and you should be able to write to your USB external drive.

```
gksudo nautilus
```

---

### Post by nategerr on 2009-12-23
The home folder still contains the pictures and music but permission is denied when I attempt to move, copy or view the files while loaded from the CD. I'll try nautilus thought adn let you know how it goes. thanks

---

### Post by nategerr on 2009-12-23
I tried nautilus and got the following error message. Gksudo:5616 :GTK WARNING **:cannot open display 

any ideas or can you give me an idea of what to type in the terminal to reload my menu.lst file. is it possible to replace it directly from the CD? That might do the trick
Thanks

---

### Post by presence1960 on 2009-12-23
> **nategerr said:**
> I tried nautilus and got the following error message. Gksudo:5616 :GTK WARNING **:cannot open display 

any ideas or can you give me an idea of what to type in the terminal to reload my menu.lst file. is it possible to replace it directly from the CD? That might do the trick
Thanks

[http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)  - for backtrack linux to move your data if the Live CD does not work for you.

As far as editing your menu.lst I need loads of info, so do this: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nategerr on 2009-12-24
```
[CODE][CODE]============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1afc1afb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,324,359   153,324,297  83 Linux
/dev/sda2         153,324,360   156,296,384     2,972,025   5 Extended
/dev/sda5         153,324,423   156,296,384     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="bf366be9-97cc-41d5-af60-4fccdf5576ab" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="93011f6c-3ffe-4e9f-9401-a819f3c95f85" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bf366be9-97cc-41d5-af60-4fccdf5576ab ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf366be9-97cc-41d5-af60-4fccdf5576ab

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        bf366be9-97cc-41d5-af60-4fccdf5576ab
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=bf366be9-97cc-41d5-af60-4fccdf5576ab ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        bf366be9-97cc-41d5-af60-4fccdf5576ab
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=bf366be9-97cc-41d5-af60-4fccdf5576ab ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        bf366be9-97cc-41d5-af60-4fccdf5576ab
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=bf366be9-97cc-41d5-af60-4fccdf5576ab ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, memtest86+
uuid        bf366be9-97cc-41d5-af60-4fccdf5576ab
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bf366be9-97cc-41d5-af60-4fccdf5576ab /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=93011f6c-3ffe-4e9f-9401-a819f3c95f85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-12-24
I can see you got to 9.10 from a dist-upgrade from 9.04. Personally I would save my data and do a clean install of 9.10. I am not a fan of dist-upgrades, for some people they cause a lot of problems.

If for some reason you can not run in terminal ```
gksu nautilus
``` to be sure copy the command from here and paste it into terminal to make sure it wasn't a mistype on your part, download backtrack linux from my previous post. it works great. I use it a lot to recover data from clients windows machines that will not boot. Then reinstall using 9.10 Live CD.

---

