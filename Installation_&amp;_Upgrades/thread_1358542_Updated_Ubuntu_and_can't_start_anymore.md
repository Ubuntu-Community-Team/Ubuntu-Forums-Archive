---
title: "Updated Ubuntu and can't start anymore"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Laucien on 2009-12-18
Hey guys, so I updated ubuntu few days ago, and now I can't turn it on any more, when I power up my laptop it gets stuck after ubuntu logo, I can see only that white _ on the top left corner. What should I do?

---

### Post by kansasnoob on 2009-12-18
> **Laucien said:**
> Hey guys, so I updated ubuntu few days ago, and now I can't turn it on any more, when I power up my laptop it gets stuck after ubuntu logo, I can see only that white _ on the top left corner. What should I do?

Really need more info, what version of Ubuntu?

My first thought is that sometimes kernel updates mess with graphics drivers so you might initially need to select an older kernel from the grub menu.

Of course if Ubuntu is the only OS then the menu is probably hidden. With legacy grub (generally Jaunty and prior) you'd press Esc to show the menu during boot, whereas with grub2 (Karmic) you'd have to press the space bar during boot to show the menu.

If you know almost nothing about the installation then let's start by booting a Live CD and from the Live Desktop post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by Laucien on 2009-12-18
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot     Start      End     Blocks    Id   System
/dev/sda1   *          1    29658  238227853+   83   Linux
/dev/sda2          29659    30401    5968147+    5   Extended
/dev/sda5          29659    30401    5968116    82   Linux swap / Solaris
```

I updated version 9.10, you know, when updater appears, no new version.

---

### Post by kansasnoob on 2009-12-18
> **Laucien said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot     Start      End     Blocks    Id   System
/dev/sda1   *          1    29658  238227853+   83   Linux
/dev/sda2          29659    30401    5968147+    5   Extended
/dev/sda5          29659    30401    5968116    82   Linux swap / Solaris
```

I updated from 9.04 to 9.10.

Well I've personally found 9.10/Karmic kind of unstable on my hardware but lets at least try a few things, I also really need to see the results of all of this!. 

From the Live Desktop run the following commands in terminal (please copy-n-paste by double clicking, then right clicking, and choosing copy):

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
grub-install -v
```

```
apt-get update && apt-get upgrade
```

Note: You'll probably be presented with a bunch of updates so say yes, but I really need to see that!

```
cat /etc/apt/sources.list
```

```
cat /boot/grub/menu.lst
```

Then just:

```
exit
```

And:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If you'd like you can try to reboot and see if the updates helped you be able to boot. Otherwise maybe the output from all of that will give me more ideas.

---

### Post by kansasnoob on 2009-12-18
> **Laucien said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot     Start      End     Blocks    Id   System
/dev/sda1   *          1    29658  238227853+   83   Linux
/dev/sda2          29659    30401    5968147+    5   Extended
/dev/sda5          29659    30401    5968116    82   Linux swap / Solaris
```

I updated version 9.10, you know, when updater appears, no new version.

Well you first said:

> I updated from 9.04 to 9.10.

Now you say:

> I updated version 9.10, you know, when updater appears, no new version.

Are you still unable to boot the OS?

---

### Post by Laucien on 2009-12-18
Ok I'm not quite sure what you want me to post now, since mostly after these commands there is nothing to post xD So here are some of them.
After the first 'cat':
> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main # disabled on upgrade to jaunty
# deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main # disabled on upgrade to jaunty

After the second one:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fec6f8e-c706-43bf-bbdc-3ed279788d7c

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
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, memtest86+
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



And when I try the last command, I get:
> umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by Laucien on 2009-12-18
> **kansasnoob said:**
> Well you first said:



Now you say:



Are you still unable to boot the OS?

Yesyes I made a mistake, I updated to 9.10. before this error occured, it happened after the update in 9.10. You know what I mean? The updater popped out and I just updated, but not to a newer version of ubuntu.

---

### Post by Laucien on 2009-12-18
Btw the steps you suggested up there didn't help :(

---

### Post by kansasnoob on 2009-12-18
Well, I really doubted you'd be able to boot after that, but I really wanted to see the output of what happened when you ran "apt-get update && apt-get upgrade"!

What I can see is that you started out with Intrepid at some point and probably upgraded to Jaunty and later to Karmic. I also know you still have legacy grub because you had a menu.lst.

But I said, "**I also really need to see the results of all of this!."** Meaning I really needed to see every bit of text entered & produced in the terminal!

I'm not sure why you got the, "umount: /mnt/proc: device is busy" error. Maybe you forgot to exit? I can't know because you didn't copy-n-paste the full output of the terminal here:(

Without having the computer in front of me I can only depend on you to send me the needed info! If you can't do that I have doubts that I can help you.

---

### Post by Laucien on 2009-12-18
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# grub-install -v
grub-install (GNU GRUB 0.97)
root@ubuntu:/# apt-get update && apt-get upgrade
Hit http://hr.archive.ubuntu.com karmic Release.gpg
Ign http://hr.archive.ubuntu.com karmic/main Translation-en_US      
Ign http://hr.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://hr.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://hr.archive.ubuntu.com karmic/multiverse Translation-en_US 
Get:1 http://security.ubuntu.com karmic-security Release.gpg [189B]  
Ign http://security.ubuntu.com karmic-security/main Translation-en_US   
Hit http://archive.canonical.com karmic Release.gpg                     
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Hit http://hr.archive.ubuntu.com karmic-updates Release.gpg          
Ign http://hr.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://hr.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://hr.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://hr.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com karmic-security Release [44.1kB]    
Hit http://hr.archive.ubuntu.com karmic Release                          
Hit http://archive.canonical.com karmic Release                          
Hit http://hr.archive.ubuntu.com karmic-updates Release                   
Hit http://hr.archive.ubuntu.com karmic/main Packages                     
Hit http://archive.canonical.com karmic/partner Packages
Hit http://archive.canonical.com karmic/partner Sources               
Hit http://hr.archive.ubuntu.com karmic/restricted Packages
Hit http://hr.archive.ubuntu.com karmic/main Sources
Hit http://hr.archive.ubuntu.com karmic/restricted Sources
Hit http://hr.archive.ubuntu.com karmic/universe Packages
Hit http://hr.archive.ubuntu.com karmic/universe Sources
Get:3 http://security.ubuntu.com karmic-security/main Packages [37.5kB]
Hit http://hr.archive.ubuntu.com karmic/multiverse Packages
Hit http://hr.archive.ubuntu.com karmic/multiverse Sources
Hit http://hr.archive.ubuntu.com karmic-updates/main Packages
Hit http://hr.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://hr.archive.ubuntu.com karmic-updates/main Sources
Hit http://hr.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://hr.archive.ubuntu.com karmic-updates/universe Packages
Hit http://hr.archive.ubuntu.com karmic-updates/universe Sources
Hit http://hr.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://hr.archive.ubuntu.com karmic-updates/multiverse Sources
Get:4 http://security.ubuntu.com karmic-security/restricted Packages [14B]
Get:5 http://security.ubuntu.com karmic-security/main Sources [11.1kB]
Get:6 http://security.ubuntu.com karmic-security/restricted Sources [14B]
Get:7 http://security.ubuntu.com karmic-security/universe Packages [14.9kB]
Get:8 http://security.ubuntu.com karmic-security/universe Sources [2,533B]
Get:9 http://security.ubuntu.com karmic-security/multiverse Packages [1,666B]
Get:10 http://security.ubuntu.com karmic-security/multiverse Sources [575B]
Fetched 113kB in 1s (73.7kB/s)                    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
  firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,640kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com karmic-security/main xulrunner-1.9.1-gnome-support 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [40.6kB]
Get:2 http://security.ubuntu.com karmic-security/main xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [7,994kB]
Get:3 http://security.ubuntu.com karmic-security/main firefox-3.5-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [90.0kB]
Get:4 http://security.ubuntu.com karmic-security/main firefox-3.5-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 [206kB]
Get:5 http://security.ubuntu.com karmic-security/main firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 [943kB]
Get:6 http://security.ubuntu.com karmic-security/main firefox 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.4kB]
Get:7 http://security.ubuntu.com karmic-security/universe firefox-3.0 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Get:8 http://security.ubuntu.com karmic-security/universe firefox-3.0-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Get:9 http://security.ubuntu.com karmic-security/universe firefox-3.0-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Get:10 http://security.ubuntu.com karmic-security/main firefox-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.3kB]
Fetched 9,640kB in 19s (487kB/s)                                               
(Reading database ... 155652 files and directories currently installed.)
Preparing to replace xulrunner-1.9.1-gnome-support 1.9.1.5+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1-gnome-support_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement xulrunner-1.9.1-gnome-support ...
Preparing to replace xulrunner-1.9.1 1.9.1.5+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.1.5.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Preparing to replace firefox-3.5-gnome-support 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-gnome-support_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
Preparing to replace firefox-3.5-branding 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-branding_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-branding ...
Preparing to replace firefox-3.5 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5 ...
dpkg: warning: unable to delete old directory '/usr/lib/firefox-3.5.5': Directory not empty
Preparing to replace firefox 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-3.0 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0 ...
Preparing to replace firefox-3.0-branding 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0-branding_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0-branding ...
Preparing to replace firefox-3.0-gnome-support 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0-gnome-support_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0-gnome-support ...
Preparing to replace firefox-gnome-support 3.5.5+nobinonly-0ubuntu0.9.10.1 (using .../firefox-gnome-support_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-gnome-support ...
Processing triggers for desktop-file-utils ...
Setting up xulrunner-1.9.1 (1.9.1.6+nobinonly-0ubuntu0.9.10.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Setting up xulrunner-1.9.1-gnome-support (1.9.1.6+nobinonly-0ubuntu0.9.10.1) ...

Setting up firefox-3.5-branding (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.5 (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Please restart all running instances of firefox-3.5, or you will experience problems.

Setting up firefox-3.5-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1) ...

Setting up firefox (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0 (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0-branding (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ubuntu:/# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://hr.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic universe
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb http://blognux.free.fr/ubuntu hardy main # disabled on upgrade to jaunty
# deb-src http://blognux.free.fr/ubuntu hardy main # disabled on upgrade to jaunty
root@ubuntu:/# cat /boot/grub/menu.lst
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
# kopt=root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fec6f8e-c706-43bf-bbdc-3ed279788d7c

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
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, memtest86+
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
ubuntu@ubuntu:~$
```
That's all, from the begining to the end. :D

---

### Post by kansasnoob on 2009-12-19
Sorry if I sounded grouchy, I was getting tired. I can be a grouchy old man when I get tired.

Have you tried booting into kernel 2.6.27-15-generic rather than -16 as I suggested above?

Since the grub menu is hidden you'll have to press Esc just after the BIOS or system screen passes during bootup, then you should be able to select which kernel to boot.

Something is a bit odd there because the -16 kernel is listed twice:

```
title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
uuid		0fec6f8e-c706-43bf-bbdc-3ed279788d7c
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=0fec6f8e-c706-43bf-bbdc-3ed279788d7c ro  single
initrd		/boot/initrd.img-2.6.27-15-generic
```

If you can boot the -15 kernel I'd first install "startupmanager":

```
sudo apt-get install startupmanager
```

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

There you can change the default kernel to boot, and choose to Show bootloader menu to make things easier while we try to figure out why kernel -16 doesn't like your computer.

---

### Post by Laucien on 2009-12-19
When I try to boot with -15, I get:
```
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "intel" (module does not exist, 0)
(EE) No drivers available.
```
I click OK since there is no other choice xD
Then:
```
What would you like to do?
 1) Run Ubuntu in low-graphics mode for just one session
 2) Reconfigure graphics
 3) Troubleshoot the error
 4) Exit to console again
```
Option #1, I choose you!
Then apears a window that says 'Stand by one minute while the display restarts', with 'cancel' button grayed and 'unclickable' :D, and OK button. I press ok and then I only have a blinking _ in top left corner.

---

### Post by Greevous on 2009-12-19
I've had a similar problem since I updated my Toshiba Satellite, except that it goes from grub to a white ubuntu logo in the middle of my screen and hangs there.

Obviously it's not a graphics problem like I've seen in other 9.10 threads, since I get more than just plain text. 

I've tried all other options in the grub (including recovery options), but they all just stop somewhere in the process.

---

### Post by Greevous on 2009-12-20
Update >> I tried to fix the upgrade by mounting the filesystem on a live cd and running

```
chroot /mnt
apt-get update
```

but all I got was something like this:

```
W: Unable to read /etc/apt/apt.conf.d/ - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - FileExists (2: No such file or directory)
```

---

### Post by kansasnoob on 2009-12-21
Well, I hate to say it, but Karmic has been horribly unstable for me!

Every time I think I've figured something out everything breaks!

Sad to see things like this:

[http://www.itwire.com/content/view/28574/1141/](http://www.itwire.com/content/view/28574/1141/)

I still love Ubuntu and I'm sure we'll get past this but I can't rely on Karmic at all!

---

### Post by Greevous on 2009-12-21
Pity, because my macbook is running Karmic just fine. It's my older Satellite that had these inexplicable problems.

---

