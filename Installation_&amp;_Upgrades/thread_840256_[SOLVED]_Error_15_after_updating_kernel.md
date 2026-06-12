---
title: "[SOLVED] Error 15 after updating kernel"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by oBirdman on 2008-06-25
This morning I tried to update to 2.6.24-18 with the update manager. Everything seemed to be going ok and I was asked for a restart.

However, when I restarted the computer, I got the following message:

---
GRUB loading stage 1.5 ...
GRUB loading please wait..
Press 'ESC' to enter menu ...

Error 15: File not found
Press any key to continue
---

Pressing a key takes me to a menu where I can select three kernel versions ( -16, -17 and -18 ), each of one with a recovery mode.
None of them works and they all give the same error 15.

I have found quite some posts about how to solve this, but none of them worked in my case. I am working with one disc, so the (hd0,1) is not applicable.

Below I post the output of some commands in the hope that they are useful to anybody willing to help me:

sudo fdisk -l gives:
> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18703   150231816   83  Linux
/dev/sda2           18704       19457     6056505    5  Extended
/dev/sda5           18704       19457     6056473+  82  Linux swap / Solaris


sudo mount -t ext3 /dev/sda1 /mnt

ls -al /mnt/boot
> 
total 120
drwxr-xr-x  3 root root   4096 2008-06-25 09:23 .
drwxr-xr-x 24 root root   4096 2008-06-25 09:24 ..
drwxr-xr-x  2 root root   4096 2008-06-04 09:33 grub
-rw-r--r--  1 root root 103204 2007-09-28 10:06 memtest86+.bin


cat /mnt/boot/grub/menu.lst|grep -v \#

> 
default		0

timeout		3

hiddenmenu

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


Anybody out there willing to help me?

---

### Post by PmDematagoda on 2008-06-25
Could you please post the entire menu.lst file?

---

### Post by squee on 2008-06-25
I know very little about this kind of thing but I noticed that your kernel isnt the most uptodate version.  Im running  -19 so try to update

sudo apt-get update
sudo apt-get upgrade

you know the drill.

Also have you tried to run ubuntu from the install disk?

---

### Post by oBirdman on 2008-06-25
ok, here it goes:

> 
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
# kopt=root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by oBirdman on 2008-06-25
> **squee said:**
> I know very little about this kind of thing but I noticed that your kernel isnt the most uptodate version.  Im running  -19 so try to update

sudo apt-get update
sudo apt-get upgrade

you know the drill.

Also have you tried to run ubuntu from the install disk?

Before having this error I tried to update to -18. After getting error 15, I ran Ubuntu on the Live CD and noticed that the Update Manager was still suggesting to update to -18, which I tried again without any change. Update manager is now still suggesting to update to -18.

---

### Post by squee on 2008-06-25
Sorry, dont think i can help any more. Have you tried letting it install -18 again? There could have been an error the first time. I had a similar problem last week where it wouldnt boot and I just had to update and upgrade again.

---

### Post by frodon on 2008-06-25
The output of the following command would help too :
```
ls -l /dev/disk/by-uuid
```

My bet is for wrong uuid reference in menu.lst

---

### Post by oBirdman on 2008-06-25
> **frodon said:**
> The output of the following command would help too :
```
ls -l /dev/disk/by-uuid
```

This is the output I get:

> 
total 0
lrwxrwxrwx 1 root root 10 2008-06-25 12:10 13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-25 12:10 74ffca43-e2f7-44f6-a191-165c3667ccf7 -> ../../sda5


---

### Post by oBirdman on 2008-06-25
Another thing I noticed. The contents of my /boot/ folder are the following:

> 
abi-2.6.24-16-generic
memtest86+.bin
config-2.6.24-16-generic
System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
vmlinuz-2.6.24-16-generic


Note that the initrd file has a .bak extension and that there is no initrd file with the exact name as in the menu.lst

---

### Post by frodon on 2008-06-25
ok thanks now please the output of "cat /etc/fstab", "cat /boot" and "cat /boot/grub/device.map"

I hope that will all these information we will be able to understand what is the issue.

EDIT: seeing your previous post it seems that the kernel install went bad and that we located the issue. If you can't boot use a live CD to finish/reinstall the -18 kernel.

---

### Post by oBirdman on 2008-06-25
ok, good to hear that you located the issue. In any case I post the output you requested:

cat /etc/fstab

> 
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0


cat /boot
> 
cat: /boot: Is a directory


cat /boot/grub/device.map
> 
cat: /boot/grub/device.map: No such file or directory


The strange thing is that the following command does give an output:

cat /mnt/boot/grub/device.map

> 
(hd0)	/dev/sda


---

### Post by frodon on 2008-06-25
yep i did some typos giving you the commands sorry, your fstab is not the one i'm used too so ican't tell you if it's ok or not.

I think the thing to test is to use a live CD to chroot your ubuntu partition and reinstall the -18 kernel.

---

### Post by oBirdman on 2008-06-25
OK, so I tried to install the -18 kernel with the live CD. The Update Manager downloaded all the packages and tried to install them. But then after the system restart, there is no change. I still get the Error 15 and even stranger: the Update Manager tells me to install -18, ignoring the work it just did before the restart.

Should I update the kernel using the Update Manager, or should I do it in a different way?

---

### Post by frodon on 2008-06-25
Did You chroot your ubuntu partition with your liveCD, if not you just installed -18 kernel in your liveCD session.

Details here in case you wonder what i'm talking about :
[http://ubuntuforums.org/showthread.php?t=422523](http://ubuntuforums.org/showthread.php?t=422523)

---

### Post by oBirdman on 2008-06-25
Thanks for the link. I have followed the procedure two times and both times they did not have any effect.

The sudo apt-get update gives the following output:

> 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
...

...
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 1B in 1s (1B/s)
Reading package lists... Done


The list is pretty long, so I haven't copied it here. There are quite some ignores, but mostly translation-en_US files. The ignores that are not translations:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages; and
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg


sudo apt-get upgrade gives the following:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


sudo aptitude upgrade

> 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  initramfs-tools 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Cannot find /proc/version - is /proc mounted?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


sudo apt-get -f install

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


sudo apt-get upgrade:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


---

### Post by frodon on 2008-06-25
yep, now what you should do is to reinstall the kernel, it should be something like :
```
sudo apt-get reinstall linux-image-2.6.24-18-generic
```Sorry i don't have the exact command in mind and i'm not at home yet.

---

### Post by oBirdman on 2008-06-25
What I tried was the following command:

sudo apt-get install --reinstall linux-image-2.6.24-18-generic

It gave the following output with quite some errors:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
Recommended packages:
  lilo grub
The following NEW packages will be installed:
  linux-image-2.6.24-18-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/18.4MB of archives.
After this operation, 61.8MB of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package linux-image-2.6.24-18-generic.
(Reading database ... 155209 files and directories currently installed.)
Unpacking linux-image-2.6.24-18-generic (from .../linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb) ...
Done.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
Cannot find /proc/version - is /proc mounted?
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by frodon on 2008-06-25
Ok, please check one thing, once on the liveCD type "df -h" to check if your /boot is not full, this could be a cause of this issue.
If it is full, you must remove/move some of the old versions of the kernel then retry the reinstall of the linux-image-2.6.24-18-generic kernel.

Don't worry, i'm sure we will find a solution.

---

### Post by oBirdman on 2008-06-25
The output of 'dr -h':

> 
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1010M   16M  994M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1010M   16M  994M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1010M  108K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   60K 1010M   1% /dev
devshm               1010M   12K 1010M   1% /dev/shm
tmpfs                1010M   16K 1010M   1% /tmp
gvfs-fuse-daemon     1010M   37M  974M   4% /home/ubuntu/.gvfs
/dev/sda1             143G   49G   87G  37% /mnt/repair


Thanks a lot for the help so far. It's quite frustrating as I've been on this for about 7 hours now. But it sure is good to have some help!

---

### Post by oBirdman on 2008-06-25
ah, and if I do 'dr -h /boot', the output is the following:

> 
Filesystem            Size  Used Avail Use% Mounted on
-                    1010M   37M  974M   4% /


So I guess space is not the issue.

---

### Post by frodon on 2008-06-25
For me the problem is "Could not find postinst hook script [update-grub]", once this problem solve you should be able to reinstall correctly your kernel.

I'm short in time so i can't do more for today, put "Could not find postinst hook script [update-grub]" in google and you should find some interesting results.
You can use google too for better search results in the forum, just type the following in google :
> site:ubuntuforums.org Could not find postinst hook script [update-grub]

---

### Post by oBirdman on 2008-06-25
Hi Frodon. Thanks so far. I-ll dive into that issue.

---

### Post by oBirdman on 2008-06-25
Well, it did have some effect. At this moment the Error 15 is solved. On startup I get to see the Ubuntu screen loading, but then the system hangs on 'Starting NFS kernel daemon'.

But I guess that's another issue I have to dive into.

---

### Post by frodon on 2008-06-26
Great, so what we did solved the error 15 issue ?

Ok your "Starting NFS kernel daemon" hangs sounds like an initrams script issue for me so here something to try.
Boot your live CD and chroot your ubuntu partition or just boot in recovery mode if it works then type the following command :
```
sudo update-initramfs -u -k 2.6.24-18-generic
```Change the kernel name if needed, this command is supposeed to update the initramfs scripts of the concerned kernel.

But i think till we are not able to reinstall correctly the 2.6.24-18 kernel we will have issues, BTW 2.6.24-19 is already out maybe you can try to install it too.

---

### Post by oBirdman on 2008-06-26
Hi Frodon,
Thanks for checking back on this issue.

The problems persist. Most notably I have the following problems:
- it fails to start up basic networking on startup.
- fails to mount local filesystem
- takes very long to start the nfs kernel daemon


I updated the initramfs as you asked and didn't get any error.

Then I tried to update to -19 by typing in:

sudo apt-get install linux-image-generic

It returned quite some stuff (took out the first bit in which it fetched the package), with the following errors:

> 
(...)
Fetched 23.0MB in 54s (418kB/s)                                                
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package linux-image-2.6.24-19-generic.
(Reading database ... 157440 files and directories currently installed.)
Unpacking linux-image-2.6.24-19-generic (from .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-19-generic.
Unpacking linux-ubuntu-modules-2.6.24-19-generic (from .../linux-ubuntu-modules-2.6.24-19-generic_2.6.24-19.28_i386.deb) ...
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.24.19.21_i386.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done
Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.28) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Setting up linux-image-generic (2.6.24.19.21) ...
Cannot find /proc/version - is /proc mounted?


After restart a 'uname -r' gives kernel -19, so that's good I guess. The restart had the same errors as mentioned in the beginning of this post.

In the output of the kernel update I found the fstab error. Just in case it is of importance, I hereby include the ouput of cat /etc/fstab 

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=74ffca43-e2f7-44f6-a191-165c3667ccf7 none            swap    sw              0       0/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by frodon on 2008-06-26
So at this point of time you can boot but you have the 3 problems you listed and that you never had before ?

---

### Post by oBirdman on 2008-06-26
Yes, I can boot, but I already could yesterday night after updating the grub.

Before the Error 15, I didn't have any problem with my system. So all the problems are new.

Besides the three issues at startup I also have no sound and the network manager does not list a Wireless Network. (which I do have when booting with the Live CD) So it's basically impossible for me to upgrade anything in the normal boot, because I have no connection to the internet. For that I chroot with the Live CD.

---

### Post by frodon on 2008-06-26
Please boot and run a :
```
sudo depmod -a
```Then restart and see if it's better.Check also that you have your restricted-modules kernel-modules packages installed.

Then for the findfs error i'm curious, could you give the output of :
```
blkid /dev/sda1
vol_id /dev/sda1
```

For the findfs issue i found the 2 following links which could hopefully help :
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/110138/comments/22](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/110138/comments/22)
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/66032/comments/14](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/66032/comments/14)

---

### Post by oBirdman on 2008-06-26
The depmod did not result in any apparant change.

blkid /dev/sda1 does not give an ouput

vol_id /dev/sda1 gives:

> 
/dev/sda1: error opening volume


EDIT: only now I see the two links to the issues. I'll check them, thanks.

---

### Post by frodon on 2008-06-26
Damn, if "vol_id /dev/sda1" returns error i'm starting to think there's something wrong on your disk, maybe not hardware but maybe the MBR or partition table is wrong.

---

### Post by oBirdman on 2008-06-26
Somehow, that damn is not comforting...

---

### Post by oBirdman on 2008-06-26
I found the following thread:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Do you think it's worth trying some of the procedures they mention, or would it further mess up my system and is there something else that needs to be done first?

---

### Post by squee on 2008-06-26
Ok what about, instead of constantly mending something thats broken, throw it away and get a new one - metaphorically. Back up your important data and just start from scratch with the liveCD.

Just an idea, but after what Iv seen here, it might be easier.

---

### Post by frodon on 2008-06-26
Up to date tutorial on this is here :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show)

However i think your problem may not be related to GRUB, i don't really get why vol_id doesn't work on your partition, it is for sure one of the root cause of your kernel install issue as such install use tools to autodetect partition and UUIDs.

---

### Post by oBirdman on 2008-06-26
Squee, after so many hours of trying to fix it, I'd really like to solve it. But I guess you are right, why not a clean install...

---

### Post by frodon on 2008-06-26
> **squee said:**
> Ok what about, instead of constantly mending something thats broken, throw it away and get a new one - metaphorically. Back up your important data and just start from scratch with the liveCD.Because if the problem is in the partition table reinstalling will not solve the problem and the same issue may come back later again so in this case you lose your install and keep the issue.

vol_id not recognizing the partition is pointing out something serious that need to be understood IMO.

But sure fresh install is a good and quick solution in many cases for those who are fine with this.

---

### Post by squee on 2008-06-26
We all have to admit defeat at some stage. Iv had to do a clean install a couple of times. One memorable time was back in Warty when I chmod 777 -R somewhere I shouldnt have - I still wouldnt know how to undo that but luckily ubuntu has moved on to the point where thats not needed any more.

If you chose to continue to try and solve it, best of luck. The reward of satisfaction at the end is unmeasureable!

---

### Post by oBirdman on 2008-06-26
Frodon, I think you were right about GRUB. I ran SuperGrub and it did not result in anything. Will try to find out more info by searching on the vol_id error.

---

### Post by oBirdman on 2008-06-26
ok, forget my message of this morning of the vol_id returning the error. I did it again, but now using sudo and it did return something! (I know, stupid of me not to have used it before...)

output vol_id /dev/sda1:

> 
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9
ID_FS_UUID_ENC=13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


output of blkid /dev/sda1:

> 
/dev/sda1: UUID="13c1f0ed-e087-4fbc-af7b-f4e42d01c0b9" TYPE="ext3"


---

### Post by frodon on 2008-06-26
Even if i think it is not necesaary you can reinstall grub (just in case) using the link i gave you.

What worries me is the errors you get when you reinstall your kernel, i'm not able to evaluate accurately how much problems it can create.

---

### Post by oBirdman on 2008-06-26
OK, finally I had to give in. I did a fresh install... Everything works as it should now.

Thanks squee and especially frodon for the help!

---

### Post by frodon on 2008-06-26
I advice you to do ubuntu partition ghost images from time to time it makes life easier with such issues :)

I still feel frustrated that you did not solve your issue, you have been really unlucky on this, i almost never seen such big mess after kernel updates. hope your ubuntu experience will only be great from now, nobody deserves such upgrade mess.

---

