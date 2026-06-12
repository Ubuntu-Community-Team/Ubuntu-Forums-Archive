---
title: "Upgrade from 12.04 to 14.04 package issues/old kernels"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by Weidbrewer on 2014-08-17
I've been googling and reading forum posts since Friday on this issue, and all I can determine is that this isn't a totally uncommon problem.  Unfortunately, the solutions I've been trying from threads like [this one]("http://ubuntuforums.org/showthread.php?t=2238992") aren't working.  Everything ends with the following error:

```
Errors were encountered while processing:
 linux-image-3.2.0-57-generic
 linux-image-3.2.0-58-generic
 linux-image-3.2.0-59-generic
 linux-image-3.2.0-60-generic
 linux-image-3.2.0-61-generic
 linux-image-3.2.0-63-generic
 linux-image-3.2.0-64-generic
 linux-image-3.2.0-65-generic

```

Nothing I do seems to be able to get rid of these entries, and I can't install anything new with them in place.  Dpkg and purge can't seem to touch them, and synaptic won't remove them.

---

### Post by kansasnoob on 2014-08-17
> **Weidbrewer said:**
> I've been googling and reading forum posts since Friday on this issue, and all I can determine is that this isn't a totally uncommon problem.  Unfortunately, the solutions I've been trying from threads like [this one]("http://ubuntuforums.org/showthread.php?t=2238992") aren't working.  Everything ends with the following error:

```
Errors were encountered while processing:
 linux-image-3.2.0-57-generic
 linux-image-3.2.0-58-generic
 linux-image-3.2.0-59-generic
 linux-image-3.2.0-60-generic
 linux-image-3.2.0-61-generic
 linux-image-3.2.0-63-generic
 linux-image-3.2.0-64-generic
 linux-image-3.2.0-65-generic

```

Nothing I do seems to be able to get rid of these entries, and I can't install anything new with them in place.  Dpkg and purge can't seem to touch them, and synaptic won't remove them.

That's a bad thread to be following because we seem to be stuck :(

---

### Post by Weidbrewer on 2014-08-17
Well, that would do it.  I didn't read through the whole thing, since I couldn't even have success when anything that *was* working in the first four pages.

---

### Post by kansasnoob on 2014-08-18
It might be useful to see the bash history:

```
history
```

If it's an incredibly long history it may spill over the terminals limit in which case we'd want to send the output to a text file in Home like:

```
history > history.txt
```

Also tell us what happened first, what you were trying to accomplish, etc.

---

### Post by Bashing-om on 2014-08-18
Weidbrewer; Hey;

I too will join you here. This should not be too tough as HWE is not a factor.
Show us what we are working with:
Post back the output of terminal commands:
```

df -h
df -i
dpkg -l | grep linux

```
And we see what the package manager advises when we try and do some clean up operations. The 'df' commands are to see if we have operational head room to know what tools to employ here.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-18
> **kansasnoob said:**
> 
Also tell us what happened first, what you were trying to accomplish, etc.

Just trying to upgrade from 12.04 to 14.04.  

> **Bashing-om said:**
> Weidbrewer; Hey;

I too will join you here. This should not be too tough as HWE is not a factor.
Show us what we are working with:
Post back the output of terminal commands:
```

df -h
df -i
dpkg -l | grep linux

```
And we see what the package manager advises when we try and do some clean up operations. The 'df' commands are to see if we have operational head room to know what tools to employ here.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]




```
******@*****:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/sda5                45G   35G  7.5G  83% /
none                    4.0K     0  4.0K   0% /sys/fs/cgroup
udev                    2.0G   12K  2.0G   1% /dev
tmpfs                   392M  1.8M  390M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    2.0G   40M  1.9G   3% /run/shm
none                    100M  120K  100M   1% /run/user
/dev/sda3               405G  306G  100G  76% /media/OS
******@*****:~$ df -i
Filesystem                 Inodes  IUsed      IFree IUse% Mounted on
/dev/sda5                 2932736 394299    2538437   14% /
none                       501211      2     501209    1% /sys/fs/cgroup
udev                       498494    545     497949    1% /dev
tmpfs                      501211    597     500614    1% /run
none                       501211      4     501207    1% /run/lock
none                       501211     69     501142    1% /run/shm
none                       501211     47     501164    1% /run/user
/dev/sda3               104699052 394655  104304397    1% /media/OS
******@*****:~$ dpkg -l | grep linux
ii  extlinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders (ext2/3/4 and btrfs bootloader)
ii  libselinux1:amd64                                           2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                               1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                         1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.34.40                                        amd64        Generic Linux kernel headers
ii  linux-image-2.6.32-28-generic                               2.6.32-28.55                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
iF  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-57-generic                                3.2.0-57.87                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-58-generic                                3.2.0-58.88                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-59-generic                                3.2.0-59.90                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-60-generic                                3.2.0-60.91                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-61-generic                                3.2.0-61.93                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-63-generic                                3.2.0-63.95                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-64-generic                                3.2.0-64.97                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-65-generic                                3.2.0-65.99                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic                                3.2.0-67.101                                        amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                         3.13.0.34.40                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-34.60                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                                  1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
iU  syslinux-themes-debian                                      12-3                                                all          collection of boot loaders (theme metapackage)
rc  syslinux-themes-debian-squeeze                              12-3                                                all          collection of boot loaders (debian-squeeze theme)
iU  syslinux-themes-debian-wheezy                               12-3                                                all          collection of boot loaders (debian-wheezy theme)
ii  util-linux                                                  2.20.1-5.1ubuntu20.1                                amd64        Miscellaneous system utilities

```


Thus far, I've tried a number of things to remove the old kernels.  Synaptic, purge, and some other code.  Everything has stalled out with:

```
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:

 linux-image-3.2.0-57-generic
 linux-image-3.2.0-58-generic
 linux-image-3.2.0-59-generic
 linux-image-3.2.0-60-generic
 linux-image-3.2.0-61-generic
 linux-image-3.2.0-63-generic
 linux-image-3.2.0-64-generic
 linux-image-3.2.0-65-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2014-08-18
Weidbrewer: huumm;

We got head room, and the 'trusty' kernels are installed.
> 
Just trying to upgrade from 12.04 to 14.04. 


So did you make the upgrade ?:
show us:
```

lsb_release -a
uname -a
cat /etc/apt/sources.list

```

As we clear the deck;

[INDENT][INDENT][INDENT][INDENT]get ready for action
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-18
Here you go:

```
******@*****:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
******@*****:~$ uname -a
Linux ****** 3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
******@*****:~$ cat /etc/apt/sources.list
# deb cdrom:[Mythbuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)]/ lucid main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
# deb http://packages.medibuntu.org/ maverick free non-free # disabled on upgrade to maverick
deb http://extras.ubuntu.com/ubuntu trusty main #Third party developers repository

```

So, yeah...it *mostly* upgraded...but not completely.  (Just FYI, I'll be turning in for the night in the not too distant future, so my responses may be delayed until tomorrow evening.)

---

### Post by Bashing-om on 2014-08-18
Weidbrewer; Well,

So far, looks pretty good .. you are up on trusty, so why:
> 
Linux ****** 3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

are you booting the 'precise' kernel ?

show:
```

ls -al /
ls -al /boot

```
To see what you are linking to for the kernel to boot.
We want you up on the latest 'trusty' kernels before removing the older 'precise' kernels.

[INDENT][INDENT]now I just do not know
[INDENT][INDENT][INDENT]but there is hope we will find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-18
Hmm...is that the right syntax?

```
$ ls - al /
ls: cannot access -: No such file or directory
ls: cannot access al: No such file or directory
/:
bin    dev   initrd.img      lib64       mnt   root  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lost+found  opt   run   sys  var
cdrom  home  lib             media       proc  sbin  tmp  vmlinuz
```

---

### Post by Bashing-om on 2014-08-18
Weidbrewer, nope !

Second time I have done that ---  tired and time to quit for this session !
- silly little space !
correct to be:
```

ls -al /
ls -al /boot

```

[INDENT][INDENT]I will return
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-18
> **Bashing-om said:**
> tired and time to quit for this session !



Agreed

```
$ ls -al /
total 120
drwxr-xr-x  23 root root  4096 Aug 15 00:13 .
drwxr-xr-x  23 root root  4096 Aug 15 00:13 ..
drwxr-xr-x   2 root root  4096 Aug 14 23:54 bin
drwxr-xr-x   4 root root  4096 Aug 18 20:12 boot
drwxr-xr-x   2 root root  4096 Nov 30  2010 cdrom
drwxr-xr-x  16 root root  4440 Aug 18 20:27 dev
drwxr-xr-x 175 root root 12288 Aug 18 20:27 etc
drwxr-xr-x   4 root root  4096 Nov 30  2010 home
lrwxrwxrwx   1 root root    33 Aug 15 00:13 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root root    33 Aug  3 20:54 initrd.img.old -> /boot/initrd.img-3.2.0-67-generic
drwxr-xr-x  26 root root 12288 Aug 15 18:23 lib
drwxr-xr-x   2 root root  4096 Aug 14 22:15 lib64
drwx------   2 root root 16384 Nov 30  2010 lost+found
drwxr-xr-x  16 root root  4096 Aug 15 20:19 media
drwxr-xr-x   3 root root  4096 Mar 11 21:30 mnt
drwxr-xr-x   4 root root  4096 Feb 19 23:21 opt
dr-xr-xr-x 253 root root     0 Aug 15 19:19 proc
drwx------  16 root root  4096 Oct 14  2013 root
drwxr-xr-x  26 root root  1000 Aug 16 07:44 run
drwxr-xr-x   2 root root 12288 Aug 15 18:22 sbin
drwxr-xr-x   2 root root  4096 Apr 27  2010 srv
drwxr-xr-x  13 root root     0 Aug 15 19:19 sys
drwxrwxrwt  24 root root 12288 Aug 18 23:30 tmp
drwxr-xr-x  10 root root  4096 Jul 24  2012 usr
drwxr-xr-x  15 root root  4096 Aug 15 07:21 var
lrwxrwxrwx   1 root root    30 Aug 15 00:13 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root root    29 Aug  3 20:54 vmlinuz.old -> boot/vmlinuz-3.2.0-67-generic
******@*****:~$ ls -al /boot
total 80804
drwxr-xr-x  4 root root     4096 Aug 18 20:12 .
drwxr-xr-x 23 root root     4096 Aug 15 00:13 ..
-rw-r--r--  1 root root   646144 Jan 10  2011 abi-2.6.32-28-generic
-rw-r--r--  1 root root  1162712 Aug 13 12:45 abi-3.13.0-34-generic
-rw-r--r--  1 root root   795963 Jul 15 14:11 abi-3.2.0-67-generic
-rw-r--r--  1 root root   110590 Jan 10  2011 config-2.6.32-28-generic
-rw-r--r--  1 root root   165611 Aug 13 12:45 config-3.13.0-34-generic
-rw-r--r--  1 root root   140641 Jul 15 14:11 config-3.2.0-67-generic
drwxr-xr-x  3 root root     4096 Aug 18 20:27 extlinux
drwxr-xr-x  5 root root    12288 Aug 18 20:27 grub
-rw-r--r--  1 root root  9855879 Aug 17  2011 initrd.img-2.6.32-28-generic
-rw-r--r--  1 root root 27511622 Aug 18 20:12 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18483924 Aug 14 22:28 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2157108 Jan 10  2011 System.map-2.6.32-28-generic
-rw-------  1 root root  3381262 Aug 13 12:45 System.map-3.13.0-34-generic
-rw-------  1 root root  2896997 Jul 15 14:11 System.map-3.2.0-67-generic
-rw-r--r--  1 root root     1336 Jan 10  2011 vmcoreinfo-2.6.32-28-generic
-rw-r--r--  1 root root  4052512 Jan 10  2011 vmlinuz-2.6.32-28-generic
-rw-------  1 root root  5797728 Aug 13 12:45 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  4986960 Jul 15 14:11 vmlinuz-3.2.0-67-generic
```

---

### Post by Bashing-om on 2014-08-19
Weidbrewer; Well !

The links:
> 
lrwxrwxrwx   1 root root    33 Aug 15 00:13 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root root    33 Aug  3 20:54 initrd.img.old -> /boot/initrd.img-3.2.0-67-generic

lrwxrwxrwx   1 root root    30 Aug 15 00:13 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root root    29 Aug  3 20:54 vmlinuz.old -> boot/vmlinuz-3.2.0-67-generic

are there !
And I would expect that the booting kernel be "3.13.0-34-generic" // did you choose in grub to boot the old 'precise' kernel ?

What gives here ?

We will pick this back up in our AM.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-19
I didn't get a chance to check before I left for work this morning, and I will unfortunately be getting home rather late - but I will check once I'm there.  I certainly didn't *choose* to load that kernel, but now that I'm thinking about it, grub was also throwing an error during the upgrade.  It is possible it is loading the wrong one, but I don't think it is.

---

### Post by kansasnoob on 2014-08-19
> **Weidbrewer said:**
> I didn't get a chance to check before I left for work this morning, and I will unfortunately be getting home rather late - but I will check once I'm there.  I certainly didn't *choose* to load that kernel, but now that I'm thinking about it, grub was also throwing an error during the upgrade.  It is possible it is loading the wrong one, but I don't think it is.

When you boot that the next time run:

```
sudo update-grub
```

and post the output here.

---

### Post by Bashing-om on 2014-08-19
Weidbrewer; Morning !

See kansasnoob's last, at some point we surely want to inspect what grub is doing.
Also, we need to know the state of the system, and what the package manager thinks:
post back:
```

sudo apt-get update
sudo apt-get upgrade
apt-get -f install
sudo dpkg -C

```

Then perhaps we are ready to address the kernel removal issues.

[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-19
Jeez, that was a long day.

Kernel that is booting 3.2.0-67, but it has an asterix next to it.

> **kansasnoob said:**
> When you boot that the next time run:

```
sudo update-grub
```

and post the output here.


```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Generating grub configuration file ...
Found Windows 7 (loader) on /dev/sda2
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.

```


> **Bashing-om said:**
> 
```

sudo apt-get update
sudo apt-get upgrade
apt-get -f install
sudo dpkg -C

```

Everything up through the last command is what we've already had with the errors stated earlier with the kernels.  Then:

```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 syslinux-themes-debian-wheezy collection of boot loaders (debian-wheezy theme)
 syslinux-themes-debian collection of boot loaders (theme metapackage)
 linux-image-generic  Generic Linux kernel image
 linux-image-extra-3.13.0-34-generic Linux kernel extra modules for version 3.1
 ubuntu-desktop       The Ubuntu desktop system

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 memtest86+           thorough real-mode memory tester
 grub-pc              GRand Unified Bootloader, version 2 (PC/BIOS version)
 linux-image-3.13.0-34-generic Linux kernel image for version 3.13.0 on 64 bit 

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-3.2.0-61-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-59-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-65-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-63-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-60-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-58-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-57-generic Linux kernel image for version 3.2.0 on 64 bit x8
 linux-image-3.2.0-64-generic Linux kernel image for version 3.2.0 on 64 bit x8

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 medibuntu-keyring    GnuPG key of the Medibuntu repository
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)

```


<deep breath>  So, yeah...that's what we've got.

---

### Post by kansasnoob on 2014-08-20
OK let's try:

```
sudo dpkg --configure -a
```

If that totally pukes probably best to stop here, if not continue with:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

That may very well tell you to run additional commands which should be safe to do.

```
sudo update-grub
```

We may need to clear the cache first but I'd try that first, then if it laughs at us try:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

Then repeat all of the above.

---

### Post by Weidbrewer on 2014-08-20
> **kansasnoob said:**
> 

If that totally pukes probably best to stop here, if not continue with:


What are we considering totally puking?  Result:

```
Errors were encountered while processing:
 memtest86+
 grub-pc
 ubuntu-desktop
 linux-image-3.13.0-34-generic
 syslinux-themes-debian-wheezy
 syslinux-themes-debian
 linux-image-generic
 linux-image-extra-3.13.0-34-generic

```

---

### Post by Bashing-om on 2014-08-20
Weidbrewer; kansasnoob; Umphh

Don't know 'bout these apples to oranges !
> 
syslinux-themes-debian-wheezy collection of boot loaders (debian-wheezy theme)


Best be looking at the software sources ... and getting (??) grub properly installed ?
Then I expect we can tackle the kernels, Maybe ... !!
> 
The following packages have been unpacked but not yet configured.
<snip>
linux-image-generic  Generic Linux kernel image
linux-image-extra-3.13.0-34-generic Linux kernel extra modules for version 3.1
<snip>

Hoo Boy, this may be fun !

> 
The following packages are only half configured, probably due to problems

the list includes every kernel !

> 
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 medibuntu-keyring    GnuPG key of the Medibuntu repository
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)

This one is a piece of cake compared to th other situations.


Hoo BOY, this one is going to be fun. Are yall in for a ride ?

[INDENT][INDENT]we won't know
[INDENT][INDENT][INDENT][INDENT]'til we try
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-20
> **Bashing-om said:**
> 
Hoo BOY, this one is going to be fun. Are yall in for a ride ?



Let's do this thing.

---

### Post by Bashing-om on 2014-08-20
Weidbrewer; HooKayy,

Let's start this thing.
Small steps !

Grub ! We have to boot !
```

ls -al /etc/grub.d
ls -la /boot/grub
cat /etc/default/grub

```
At this point we need to know that you have on hand the liveDVD ( re-install grub from ).

Our sources for software and updates: they have to be correct:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
we get as close to default as possible.

Then we can look at the kernels.

[INDENT][INDENT][INDENT]hey,
[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-20
> **Bashing-om said:**
> 
```

ls -al /etc/grub.d
ls -la /boot/grub
cat /etc/default/grub

```



```
ls -al /etc/grub.d
total 148
drwxr-xr-x   4 root root  4096 Aug 15 18:14 .
drwxr-xr-x 175 root root 12288 Aug 20 22:13 ..
-rwxr-xr-x   1 root root  9424 May 15 15:02 00_header.dpkg-dist
-rwxr-xr-x   1 root root   188 Mar 20  2013 00_os-prober_proxy
-rwxr-xr-x   1 root root  6058 May  8 08:08 05_debian_theme.dpkg-dist
-rwxr-xr-x   1 root root 11608 May 15 15:02 10_linux.dpkg-dist
-rwxr-xr-x   1 root root  6743 Sep 12  2012 11_header
-rwxr-xr-x   1 root root  5522 Apr 21  2011 12_debian_theme
-rwxr-xr-x   1 root root  7407 May 17  2012 13_linux
-rwxr-xr-x   1 root root  6335 May 17  2012 14_linux_xen
-rwxr-xr-x   1 root root  1588 Sep 24  2010 15_memtest86+
-rwxr-xr-x   1 root root   188 Mar 20  2013 16_os-prober_proxy
-rwxr-xr-x   1 root root   214 Apr 13  2010 17_custom
-rwxr-xr-x   1 root root    95 Apr 27  2011 18_custom
-rwxr-xr-x   1 root root 10412 May 15 15:02 20_linux_xen.dpkg-dist
-rwxr-xr-x   1 root root  1992 Mar 12 08:31 20_memtest86+.dpkg-dist
-rwxr-xr-x   1 root root 11692 May 15 15:02 30_os-prober.dpkg-dist
-rwxr-xr-x   1 root root  1416 May 15 15:02 30_uefi-firmware
-rwxr-xr-x   1 root root   216 May 15 15:02 41_custom.dpkg-dist
drwxr-xr-x   2 root root  4096 Mar 20  2013 bin
drwxr-xr-x   2 root root  4096 Mar 20  2013 proxifiedScripts
-rw-r--r--   1 root root   483 Apr 13  2010 README
*****@*****:~$ ls -la /boot/grub
total 2416
drwxr-xr-x 5 root root   12288 Aug 20 21:03 .
drwxr-xr-x 4 root root    4096 Aug 20 21:03 ..
drwxr-xr-x 2 root root    4096 Aug 15 18:15 fonts
-rw-r--r-- 1 root root     699 Jul 23  2012 gfxblacklist.txt
-r--r--r-- 1 root root   13616 Aug 20 21:02 grub.cfg
-rw------- 1 root root    1227 Aug 20 21:03 grub.cfg.new
-rw-r--r-- 1 root root    1024 Aug 19 22:18 grubenv
drwxr-xr-x 2 root root   12288 Aug 20 21:02 i386-pc
drwxr-xr-x 2 root root    4096 Nov 30  2010 locale
-rw-r--r-- 1 root root 2405285 Aug 20 21:02 unicode.pf2
*****@*****:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="8"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash vga=795"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

> 

```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```


```
****@*****:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Mythbuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)]/ lucid main multiverse restricted universe
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29	deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30	
    31	## Uncomment the following two lines to add software from the 'backports'
    32	## repository.
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    39	# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb http://archive.canonical.com/ubuntu lucid partner
    46	# deb-src http://archive.canonical.com/ubuntu lucid partner
    47	
    48	deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    49	deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    50	deb http://security.ubuntu.com/ubuntu trusty-security universe
    51	deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    52	deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    53	deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    54	# deb http://packages.medibuntu.org/ maverick free non-free # disabled on upgrade to maverick
    55	deb http://extras.ubuntu.com/ubuntu trusty main #Third party developers repository
****@*****:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/atareao-atareao-oneiric.list <==

==> /etc/apt/sources.list.d/atareao-atareao-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu precise main # disabled on upgrade to precise

==> /etc/apt/sources.list.d/atareao-atareao-oneiric.list.save <==

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list <==

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main
deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list.save <==

==> /etc/apt/sources.list.d/fkrull-deadsnakes-precise.list <==

==> /etc/apt/sources.list.d/fkrull-deadsnakes-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu precise main
deb-src http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu precise main

==> /etc/apt/sources.list.d/fkrull-deadsnakes-precise.list.save <==

==> /etc/apt/sources.list.d/langdalepl-gvfs-mtp-precise.list <==
# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/langdalepl-gvfs-mtp-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu precise main
deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu precise main

==> /etc/apt/sources.list.d/langdalepl-gvfs-mtp-precise.list.save <==
# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/medibuntu.list <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ maverick free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx" disabled on upgrade to maverick
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

==> /etc/apt/sources.list.d/medibuntu.list.distUpgrade <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ maverick free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx" disabled on upgrade to maverick
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

==> /etc/apt/sources.list.d/medibuntu.list.save <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ maverick free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx" disabled on upgrade to maverick
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

==> /etc/apt/sources.list.d/mythbuntu-repos.list.distUpgrade <==
# deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu maverick main # disabled on upgrade to maverick
# deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu maverick main # disabled on upgrade to maverick
# deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu maverick main # disabled on upgrade to maverick

==> /etc/apt/sources.list.d/mythbuntu-repos.list.save <==
# deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu maverick main # disabled on upgrade to maverick
# deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu maverick main # disabled on upgrade to maverick
# deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu maverick main # disabled on upgrade to maverick

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list <==

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save <==

==> /etc/apt/sources.list.d/rgibert-ebook-precise.list <==

==> /etc/apt/sources.list.d/rgibert-ebook-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/rgibert/ebook/ubuntu precise main
deb-src http://ppa.launchpad.net/rgibert/ebook/ubuntu precise main

==> /etc/apt/sources.list.d/rgibert-ebook-precise.list.save <==

==> /etc/apt/sources.list.d/steam.list <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/steam.list.distUpgrade <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list <==

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.save <==

==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list <==

==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save <==


```


As for GRUB...crap...I gotta find one of the CDs...
I'm actually in the process of moving, so all my CDs - blank or otherwise - are in a storage unit.  Have to grab one at work tomorrow or something.

---

### Post by kansasnoob on 2014-08-21
IMHO the best thing to do would be to create an external backup of anything and everything important, then just perform a fresh install of 14.04.1 and start over ;)

---

### Post by Bashing-om on 2014-08-21
Weidbrewer; Welp;

Looks like you know your way around grub !
I would like to (re-)install grub to all defaults.
To that end I suggest that you backup your files from "/etc/grub.d" as it is foreseeable that you 'might' reuse them at some point.

Next is the sources, several sources exist from 'precise'. At this time disable ALL 3rd party sources ( /etc/apt/sources.list.d/ ) -will leave x-swat active 'til reversion to open source is complete - and you can bet, when we come out of this ordeal, some of them (precise) will not have made it up to 'trusty'. These will be reverted back to what is in the repository OR removed from the system. At some point in our adventure.

And I still hold that we (RE-)install grub. I suggest a complete purge, and start all over. That will require a liveDVD(USB), just in case.
Presently Are you able to boot the install ? -  the 3.2.0-67-generic kernel - should be good 'nuff to work over grub with.  Once the sources are all cleaned up and you can boot the install, we can  purge/reinstall grub from the install, but if things go south we will require a liveDVD(USB) to recover.
To that end, let's look at what partition(s) are booting,
```

sudo fdisk -lu
sudo parted -l
sudo blkid
cat /etc/fstab

```
should cover all the bases and give a good overview of the system we are working on. We do need to know where to tell grub to install the boot code.

Graphics driver ! Proprietary ? do you got to have it, or can we revert to opensource ?
> 
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main

We really need to be as close to default as possible .. a proprietary driver at this stage ( and maybe a big cause of this situation ) can really hose up the works ! -- there is that 'precise' again, I would have thought that the cutting edge graphics folks would have been ready for 'trusty'. So what gives here ? Might be worth our time to investigate the PPA at our earliest restore point.

;
sources: 3rd party turned off (leave x-swat till reverted !) then turn off x-swat
graphics driver reverted to open source
liveDVD(USB) on hand ! ->
Grub (RE-)installed
Then we look at cleaning up the system and checking/repairing the configurations - that includes the kernels.

a lot of work
[INDENT][INDENT][INDENT]but somebody has got to do it
[/INDENT][/INDENT][/INDENT]

By the way, I am at GMT-6 and my get up and go, got up and went about 2 hours ago. I am generally fried by about 02:00 GMT or so.

---

### Post by Weidbrewer on 2014-08-21
> **kansasnoob said:**
> IMHO the best thing to do would be to create an external backup of anything and everything important, then just perform a fresh install of 14.04.1 and start over ;)

I agree that that is certainly the *easy* way of doing things - and I've backed up my home folder in preperation for that - but right now, while I have willing help, I want to see if we can fix this and (maybe) figure out what went wrong.  (after all, LTS to LTS is *supposed* to be seemless) There's a reason I always upgrade the laptop first:  it's no biggie to wipe it.  However, if I run into this issue with my wife's computer?  Worse yet, my server?  Bad scene.

Soooooo much to cover with Bash - 

> **Bashing-om said:**
> 
I would like to (re-)install grub to all defaults.
To that end I suggest that you backup your files from "/etc/grub.d" as it is foreseeable that you 'might' reuse them at some point.


What's the best way to go about that, especially the backup part?  I can reinstall grub with the live CD, no biggie, but I'm not sure about the backup.  Also, just to be clear, I've been booting up fine - it's just the update that's throwing that grub error.  

> 

Next is the sources, several sources exist from 'precise'. At this time disable ALL 3rd party sources ( /etc/apt/sources.list.d/ ) -will leave x-swat active 'til reversion to open source is complete 

Done

> 
```

sudo fdisk -lu
sudo parted -l
sudo blkid
cat /etc/fstab

```


```

****@*****:~$ sudo parted -l
Model: ATA WDC WD5000BEVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  15.8GB  15.7GB  primary   ntfs            boot
 3      15.8GB  450GB   434GB   primary   ntfs
 4      450GB   500GB   50.1GB  extended
 5      450GB   498GB   48.0GB  logical   ext4
 6      498GB   500GB   2096MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: TSSTcorp DVD+-RW TS-L633C (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3979MB  3989MB  9568kB               EFI


****@*****:~$ sudo blkid

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="3886265E86261CBE" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="E8CA28EDCA28B9A8" TYPE="ntfs" 
/dev/sda5: UUID="5e8ac879-97e7-4e97-bd89-bf101656a290" TYPE="ext4" 
/dev/sda6: UUID="d6ba35f8-92ae-4a0c-b09e-4d81cea884d1" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
****@*****:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d6ba35f8-92ae-4a0c-b09e-4d81cea884d1 none            swap    sw              0       0
```


> 

Graphics driver ! Proprietary ? do you got to have it, or can we revert to opensource ?


hmm...I don't remember changing that driver.  No issues with reverting.  Can you give me some advice on doing so?

```
lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)

```

---

### Post by Bashing-om on 2014-08-21
Weidbrewer; Hey hey;

One reason to (re-)install grub:
> 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Generating grub configuration file ...
Found Windows 7 (loader) on /dev/sda2
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.


I do not comprehend what could possibly cause this output from a "grub-update" command.
As well, for the other reason, you are booting the precise kernel when symlinks to /boot show you should be booting the trusty kernel.
Now in your /etc/grub.d are several non-standard (non ubuntu ?) control files that I have not the intention of trying to understand. If you have put effort into them and are worth saving, copy them off ( simple copy command to where ever) .. else I am happy to start by delete-ing them and getting back to a default '/etc/grub' directory. So that there is no interference/conflict upon (re-)install.

Next is the graphics driver: for reference when we come out of this, let's see now what you are running:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
And what it might take to revert back to open source, as again we want to reduce any conflict when we go to removing/installing kernels and resolving system configuration issues at a later time.


partitions/UUID/fstab all agree and looks good, no worry there. ubuntu installed to 'sda5' and boot code to be installed to the MBR of 'sda'.
chainload Windows -
we can so that, no sweat.
---------------------------------------
I am done for this session, thinking getting forced and brain is foggy. In my AM I will give you the list to remove from '/etc/grub.d'
Post back to us the graphics info
and tomorrow - when you are in and ready - we go to work
Objective: revert graphics driver, (re-)install grub, overall assessment of the package manager.


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-22
> **Bashing-om said:**
> Weidbrewer; Hey hey;

One reason to (re-)install grub:


I do not comprehend what could possibly cause this output from a "grub-update" command.
As well, for the other reason, you are booting the precise kernel when symlinks to /boot show you should be booting the trusty kernel.
Now in your /etc/grub.d are several non-standard (non ubuntu ?) control files that I have not the intention of trying to understand. If you have put effort into them and are worth saving, copy them off ( simple copy command to where ever) .. else I am happy to start by delete-ing them and getting back to a default '/etc/grub' directory. So that there is no interference/conflict upon (re-)install.

Next is the graphics driver: for reference when we come out of this, let's see now what you are running:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
And what it might take to revert back to open source, as again we want to reduce any conflict when we go to removing/installing kernels and resolving system configuration issues at a later time.


partitions/UUID/fstab all agree and looks good, no worry there. ubuntu installed to 'sda5' and boot code to be installed to the MBR of 'sda'.
chainload Windows -
we can so that, no sweat.
---------------------------------------
I am done for this session, thinking getting forced and brain is foggy. In my AM I will give you the list to remove from '/etc/grub.d'
Post back to us the graphics info
and tomorrow - when you are in and ready - we go to work
Objective: revert graphics driver, (re-)install grub, overall assessment of the package manager.


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

Did you notice that one of the many PPA's in use was for some version of Grub Customizer:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

> ==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list <==

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main

So I suppose one needs to check the version of each and every package remotely related to grub-pc, including all dependencies. Maybe spend an hour or so digging through the old apt logs from Precise.

---

### Post by Bashing-om on 2014-08-22
@kasasnoob -> Weidbrewer; Agreed for checking.

I have a fresh mind this morning, and in the night's rest I have come to the conclusion to re-examine this situation. See perhaps if it is not as dire as I dread it to be. Presently I still consider our best interest is served by a complete purge of grub, and just start all over. Looking next to see if I still feel that way ( me with a fresh mind on this) .
Looking at the easiest most "secure" way to get to the kernels and cleaning the system up.
We for sure want to be working from the 'trusty' kernel.

[INDENT][INDENT]I be alook'n
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
> **Bashing-om said:**
> Weidbrewer; Hey hey;

One reason to (re-)install grub:


Sorry - I wasn't questioning you on the *need,* just the execution.  Also, I misunderstood what you meant about backing up "the files" for grub  Yeah, I backed up that section last night.  When I attempted a reinstall from a live CD, I got this:

```
root@ubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
/proc/devices: fopen failed: No such file or directory
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
device node not found
/proc/devices: fopen failed: No such file or directory
device node not found
/proc/devices: fopen failed: No such file or directory
device node not found
/proc/devices: fopen failed: No such file or directory
device node not found
Installation finished. No error reported.
```

> **kansasnoob said:**
> Did you notice that one of the many PPA's in use was for some version of Grub Customizer:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)



So I suppose one needs to check the version of each and every package remotely related to grub-pc, including all dependencies. Maybe spend an hour or so digging through the old apt logs from Precise.

Hmm....that is very strange.  I don't remember anything of installing that...   Do we think that might be the root of all of these upgrade issues?


I will check on the GFX driver again when I get home.   Good news to you helpful folk:  I'll be out of town tomorrow and Sunday, so you'll get a reprieve from me.  :)

---

### Post by Bashing-om on 2014-08-22
Weidbrewer && kansasnoob;;

Looked the situation over: And there is NO DOUBT in my mind to purge grub !
Here be what is:
The following packages have been unpacked but not yet configured.
 linux-image-generic  Generic Linux kernel image
 linux-image-extra-3.13.0-34-generic Linux kernel extra modules for version 3.1
 ubuntu-desktop       The Ubuntu desktop system
Good news is the latest 3.2 kernel is not included in the problem list from ->The following packages are only half installed, due to problems during installation. => all kernels less the -67 (booting)

Grub: convinces me to purge: ->
> 
-r--r--r-- 1 root root   13616 Aug 20 21:02 grub.cfg
-rw------- 1 root root    1227 Aug 20 21:03 grub.cfg.new

grub.cfg.new should have been overwritten to grub.cfg and no longer in existence, The system puked on it ! See the difference in the file sizes !
Looking at /etc/grub.d and Yeah, this is the biggy for the release upgrade difficulties ! And then lesser is the 3rd party software the system could not cope with ( It ain't ubuntu !) .
The files in this directory that begins with a numerical index Will be parsed, and in the numerical order .. so many many unorthodox files !
These files make up /boot/grub/grub.cfg what the kernel parses and boots up from.

Let's get started:
We WILL NOT reboot until grub is purged/(RE-)installed;
We will not even start this if there is a possibility of a power failure, a power failure now will be catastrophic, and I do not even want to build this system back from very uncertain initrd.img and initramfs system files ! Not even to be considered. Loose power, we do a fresh clean install !
-Put the cat outside ! -
```

mkdir ~/home/save-grub
sudo mv /etc/grub.d/00_header.dpkg-dist /etc/grub.d/00_header ##back to default name- size is correct assume the file is intact
sudo mv /etc/grub.d/os-prober_proxy ~/home/save-grub
sudo mv /etc/grub.d/05_debian_theme.dpkg-dist /etc/grub.d/05_debian_theme ##back to default name
sudo mv /etc/grub.d/10_linux.dpkg-dist /etc/grub.d/10_linux ##yep. default
sudo mv /etc/grub.d/11_header ~/home/save-grub
sudo mv /etc/grub.d/12_debian_theme ~/home/save-grub
sudo mv /etc/grub.d/13_linux ~/home/save-grub
sudo mv /etc/grub.d/14_linux_xen ~/home/save-grub
sudo mv /etc/grub.d/20_linux_xen.dpkg-dist /etc/grub.d/20_linux_xen ##correct file correct placement
sudo mv /etc/grub.d/15_memtest86+ ~/home/save-grub
sudo mv /etc/grub.d/20_memtest86+.dpkg-dist /etc/grub.d/20_memtest86+
sudo mv /etc/grub.d/16_os-prober_proxy ~/home/save-grub
sudo mv /etc/grub.d/17_custom ~/home/save-grub
sudo mv /etc/grub.d/18_custom ~/home/save-grub
sudo mv /etc/grub.d/30_os-prober.dpkg-dist /etc/grub.d/30_os-prober
touch /etc/grub.d/40_custom ## I will provide the contents to copy to##
sudo mv /etc/grub.d/41_custom.dpkg-dist /etc/grub.d/41_custom
sudo mv -R /etc/grub.d/bin~/home/save-grub
sudo mv -R /etc/grub.d/proxifiedScripts~/home/save-grub

```

Proof read, see if yall see any errors and things I have left out !
Now show us the results, checking to see what I have missed !
```

ls -al /etc/grub.d

```

And onto the '/etc/default/gub' file, and make these changes:
```

gksudo gedit /etc/default/grub

```
line 1 that is - GRUB_DEFAULT="8" - change the '8' to '0' (that is a zero)
line 3 that is - GRUB_HIDDEN_TIMEOUT_QUIET="true" - change 'true to 'false'

save the file; and exit back to terminal
An now for that moment of truth !
```

sudo update-grub

``` 
EDIT: Show us that output !
as a interim step, we are still going to purge all this and (re-)install from scratch.

Report the status at this time, if all is acceptable, we proceed to purge !

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-22
[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options") has an advanced [purge option]("http://pix.toile-libre.org/upload/img/1357337899.png").

---

### Post by Weidbrewer on 2014-08-22
Oh my goodness me my...that's a lot to digest.

> **Bashing-om said:**
> 
EDIT: Show us that output !
as a interim step, we are still going to purge all this and (re-)install from scratch.

Report the status at this time, if all is acceptable, we proceed to purge !


Okay, so there's something that will be after all of that before we can reboot/power off after all that?  In that case, I am going to wait until I get back in town Sunday just in case, since I'll be shutting down before I leave tomorrow morning.


> **kansasnoob said:**
> [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options") has an advanced [purge option]("http://pix.toile-libre.org/upload/img/1357337899.png").

Is that in addition to, instead of, or just FYI for anything in Bash's post?

(thank you both for the continued help and effort.)

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Welp;

You have to be comfortable when we start this.
Can not hurt a thing to try  boot-repair, but I have had some bad experiences with it's miss use and one will not learn anything when used. However, it is a fast fix - when it is able to work ! And that is one smart tool !

We are going to start and do all this, get to the point of "sudo update-grub", look over that result and if things do look favorable then ->
Purge grub, (RE-)install grub from scratch, take a good long hard look at the produced file " /boot/grub/grub.cfg " AND when that file looks good
At that point and ONLY then do we see what happens at the reboot.

Coming up from the reboot we best be booting the 'trusty' kernel .. else it is back to the drawing board to find out the why not.
If then we are able to boot and booting the 'trusty' kernel .. we go to work on the kernel dependencies and eliminating all but the current booting 'trusty' kernel and 1 other.

Finally we get to those little niggly dependency issues with the "other" software.

Now that is my plan,
kansasnoob, what say you ?
Weidbrewer; now is your time to speak -> you have the floor.

[INDENT][INDENT][INDENT]kansasnoob told ya
[INDENT][INDENT][INDENT]ain't going to be easy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
> **Bashing-om said:**
> Weidbrewer; Welp;

You have to be comfortable when we start this.


And that's the exact reason I'll most likely wait until I' back.  That gives me time to review all the syntax and can leave the machine running if I hit a snag and you aren't around.  No need to rush myself (unless I get hit with a bit of insanity later tonight)

---

### Post by Weidbrewer on 2014-08-22
Decided, "What the hell."

Here are the lines that I had issues with:

```
sudo mv /etc/grub.d/os-prober_proxy /home/me/save-grub #used a different location
```

It could not find /etc/grub.d/os-prober_proxy

```
*****@*****:~$ touch /etc/grub.d/40_custom ## I will provide the contents to copy to##
touch: cannot touch ‘/etc/grub.d/40_custom’: Permission denied
*****@*****:~$ sudo mv /etc/grub.d/41_custom.dpkg-dist /etc/grub.d/41_custom
*****@*****:~$ sudo mv -R /etc/grub.d/bin /home/me/save-grub
mv: invalid option -- 'R'
Try 'mv --help' for more information.
sudo mv -R /etc/grub.d/proxifiedScripts /home/me/save-grub
mv: invalid option -- 'R'
```

I'm thinking I might have missed something in translation with this section (such as a 'sudo' before the touch part.)  Let me know, and then I'll move on to the next step in your suggestions.

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Yeah !

But ya have about 2 hours before that insanity attack will be null and void.
( I look forward to starting this on a Monday )

[INDENT][INDENT]we be step'n
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
> **Bashing-om said:**
> Weidbrewer; Yeah !
( I look forward to starting this on a Monday )



Um....see my last post.  I invoked the insanity clause... :)

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Hey, I am back !

Making my rounds!
OK; -
1) "It could not find /etc/grub.d/os-prober_proxy" that is true, that file does not exist:
ya missed the '16' as in:
/etc/grub.d/[color=blue]16[/color]_os-prober_proxy ~/home/save-grub

2) touch /etc/grub.d/40_custom :
Yup, you are correct need to use 'sudo"
so:
sudo touch /etc/grub.d/40_custom
and copy into:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

3) sudo mv -R /etc/grub.d/bin /home/me/save-grub -> mv: invalid option -- 'R'
YUP ! My bad, no such option for that command
TRY as: sudo mv -T /etc/grub.d/bin /home/me/save-grub
I do not recall if the destination directory must exist.

same same with "sudo mv -T /etc/grub.d/proxifiedScripts"

heh !
[INDENT][INDENT][INDENT]are we having fun now ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
Still having issues:

```
mv: cannot move ‘/etc/grub.d/bin’ to ‘/home/me/save-grub’: Directory not empty
mv: cannot move ‘/etc/grub.d/proxifiedScripts’ to ‘/home/me/save-grub’: Directory not empty

```

But we're getting closer!

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Not too shabby;

Let's just do it and be done:
```

mkdir /home/me/save-grub/bin
sudo cp -R /etc/grub.d/bin /home/me/save-grub/bin
mkdir /home/me/save-grub/proxifiedScripts
sudo cp -R /etc/grub.d/proxifiedScripts /home/me/save-grub/proxifiedScripts

##make sure the files have been moved and are inplace, 
ls -la /home/me/save-grub/bin
ls -la /home/me/save-grub/proxifiedScripts
##then:
sudo rm -R /etc/grub.d/bin
sudo rm -R /etc/grub.d/proxifiedScripts

```

Now, let's look and check.
post back the output of:
```

ls -la /etc/grub.d

```

and let's look and see if I have missed anything else.

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
Here's what we've got:

```
$ ls -la /etc/grub.d
total 96
drwxr-xr-x   2 root root  4096 Aug 22 20:49 .
drwxr-xr-x 175 root root 12288 Aug 22 20:20 ..
-rwxr-xr-x   1 root root  9424 May 15 15:02 00_header
-rwxr-xr-x   1 root root   188 Mar 20  2013 00_os-prober_proxy
-rwxr-xr-x   1 root root  6058 May  8 08:08 05_debian_theme
-rwxr-xr-x   1 root root 11608 May 15 15:02 10_linux
-rwxr-xr-x   1 root root 10412 May 15 15:02 20_linux_xen
-rwxr-xr-x   1 root root  1992 Mar 12 08:31 20_memtest86+
-rwxr-xr-x   1 root root 11692 May 15 15:02 30_os-prober
-rwxr-xr-x   1 root root  1416 May 15 15:02 30_uefi-firmware
-rw-r--r--   1 root root   214 Aug 22 20:20 40_custom
-rw-r--r--   1 root root     0 Aug 22 20:20 40_custom~
-rwxr-xr-x   1 root root   216 May 15 15:02 41_custom
-rw-r--r--   1 root root   483 Apr 13  2010 README

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Hey, only missed one !

Move: "00_os-prober_proxy" out of the /etc/grub.d directory.
and
get rid of the added empty file ( will really hose up the works !) "0 Aug 22 20:20 40_custom~"
```

sudo rm /etc/grub.d/40_custom~

```

And move on to editing the /etc/default/grub file.

[INDENT][INDENT]hey hey .. getting there !
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
<drumroll>

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Yeah ! - 5 beats to the bar !

So recon what gives with " no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory " ??

What and why have you got something like "loadparm.c:4864" running ?

We getting closer and closer to doing grub in !

[INDENT][INDENT]feel'n froggy, huh ?
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
If you look back, I've been including that line with most of my posts.  Baffled what it's from.

So what next?

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; yay !


looking good ! except that "leaking memory" is totally UnGood !
Lets look a bit and see what we can find out:
```

ls -la ./source3/param/
##or maybe as:
ls -la /source3/param/
##as it may not be a 'dot' file !
##and I do believe we can probably live with grub just as it is ... I betcha !##
##let's look at the kernel issue  that grub do not want to even look at, but let's do look at:
dpkg -l | grep linux-

```

[INDENT][INDENT]look'n bright
[INDENT][INDENT][INDENT]sunglasses ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
```
*****@*****:~$ ls -la ./source3/param/
ls: cannot access ./source3/param/: No such file or directory
*****@*****:~$ ls -la /source3/param/
ls: cannot access /source3/param/: No such file or directory
*****@*****:~$ dpkg -l | grep -linux-
grep: invalid option -- '-'
Usage: grep [OPTION]... PATTERN [FILE]...
Try 'grep --help' for more information.

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Humm ???

Why would the system miss-represent the truth ?
> 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory


```

ps aux

```
do you see anything relational to " loadparm" ?
Maybe we can 'find' it  ??

and yeah, haste makes waste .. typo for 'dpkg', make it:
```

dpkg -l | grep linux-

```

[INDENT][INDENT]merrily on our way
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
> **Bashing-om said:**
> 
```

ps aux

```
do you see anything relational to " loadparm" ?


Nope.  Nothing.

> 
```

dpkg -l | grep linux-

```


```

$ dpkg -l | grep linux-
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.34.40                                        amd64        Generic Linux kernel headers
ii  linux-image-2.6.32-28-generic                               2.6.32-28.55                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
iF  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-57-generic                                3.2.0-57.87                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-58-generic                                3.2.0-58.88                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-59-generic                                3.2.0-59.90                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-60-generic                                3.2.0-60.91                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-61-generic                                3.2.0-61.93                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-63-generic                                3.2.0-63.95                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-64-generic                                3.2.0-64.97                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-65-generic                                3.2.0-65.99                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic                                3.2.0-67.101                                        amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                         3.13.0.34.40                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-34.60                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
iU  syslinux-themes-debian                                      12-3                                                all          collection of boot loaders (theme metapackage)
rc  syslinux-themes-debian-squeeze                              12-3                                                all          collection of boot loaders (debian-squeeze theme)
iU  syslinux-themes-debian-wheezy                               12-3                                                all          collection of boot loaders (debian-wheezy theme)

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Welp;

How bout we go look'n and see what we can 'find' ?
What returns from:
```

sudo find / -name "loadparm*"

```
Give it plenty of time to complete, takes a lot of time for the system to search all files on the system.

and while on my mind ! 'fore it slipps away:
```

ls -la /
ls -la /boot
cat /boot/grub/grub.cfg

```
and we shift focus to the old kernels.

[INDENT][INDENT]moving smartly along
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
While the other is running:

> **Bashing-om said:**
> 
```

ls -la /
ls -la /boot
cat /boot/grub/grub.cfg

```


```
*****@*****:~$ ls -la /
total 124
drwxr-xr-x  24 root root  4096 Aug 21 21:22 .
drwxr-xr-x  24 root root  4096 Aug 21 21:22 ..
drwxr-xr-x   2 root root  4096 Aug 14 23:54 bin
drwxr-xr-x   4 root root  4096 Aug 21 22:11 boot
drwxr-xr-x   2 root root  4096 Nov 30  2010 cdrom
drwxr-xr-x  16 root root  4460 Aug 22 21:06 dev
drwxr-xr-x 175 root root 12288 Aug 22 21:06 etc
drwxr-xr-x   5 root root  4096 Aug 21 21:22 grub
drwxr-xr-x   5 root root  4096 Aug 22 19:00 home
lrwxrwxrwx   1 root root    33 Aug 15 00:13 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root root    33 Aug  3 20:54 initrd.img.old -> /boot/initrd.img-3.2.0-67-generic
drwxr-xr-x  26 root root 12288 Aug 15 18:23 lib
drwxr-xr-x   2 root root  4096 Aug 14 22:15 lib64
drwx------   2 root root 16384 Nov 30  2010 lost+found
drwxr-xr-x  16 root root  4096 Aug 15 20:19 media
drwxr-xr-x   3 root root  4096 Mar 11 21:30 mnt
drwxr-xr-x   4 root root  4096 Aug 20 22:19 opt
dr-xr-xr-x 248 root root     0 Aug 21 21:26 proc
drwx------  16 root root  4096 Aug 21 21:25 root
drwxr-xr-x  26 root root   980 Aug 22 08:05 run
drwxr-xr-x   2 root root 12288 Aug 15 18:22 sbin
drwxr-xr-x   2 root root  4096 Apr 27  2010 srv
drwxr-xr-x  13 root root     0 Aug 21 21:26 sys
drwxrwxrwt  13 root root 12288 Aug 22 21:52 tmp
drwxr-xr-x  10 root root  4096 Jul 24  2012 usr
drwxr-xr-x  15 root root  4096 Aug 15 07:21 var
lrwxrwxrwx   1 root root    30 Aug 15 00:13 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root root    29 Aug  3 20:54 vmlinuz.old -> boot/vmlinuz-3.2.0-67-generic
*****@*****:~$ ls -la /boot
total 80808
drwxr-xr-x  4 root root     4096 Aug 21 22:11 .
drwxr-xr-x 24 root root     4096 Aug 21 21:22 ..
-rw-r--r--  1 root root   646144 Jan 10  2011 abi-2.6.32-28-generic
-rw-r--r--  1 root root  1162712 Aug 13 12:45 abi-3.13.0-34-generic
-rw-r--r--  1 root root   795963 Jul 15 14:11 abi-3.2.0-67-generic
-rw-r--r--  1 root root   110590 Jan 10  2011 config-2.6.32-28-generic
-rw-r--r--  1 root root   165611 Aug 13 12:45 config-3.13.0-34-generic
-rw-r--r--  1 root root   140641 Jul 15 14:11 config-3.2.0-67-generic
drwxr-xr-x  3 root root     4096 Aug 21 22:11 extlinux
drwxr-xr-x  5 root root    12288 Aug 22 21:06 grub
-rw-r--r--  1 root root  9855879 Aug 17  2011 initrd.img-2.6.32-28-generic
-rw-r--r--  1 root root 27509419 Aug 21 22:11 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18483924 Aug 14 22:28 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2157108 Jan 10  2011 System.map-2.6.32-28-generic
-rw-------  1 root root  3381262 Aug 13 12:45 System.map-3.13.0-34-generic
-rw-------  1 root root  2896997 Jul 15 14:11 System.map-3.2.0-67-generic
-rw-r--r--  1 root root     1336 Jan 10  2011 vmcoreinfo-2.6.32-28-generic
-rw-r--r--  1 root root  4052512 Jan 10  2011 vmlinuz-2.6.32-28-generic
-rw-------  1 root root  5797728 Aug 13 12:45 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  4986960 Jul 15 14:11 vmlinuz-3.2.0-67-generic
*****@*****:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
else
  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5e8ac879-97e7-4e97-bd89-bf101656a290' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-67-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-67-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.2.0-67-generic ...'
		linux	/boot/vmlinuz-3.2.0-67-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-67-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-67-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-67-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.2.0-67-generic ...'
		linux	/boot/vmlinuz-3.2.0-67-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-67-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-28-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 2.6.32-28-generic ...'
		linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-2.6.32-28-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-28-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 2.6.32-28-generic ...'
		linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-2.6.32-28-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-3886265E86261CBE' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  3886265E86261CBE
	else
	  search --no-floppy --fs-uuid --set=root 3886265E86261CBE
	fi
	parttool ${root} hidden-
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
*****@*****:~$ ls -la /
total 124
drwxr-xr-x  24 root root  4096 Aug 21 21:22 .
drwxr-xr-x  24 root root  4096 Aug 21 21:22 ..
drwxr-xr-x   2 root root  4096 Aug 14 23:54 bin
drwxr-xr-x   4 root root  4096 Aug 21 22:11 boot
drwxr-xr-x   2 root root  4096 Nov 30  2010 cdrom
drwxr-xr-x  16 root root  4460 Aug 22 21:06 dev
drwxr-xr-x 175 root root 12288 Aug 22 21:06 etc
drwxr-xr-x   5 root root  4096 Aug 21 21:22 grub
drwxr-xr-x   5 root root  4096 Aug 22 19:00 home
lrwxrwxrwx   1 root root    33 Aug 15 00:13 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root root    33 Aug  3 20:54 initrd.img.old -> /boot/initrd.img-3.2.0-67-generic
drwxr-xr-x  26 root root 12288 Aug 15 18:23 lib
drwxr-xr-x   2 root root  4096 Aug 14 22:15 lib64
drwx------   2 root root 16384 Nov 30  2010 lost+found
drwxr-xr-x  16 root root  4096 Aug 15 20:19 media
drwxr-xr-x   3 root root  4096 Mar 11 21:30 mnt
drwxr-xr-x   4 root root  4096 Aug 20 22:19 opt
dr-xr-xr-x 248 root root     0 Aug 21 21:26 proc
drwx------  16 root root  4096 Aug 21 21:25 root
drwxr-xr-x  26 root root   980 Aug 22 08:05 run
drwxr-xr-x   2 root root 12288 Aug 15 18:22 sbin
drwxr-xr-x   2 root root  4096 Apr 27  2010 srv
drwxr-xr-x  13 root root     0 Aug 21 21:26 sys
drwxrwxrwt  13 root root 12288 Aug 22 21:52 tmp
drwxr-xr-x  10 root root  4096 Jul 24  2012 usr
drwxr-xr-x  15 root root  4096 Aug 15 07:21 var
lrwxrwxrwx   1 root root    30 Aug 15 00:13 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root root    29 Aug  3 20:54 vmlinuz.old -> boot/vmlinuz-3.2.0-67-generic
*****@*****:~$ ls -la /boot
total 80808
drwxr-xr-x  4 root root     4096 Aug 21 22:11 .
drwxr-xr-x 24 root root     4096 Aug 21 21:22 ..
-rw-r--r--  1 root root   646144 Jan 10  2011 abi-2.6.32-28-generic
-rw-r--r--  1 root root  1162712 Aug 13 12:45 abi-3.13.0-34-generic
-rw-r--r--  1 root root   795963 Jul 15 14:11 abi-3.2.0-67-generic
-rw-r--r--  1 root root   110590 Jan 10  2011 config-2.6.32-28-generic
-rw-r--r--  1 root root   165611 Aug 13 12:45 config-3.13.0-34-generic
-rw-r--r--  1 root root   140641 Jul 15 14:11 config-3.2.0-67-generic
drwxr-xr-x  3 root root     4096 Aug 21 22:11 extlinux
drwxr-xr-x  5 root root    12288 Aug 22 21:06 grub
-rw-r--r--  1 root root  9855879 Aug 17  2011 initrd.img-2.6.32-28-generic
-rw-r--r--  1 root root 27509419 Aug 21 22:11 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18483924 Aug 14 22:28 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2157108 Jan 10  2011 System.map-2.6.32-28-generic
-rw-------  1 root root  3381262 Aug 13 12:45 System.map-3.13.0-34-generic
-rw-------  1 root root  2896997 Jul 15 14:11 System.map-3.2.0-67-generic
-rw-r--r--  1 root root     1336 Jan 10  2011 vmcoreinfo-2.6.32-28-generic
-rw-r--r--  1 root root  4052512 Jan 10  2011 vmlinuz-2.6.32-28-generic
-rw-------  1 root root  5797728 Aug 13 12:45 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  4986960 Jul 15 14:11 vmlinuz-3.2.0-67-generic
*****@*****:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
else
  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5e8ac879-97e7-4e97-bd89-bf101656a290' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-67-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-67-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.2.0-67-generic ...'
		linux	/boot/vmlinuz-3.2.0-67-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-67-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-67-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-67-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 3.2.0-67-generic ...'
		linux	/boot/vmlinuz-3.2.0-67-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-67-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-28-generic-advanced-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 2.6.32-28-generic ...'
		linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro splash vga=795 quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-2.6.32-28-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-28-generic-recovery-5e8ac879-97e7-4e97-bd89-bf101656a290' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
		else
		  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
		fi
		echo	'Loading Linux 2.6.32-28-generic ...'
		linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5e8ac879-97e7-4e97-bd89-bf101656a290 ro recovery nomodeset splash vga=795
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-2.6.32-28-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5e8ac879-97e7-4e97-bd89-bf101656a290
	else
	  search --no-floppy --fs-uuid --set=root 5e8ac879-97e7-4e97-bd89-bf101656a290
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-3886265E86261CBE' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  3886265E86261CBE
	else
	  search --no-floppy --fs-uuid --set=root 3886265E86261CBE
	fi
	parttool ${root} hidden-
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Hey, hey !

Grub looks good to me !

let's poke at the kernel situation and see what results !
```

sudo apt-get install linux-headers-3.2.0-67-generic

```

[INDENT][INDENT]we still got traction ?
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
First off, the find "loadparm" did not return anything.

As for the latest:

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-67-generic
E: Couldn't find any package by regex 'linux-headers-3.2.0-67-generic'
```


BTW - not that I need to, but are we safe to reboot yet?

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; sheeshh,

That " Unable to locate package linux-headers-3.2.0-67-generic" kinda makes sense, as we are up now in 'trusty' and that 3.2 kernel is 'precise' and you are fortunate not to have done the HWE for the later stacks.

so .... Yeah ! reboot and let's see you come back up on the 'trusty' kernel !

[INDENT][INDENT]ain't gotta cross my fingers
[INDENT][INDENT][INDENT]too hard
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-22
Weidbrewer;

Car 54 - where are you ?

[INDENT][INDENT]my fingers were crossed
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
Sorry - I wandered away.  Gonna be turning in soon, since I gotta hit the road early.

Rebooted.

```
$ uname -r
3.13.0-34-generic

```

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; Hooray !

we can stop here .. I getting retarded also.
1st though ->
Let's take a gentle poke and see what results:
```

sudo dpkg -P linux-image-3.2.0-57-generic

```

[INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-22
Would it I good, but that's locked out right now...since I'm running the [partial] upgrade.  Not to jinx anything, but normally it would have crapped out by now with errors.   I'm gonna come back later and check.  Will keep you posted.

---

### Post by Bashing-om on 2014-08-22
Weidbrewer; OK,

see ya later, and 
[INDENT][INDENT][INDENT]pick this up
[INDENT][INDENT][INDENT][INDENT]cary'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-23
Okay, here's where I've left off - I can now boot up, install/uninstall things from synaptic and via command line...all that seems good.  However, on booting, I get a bunch of "System program problem detected" popups for all of these individually:

```
linux-image-3.2.0-58-generic
linux-image-3.13.0-34-generic
linux-image-3.2.0-64-generic
linux-image-3.2.0-63-generic
linux-image-3.2.0-61-generic
linux-image-3.2.0-59-generic
memtest86+

```

Also, I did a little bit of googling, and that memory leak seems to be reported in conjunction with Samba for some reason.

---

### Post by Bashing-om on 2014-08-23
Weidbrewer; Morning;

This one:
> 
linux-image-3.13.0-34-generic

concerns me the most:
Let's see what we can do:
```

sudo apt-get install --reinstall linux-headers-3.13.0-34-generic
sudo apt-get install --reinstall linux-image-3.13.0-34-generic

```
see how the package manager responds, and take action from there.

[INDENT][INDENT]a comprehension of
[INDENT][INDENT][INDENT][INDENT]the process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-25
Okay...no obvious errors.  Next?


EDIT:  Just did a reboot, and no system problem pop-ups.  Dare we hope we've fixed it all?

---

### Post by Bashing-om on 2014-08-25
Weidbrewer; Well !

Wonders never do cease, do they ?

Let's test and see if all in is order:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade #nope, only deals with installed packages, not new releases !
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove ## pay attention here as to what is going to be removed !
##should remove all the old kernels -less current and 1 other, AND any straggler system files
##look to be aware of potential problems with what the package manager removes from the system
dpkg -l | grep linux-
ls -la /lib/modules
sudo apt-get -f install

```

If '-f install' has no return, we are home free !

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-25
I assume you wanted to see this part:

```
$ dpkg -l | grep linux-
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.34.40                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic                                3.2.0-67.101                                        amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.34.40                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-34.60                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3                                                all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3                                                all          collection of boot loaders (debian-wheezy theme)
******@********:~$ ls -la /lib/modules
total 28
drwxr-xr-x  5 root root  4096 Aug 15 18:28 .
drwxr-xr-x 26 root root 12288 Aug 15 18:23 ..
drwxr-xr-x  2 root root  4096 Aug 23 02:19 2.6.32-28-generic
drwxr-xr-x  6 root root  4096 Aug 25 11:46 3.13.0-34-generic
drwxr-xr-x  5 root root  4096 Aug 15 18:27 3.2.0-67-generic

```

I am really wondering about this:

```
2.6.32-28-generic
```

Several times, I've been sure I removed that.

Still have that pesky memory leak.  Also, strangely, I've regularly had the issue where the first time I enter my password for sudo each session, it rejects it.  I've been paying attention, and it IS entered correctly...just rejects it.  Not a huge issue, just annoying.

---

### Post by Bashing-om on 2014-08-25
Weidbrewer; Well !

I had fully expected "autoremove" to take out those old kernels .,.,
We will take them out ourselves and maybe in the process of doing so see why the package manager did not.
Show me how we are now booting - for confirmation of what NOT to remove:
```

ls -al /
ls -al /boot
ls -al /usr/src

```

as to the memory leak .. I bet ya got something ( samba ?) starting in a startup file somewhere, and the application no longer exists on the system, such that the hole is left. System logs should give an indication of what/when/where .

The identity crisis... do not know .. maybe by the time we get the kernel's situation resolved will see about rebuilding the initramfs image, maybe see what effect that has . 

[INDENT][INDENT]we be a long way
[INDENT][INDENT][INDENT]from where we started
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-25
Yeah, like I said the other day, some googling suggested Samba as well.

Here's the other:

```
$ ls -al /
total 124
drwxr-xr-x  24 root root  4096 Aug 21 21:22 .
drwxr-xr-x  24 root root  4096 Aug 21 21:22 ..
drwxr-xr-x   2 root root  4096 Aug 14 23:54 bin
drwxr-xr-x   4 root root  4096 Aug 25 11:47 boot
drwxr-xr-x   2 root root  4096 Nov 30  2010 cdrom
drwxr-xr-x  16 root root  4240 Aug 25 11:57 dev
drwxr-xr-x 171 root root 12288 Aug 25 13:05 etc
drwxr-xr-x   5 root root  4096 Aug 21 21:22 grub
drwxr-xr-x   5 root root  4096 Aug 22 19:00 home
lrwxrwxrwx   1 root root    33 Aug 15 00:13 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root root    33 Aug  3 20:54 initrd.img.old -> /boot/initrd.img-3.2.0-67-generic
drwxr-xr-x  26 root root 12288 Aug 15 18:23 lib
drwxr-xr-x   2 root root  4096 Aug 14 22:15 lib64
drwx------   2 root root 16384 Nov 30  2010 lost+found
drwxr-xr-x  15 root root  4096 Aug 25 11:42 media
drwxr-xr-x   3 root root  4096 Mar 11 21:30 mnt
drwxr-xr-x   4 root root  4096 Aug 20 22:19 opt
dr-xr-xr-x 221 root root     0 Aug 25 11:56 proc
drwx------  16 root root  4096 Aug 21 21:25 root
drwxr-xr-x  26 root root   900 Aug 25 11:58 run
drwxr-xr-x   2 root root 12288 Aug 15 18:22 sbin
drwxr-xr-x   2 root root  4096 Apr 27  2010 srv
dr-xr-xr-x  13 root root     0 Aug 25 11:56 sys
drwxrwxrwt  11 root root 12288 Aug 25 16:17 tmp
drwxr-xr-x  10 root root  4096 Jul 24  2012 usr
drwxr-xr-x  15 root root  4096 Aug 15 07:21 var
lrwxrwxrwx   1 root root    30 Aug 15 00:13 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root root    29 Aug  3 20:54 vmlinuz.old -> boot/vmlinuz-3.2.0-67-generic
****@*****:~$ ls -al /boot
total 64360
drwxr-xr-x  4 root root     4096 Aug 25 11:47 .
drwxr-xr-x 24 root root     4096 Aug 21 21:22 ..
-rw-r--r--  1 root root  1162712 Aug 13 12:45 abi-3.13.0-34-generic
-rw-r--r--  1 root root   795963 Jul 15 14:11 abi-3.2.0-67-generic
-rw-r--r--  1 root root   165611 Aug 13 12:45 config-3.13.0-34-generic
-rw-r--r--  1 root root   140641 Jul 15 14:11 config-3.2.0-67-generic
drwxr-xr-x  3 root root     4096 Aug 25 11:47 extlinux
drwxr-xr-x  5 root root    12288 Aug 25 11:47 grub
-rw-r--r--  1 root root 27508524 Aug 25 11:47 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18483924 Aug 14 22:28 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-------  1 root root  3381262 Aug 13 12:45 System.map-3.13.0-34-generic
-rw-------  1 root root  2896997 Jul 15 14:11 System.map-3.2.0-67-generic
-rw-------  1 root root  5797728 Aug 13 12:45 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  4986960 Jul 15 14:11 vmlinuz-3.2.0-67-generic
****@*****:~$ ls -al /usr/src
total 20
drwxrwsr-x  5 root src  4096 Aug 15 18:27 .
drwxr-xr-x 10 root root 4096 Jul 24  2012 ..
drwxr-xr-x  5 root root 4096 Aug 14 23:43 bcmwl-6.30.223.141+bdcom
drwxr-xr-x 24 root root 4096 Aug 14 23:54 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 25 11:46 linux-headers-3.13.0-34-generic

```

---

### Post by Bashing-om on 2014-08-25
Weidbrewer; Hey;

On 2nd look, not looking too shabby at all !

```

sudo apt-get install linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic --fix-missing

```

Not at all sure what prompts this:
> 
/lib/modules -> drwxr-xr-x  2 root root  4096 Aug 23 02:19 2.6.32-28-generic

Why it is still hanging about !
Let's see what returns:
```

sudo dpkg -P linux-image-2.6.32-28-generic
sudo dpkg -P linux-headers-2.6.32-28-generic

```
Depending on IF/what returns is what I think we do for this old kernel.

Overall,
[INDENT][INDENT][INDENT]look'n good[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-25
> **Bashing-om said:**
> 

```

sudo apt-get install linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic --fix-missing

```



```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-67
E: Couldn't find any package by regex 'linux-headers-3.2.0-67'
E: Unable to locate package linux-headers-3.2.0-67-generic
E: Couldn't find any package by regex 'linux-headers-3.2.0-67-generic'

```

> 
```

sudo dpkg -P linux-image-2.6.32-28-generic
sudo dpkg -P linux-headers-2.6.32-28-generic

```


```
~$ sudo dpkg -P linux-image-2.6.32-28-generic
dpkg: warning: ignoring request to remove linux-image-2.6.32-28-generic which isn't installed
~$ sudo dpkg -P linux-headers-2.6.32-28-generic
dpkg: warning: ignoring request to remove linux-headers-2.6.32-28-generic which isn't installed

```

---

### Post by Bashing-om on 2014-08-25
Weidbrewer; Hey;

Good . Not at all surprised,
kernel stuff for the 3.2 series  will not exist in trusty's repository ( I should have known that !) Let's leave well enough alone and wait for the next kernel update to install an additional kernel, then we can remove the 3.2.0-67 kernel.

As the system is no longer tracking 2.6.32-28, it is safe to remove:
```

sudo rm -R /lib/modules/2.6.32-28-generic

```
That should be the last you here from it.

And now let's see about that identity crisis:
```

sudo update-initramfs -u

``` now that all is cleaned up and running well, rebuilding the image file(s) to what is current on the system.

Reboot .
[INDENT][INDENT]finer than a frog's hair ??
[/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-26
Whoops...Gmail decided to start marking update notifications as spam.

> **Bashing-om said:**
> 

```

sudo rm -R /lib/modules/2.6.32-28-generic

```

```

sudo update-initramfs -u

``` now that all is cleaned up and running well, rebuilding the image file(s) to what is current on the system.

Reboot .


Done, done and done.

---

### Post by Bashing-om on 2014-08-26
> **Weidbrewer said:**
> Whoops...Gmail decided to start marking update notifications as spam.



Done, done and done.

^^ are we done ?

[INDENT][INDENT][INDENT]close but ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-27
Anything we can do to check to be sure?  How about tracking down the memory leak that only cropped up after the upgrade?

Anything I can pre-check on the other machines to make sure this doesn't happen with them?

---

### Post by Bashing-om on 2014-08-27
Weidbrewer; Well;
As to:
> 
How about tracking down the memory leak that only cropped up after the upgrade?

All I know to do is read the logs, see if we can spot an anomaly . Take it from there.

> 
Anything I can pre-check on the other machines to make sure this doesn't happen with them?

ubuntu is very good about taking care of it's own, the same can not be said for 3rd party installed software.
1) Revert all PPAs to what is available in the official repository and then disable the sources;
2) The above is particularly applicable to any drivers ( graphics, networking, printers !);
3) The system is fully updated and upgraded prior to release upgrade ( Watch out for HWE );
4) Old kernels are removed, prior;
5) Insure there is plenty of operational head room, NO partitions are bumping the limit;
6) Screensaver is disabled.

Once you are as close to default as possible, fully updated, plenty of head space -> go for it !

Doing these, I have never had a problem doing an on-line release upgrade ( but, I do try and have a liveDVD on hand - just in case !).

---

### Post by Weidbrewer on 2014-08-30
Well...then I shall proceed as normal and hope for the best.  I can always submit another thread, if need be :)

Seriously, though, I'd never had a problem like this with an upgrade before.  Here's hoping it's the last one.

On a personal note, I want to thank you for the help, and the nice way in which it happened.  I've been a member of these forums for a number of years, but I'd come to avoid asking questions like the plague, because the responses in here tend to range from insulting to downright belligerent.  I followed this thread in a state of cringing for two days waiting for it, but it never came.  Thanks again!

---

### Post by Bashing-om on 2014-08-30
Weidbrewer; Well;

Adhering to the guideline, you will have no problem.

In respect to this forum:
> 
 because the responses in here tend to range from insulting to downright belligerent. 

I can not say I encounter such - admittedly I see but a fraction of all these numerous posts.
However;
That attitude is unacceptable, In the event that you do encounter such behavior, please use the provided "abuse" button for proper action to be taken.
This forum is to formulate solutions, promote 'buntu, teach and as well guide. "insult to downright belligerents" has no place in the mandate And is contrary to the ubuntu philosophy  .

And yeah, If you are satisfied the original issue is concluded. Then:
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 

The other issues are better addressed in new thread(s) to gain a broader viewing audience.

We are all in this together
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

### Post by Iowan on 2014-08-30
> **Bashing-om said:**
>  In the event that you do encounter such behavior, please use the provided "abuse" button for proper action to be taken.It's currently labeled "Report Post" but the idea is the same.

---

### Post by Bashing-om on 2014-09-01
Weidbrewer;Gone, but not forgotten !

In respect to the memory leak: check:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186)
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680)

See if these also affect you.

[INDENT][INDENT][INDENT]there be a process
[/INDENT][/INDENT][/INDENT]

---

