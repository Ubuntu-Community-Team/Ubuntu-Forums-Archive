---
title: "Grub error 15 after lucid upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by fiftysix on 2010-05-03
Thank you in advance for any help rendered !

Anyhow, I just upgraded from 9.10 and now I cannot boot into 10.04
because of grub error 15; file not found.

I have tried and failed at the following:

1) I did the find /boot/grub/stage1 and got hd0,5.
Checked it against my existing setting and it was fine.

2) Booted through a livecd and found that my boot directory
was almost empty. No sign of vmlinuz and initrd as well.

3) through the livecd, I copied contents of boot into the boot directory
of my existing installation and umm...nothing changed at reboot.

I checked the disk utility in the livecd scenario and it said 10.04 LTS was installed
on my drive but grub only lets me select 9.10 kernels. There is also no sign of vmlinuz and initrd files anywhere (except those I copied from elsewhere).

---

### Post by kansasnoob on 2010-05-03
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2010-05-03
Welcome to the forums.

Error 15 is most common with both grub legacy (0.97) and grub2 installed. They do not like each other.

This will show what is installed where but because you did copy some files it may not be 100%.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by fiftysix on 2010-05-03
Hi guys,

As instructed, my results.txt is as below:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,671,414   102,671,352  83 Linux
/dev/sda2         102,671,415   312,576,704   209,905,290   5 Extended
/dev/sda5         306,568,458   312,576,704     6,008,247  82 Linux swap / Solaris
/dev/sda6    *    102,671,541   300,560,084   197,888,544  83 Linux
/dev/sda7         300,560,148   306,568,394     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F47470BA74708162                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a6da17ee-731d-45f7-88e6-44a75bc94e32   swap                                     
/dev/sda6        8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d   ext3                                     
/dev/sda7        9de38e8d-e2f3-4c69-b94c-9650accb5aeb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 9.10, kernel 2.6.31-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.24-24-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 9.10, kernel 2.6.24-23-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 9.10, kernel 2.6.24-22-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 9.10, kernel 2.6.24-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 9.10, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d ro  single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8a2dfd2d-4f1b-4423-804c-5d6bdb0d001d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=9de38e8d-e2f3-4c69-b94c-9650accb5aeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  92.7GB: boot/grub/menu.lst
  71.2GB: boot/grub/stage2


```

---

### Post by kansasnoob on 2010-05-03
> **fiftysix said:**
> Thank you in advance for any help rendered !

Anyhow, I just upgraded from 9.10 and now I cannot boot into 10.04
because of grub error 15; file not found.

I have tried and failed at the following:

1) I did the find /boot/grub/stage1 and got hd0,5.
Checked it against my existing setting and it was fine.

2) Booted through a livecd and found that my boot directory
was almost empty. No sign of vmlinuz and initrd as well.

3) through the livecd, I copied contents of boot into the boot directory
of my existing installation and umm...nothing changed at reboot.

I checked the disk utility in the livecd scenario and it said 10.04 LTS was installed
on my drive but grub only lets me select 9.10 kernels. There is also no sign of vmlinuz and initrd files anywhere (except those I copied from elsewhere).

Well you've done a good job of troubleshooting this so far. I'm curious about this:

> There is also no sign of vmlinuz and initrd files anywhere (except those I copied from elsewhere).

So if you navigate to the root filesystem you see no vmlinuz or initrd here:

[ATTACH]155314[/ATTACH]

I'm also curious where you copied from? Anyway this is always worth a look:

[http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

I can't see anything wrong in your menu.lst but sometimes a different pair of eyes can help.

Anyway a few things come to mind, but **[COLOR="Red"]just consider this mostly thinking out loud at this point[/COLOR]**. A lot of this depends on individual skill level so it's best we discuss things before proceeding:D

I multi-boot a lot so I quite often have some "parallel" OS I can copy from, it's especially easy since all OS's have the same root user/privileges, but of course you don't quite have that situation.

Anyway please look at my notes on using a chroot to "fix" things in Ubuntu:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Note: that is written using /dev/sda3 as an example, but your Ubuntu is on /dev/sda6.

One of my first thoughts is that I recently installed a new kernel (2.6.32-22) from the "proposed" repos, specific apt info:

> Commit Log for Fri Apr 30 06:56:28 2010


Upgraded the following packages:
empathy (2.30.0.1-0ubuntu3) to 2.30.1-0ubuntu1
empathy-common (2.30.0.1-0ubuntu3) to 2.30.1-0ubuntu1
file-roller (2.30.0-0ubuntu1) to 2.30.1.1-0ubuntu2
linux-generic (2.6.32.21.22) to 2.6.32.22.23
linux-headers-generic (2.6.32.21.22) to 2.6.32.22.23
linux-image-generic (2.6.32.21.22) to 2.6.32.22.23
nautilus-sendto-empathy (2.30.0.1-0ubuntu3) to 2.30.1-0ubuntu1
unattended-upgrades (0.55ubuntu3) to 0.55ubuntu4

Installed the following packages:
linux-headers-2.6.32-22 (2.6.32-22.33)
linux-headers-2.6.32-22-generic (2.6.32-22.33)
linux-image-2.6.32-22-generic (2.6.32-22.33)


Note that "linux-libc-dev" had come in the day before:

> linux-libc-dev (2.6.32-21.32) to 2.6.32-22.33

So I'm thinking that installing that kernel might initiate the "update" process and sort things out, but that's a big maybe! I'd begin by mounting and chrooting that Ubuntu:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Then I'd explore free disc space to be sure that's not an issue:

```
df -H
```

Note: "df -H" is quite "human readable" :)

```
du -sh /*
```

That takes a while to run so be patient, it gives a more in depth look at disc usage, example:

```
6.7M	/bin
33M	/boot
4.0K	/cdrom
492K	/dev
15M	/etc
du: cannot access `/home/lance/.gvfs': Permission denied
273M	/home
0	/initrd.img
0	/initrd.img.old
217M	/lib
16K	/lost+found
8.0K	/media
7.2G	/mnt
29M	/opt
du: cannot access `/proc/6849/task/6849/fd/4': No such file or directory
du: cannot access `/proc/6849/task/6849/fdinfo/4': No such file or directory
du: cannot access `/proc/6849/fd/4': No such file or directory
du: cannot access `/proc/6849/fdinfo/4': No such file or directory
0	/proc
1.5M	/root
6.7M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
60K	/tmp
2.3G	/usr
743M	/var
0	/vmlinuz
0	/vmlinuz.old

```

Regardless of what that shows I believe I'd clean up any old .debs (whether in use or not):

```
apt-get autoclean
```

```
apt-get clean
```

Now you might just try a combination of the following:

```
apt-get update
```

```
apt-get dist-upgrade
```

```
apt-get -f install
```

```
dpkg --configure -a
```

```
update-grub
```

Note: "update-grub" may (or may not) give some good clues!

Also if you want to try that newest kernel in "proposed" you need to be sure you have that newest version of "linux-libc-dev":

```
aptitude show linux-libc-dev|head -4
```

Note that "aptitude show <package-name>|head -4" works with any package, and if you'd want to see all info on a package just use "aptitude show <package-name>". Example:

```
lance@lance-desktop:~$ aptitude show linux-libc-dev|head -4
Package: linux-libc-dev
State: installed
Automatically installed: no
Version: 2.6.32-22.33

```

And you will of course have to "activate" the proposed repos in "/etc/apt/sources.list". I've found gedit not to work very well in a chroot so I normally use nano, but nano can be a bit tricky if you've never used it. Have you used nano before?

I always like to begin by running "cat /etc/apt/sources.list" and then copy-n-pasting that output into a simple text doc so I have it as a backup in case I hose things :)

Anyway if you know what I mean by "uncommenting" the "proposed repos", using nano, etc. remember you'll have to run "apt-get update" and "apt-get dist-upgrade" again to install those proposed updates.

Have I completely lost you yet?

Remember when you're done in the chroot to exit and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

---

### Post by fiftysix on 2010-05-03
Hey kansasnoob,

Yes ! that chrooting procedure solved it for me.

I just had to update the kernel I think. Oh and about the vmlinuz and initrd, I realised
that I didnt actually copy the actual files from anywhere, the ones I copied were actually shortcuts
in my root directory. Haha.

Well, basically I just mounted and chrooted and blah blah and rebooted and Wala!

I greatly appreciate your help on this, I was like minutes away from backing up some data and reformatting
the whole drive!.

Thanks again and cheers!

---

### Post by kansasnoob on 2010-05-04
Cool! If you happen to pop back in would you mark this solved?

Edit: I see you already did ........... must drink more coffee ;^)

---

### Post by muddysmind on 2010-06-06
Having a similar issue however mine is from a seemingly bad auto update of the kernel today, still using 9.10 and it upgraded to the latest 2.6.31 kernel.
Now getting the Grub Error 15, using 0.97 version

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

md6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00069e1c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sda2           1,959,930     5,863,724     3,903,795  82 Linux swap / Solaris
/dev/sda3           5,863,725    72,453,149    66,589,425  fd Linux raid autodetect
/dev/sda4          72,453,150   390,716,864   318,263,715  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00069e1c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdb2           1,959,930     5,863,724     3,903,795  82 Linux swap / Solaris
/dev/sdb3           5,863,725    72,453,149    66,589,425  fd Linux raid autodetect
/dev/sdb4          72,453,150   390,716,864   318,263,715  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/md5         ca2870aa-2afd-4606-b96a-108ddd8b18df   reiserfs                                 
/dev/md6         77ea8699-c580-4da8-ab56-8649962998f3   reiserfs                                 
/dev/sda1        783856a9-464c-628b-61c4-1db844858d03   linux_raid_member                               
/dev/sda2        60376b15-45a8-43c1-abce-52ea7f029201   swap                                     
/dev/sda3        ab27d56d-fb1c-f5a9-765d-e02306028b5b   linux_raid_member                               
/dev/sda4        781244f2-7c60-bc8d-cdb4-487458e4e875   linux_raid_member                               
/dev/sdb1        783856a9-464c-628b-61c4-1db844858d03   linux_raid_member                               
/dev/sdb2        91bb84ee-79fd-419c-957f-fd6bfbf30a1b   swap                                     
/dev/sdb3        ab27d56d-fb1c-f5a9-765d-e02306028b5b   linux_raid_member                               
/dev/sdb4        781244f2-7c60-bc8d-cdb4-487458e4e875   linux_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md6         /                        reiserfs   (rw)
/dev/md5         /boot                    reiserfs   (rw)


============================== md5/grub/menu.lst: ==============================

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
# kopt=root=/dev/md6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-22-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-22-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-21-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-21-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-16-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-16-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-15-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-15-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/md6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/md6 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

==================== md5: Location of files loaded by Grub: ====================


    ??GB: grub/menu.lst
    ??GB: grub/stage2
    ??GB: initrd.img-2.6.28-16-generic
    ??GB: initrd.img-2.6.31-14-generic
    ??GB: initrd.img-2.6.31-15-generic
    ??GB: initrd.img-2.6.31-16-generic
    ??GB: initrd.img-2.6.31-17-generic
    ??GB: initrd.img-2.6.31-19-generic
    ??GB: initrd.img-2.6.31-20-generic
    ??GB: initrd.img-2.6.31-21-generic
    ??GB: initrd.img-2.6.31-22-generic
    ??GB: vmlinuz-2.6.28-16-generic
    ??GB: vmlinuz-2.6.31-14-generic
    ??GB: vmlinuz-2.6.31-15-generic
    ??GB: vmlinuz-2.6.31-16-generic
    ??GB: vmlinuz-2.6.31-17-generic
    ??GB: vmlinuz-2.6.31-19-generic
    ??GB: vmlinuz-2.6.31-20-generic
    ??GB: vmlinuz-2.6.31-21-generic
    ??GB: vmlinuz-2.6.31-22-generic

================================ md6/etc/fstab: ================================

# /etc/fstab:       static file system information
proc     /proc     proc     defaults     0 0  

# /dev/md6
UUID=77ea8699-c580-4da8-ab56-8649962998f3     /     reiserfs     defaults     0 1

# /dev/md5
#UUID=783856a9-464c628b-61c41db8-44858d03     /boot     reiserfs     defaults     0 2

# /dev/md4
UUID=b5c18a4e-9256-4e87-93ae-a7fbe5f36bd9     /home     reiserfs     defaults     0 0

# swap
/dev/sda2     none     swap     sw     0 0 
/dev/sdb2     none     swap     sw     0 0


192.168.1.100:/storage     /home/jeff/storage     nfs timeo=20,rsize=8192,wsize=8192,nosuid 0 0
192.168.1.100:/gnucash     /home/jeff/gnucash     nfs timeo=20,rsize=8192,wsize=8192,nosuid 0 0
192.168.1.100:/storage/backup.corsair     /home/jeff/backup     nfs timeo=20,rsize=8192,wsize=8192,nosuid 0 0
192.168.1.110:/mythtv     /home/jeff/mythbox     nfs timeo=20,rsize=8192,wsize=8192,nosuid 0 0

==================== md6: Location of files loaded by Grub: ====================


    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
=============================== StdErr Messages: ===============================

mdadm: SET_ARRAY_INFO failed for /dev/md4: Device or resource busy
mdadm: md device /dev/md4 does not appear to be active.

```I believe the problem lies that grub shows the menu, knows the files are supposed to be in /boot but can't identify them for some reason.
I am running raid 1 with mdadm setup as you can see.
Any ideas this is my main box and I'm dead in the water w/o it.

Thanks!

My issue was resolved by removing the menu.lst file in /boot/grub and renaming the menu.lst~ file that was there to menu.lst and rebooting.
Seems one of them listed everything as /boot and the other w/o the /boot

---

### Post by rlmcclain on 2010-07-02
I'm running an upgrade 10.04 32bit with and upgraded to grub2 installation. Everything has been fine. Yesterday I updated the system with a group of patches including the a linux upgrade to 2.6.32-23, which requested a reboot. Upon reboot, I received numerous error and X would not start (using a nvidia driver). It appeared that the system was booting using the old grub with a very outdated menu.lst file. I attempted to reinstall / reconfigure grub2 and ended up now with Error 15: file not found. I found this thread and [https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15). I did the steps outlined in the wiki to no avail - still getting the Error 15.  I'm at a loss. Any help would be appreciated.

Rich

Update - I decided to post this as a new thread. It's now been solved.

---

### Post by RJARRRPCGP on 2010-07-02
> **oldfred said:**
> Welcome to the forums.

Error 15 is most common with both grub legacy (0.97) and grub2 installed. They do not like each other.



Looks like that's not the problem. Looks like the kernel is missing.

---

### Post by XxjacexX on 2010-12-11
> **oldfred said:**
> Welcome to the forums.

Error 15 is most common with both grub legacy (0.97) and grub2 installed. They do not like each other.

This will show what is installed where but because you did copy some files it may not be 100%.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

So I have been having a problem where grub won't boot I always have to put in my live USB and boot from first hard drive where it seems like it fixes it but it goes straight to Busybox where i have to reboot and as I reboot i remove the live USB and it boots grub... but that process is annoying so i entered this in terminal
```

$ sudo fdisk -l | grep -i linux

```MY RESULTS
```

/dev/sda1   *           1       29674   238349312   83  Linux
/dev/sda5           29674       30402     5847040   82  Linux swap / Solaris

```I tried to see if maybe i could restore GRUB by doing these steps in terminal
```

Type "grub" which makes a GRUB prompt appear.

Type "find /boot/grub/stage1".

```My results were "Error 15 file not found"

So I just tried this so can someone tell me what all this means???


```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   476,700,671   476,698,624  83 Linux
/dev/sda2         476,702,718   488,396,799    11,694,082   5 Extended
/dev/sda5         476,702,720   488,396,799    11,694,080  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        220731fc-4249-4717-be8f-c757249eda2f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a9a845d8-9c1a-4d3e-a5b3-1a69229a7d95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=220731fc-4249-4717-be8f-c757249eda2f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 131.1GB: boot/grub/core.img
 129.1GB: boot/grub/grub.cfg
 131.1GB: boot/initrd.img-2.6.32-24-generic
 131.1GB: boot/initrd.img-2.6.32-26-generic
 131.1GB: boot/vmlinuz-2.6.32-24-generic
 131.1GB: boot/vmlinuz-2.6.32-26-generic
 131.1GB: initrd.img
 131.1GB: initrd.img.old
 131.1GB: vmlinuz
 131.1GB: vmlinuz.old

```

---

