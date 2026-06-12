---
title: "dist-upgrade problem with linux-image-generic-3.11.0-14.15"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by heavyonion on 2013-11-21
I was just trying to update:

I ran sudo apt-get update        No problem.
sudo apt-get dist-upgrade and I keep getting this

The following partially installed packages will be configured:
  linux-generic linux-image linux-image-3.11.0-14-generic 
  linux-image-extra-3.11.0-14-generic linux-image-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up linux-image-3.11.0-14-generic (3.11.0-14.21) ...
Internal Error: Could not find image (/boot/vmlinuz-3.11.0-14-generic)
dpkg: error processing linux-image-3.11.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-14-generic:
 linux-image-extra-3.11.0-14-generic depends on linux-image-3.11.0-14-generic; however:
  Package linux-image-3.11.0-14-generic is not configured yet.


dpkg: error processing linux-image-extra-3.11.0-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.11.0-14-generic; however:
  Package linux-image-3.11.0-14-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.11.0-14-generic; however:
  Package linux-image-extra-3.11.0-14-generic is not configured yet.


No apport report written because MaxReports is reached already
                                                              dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.11.0.14.15); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-image (--configure):No apport report written because MaxReports is reached already


 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.11.0-14-generic
 linux-image-extra-3.11.0-14-generic
 linux-image-generic
 linux-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.11.0-14-generic (3.11.0-14.21) ...
Internal Error: Could not find image (/boot/vmlinuz-3.11.0-14-generic)
dpkg: error processing linux-image-3.11.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-14-generic:
 linux-image-extra-3.11.0-14-generic depends on linux-image-3.11.0-14-generic; however:
  Package linux-image-3.11.0-14-generic is not configured yet.


dpkg: error processing linux-image-extra-3.11.0-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.11.0-14-generic; however:
  Package linux-image-3.11.0-14-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.11.0-14-generic; however:
  Package linux-image-extra-3.11.0-14-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.11.0.14.15); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.11.0-14-generic
 linux-image-extra-3.11.0-14-generic
 linux-image-generic
 linux-generic
 linux-image

I have tried to configure and remove var lock files and nothing works????

Thank you for your time.

---

### Post by Bashing-om on 2013-11-21
heavyonion; Hi !

I'll start this ball rolling !
This:
> 
Internal Error: Could not find image (/boot/vmlinuz-3.11.0-14-generic)

says the package manager is looking:
 Show the output of terminal code:
```

dpkg -l | grep linux-image
ls -la /boot
lsb_release -a
uname -a

```

Maybe as easy as installing what the package manager wants ?

[INDENT][INDENT]hey, it's a start
[/INDENT][/INDENT]

---

### Post by heavyonion on 2013-11-21
~# dpkg -l | grep linux-image
iU  linux-image                                           3.11.0.14.15                            i386         Generic Linux kernel image.
rc  linux-image-3.10.0-2-generic                          3.10.0-2.11                             i386         Linux kernel image for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-3.10.0-3-generic                          3.10.0-3.12                             i386         Linux kernel image for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-3.10.0-4-generic                          3.10.0-4.13                             i386         Linux kernel image for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-3.10.0-5-generic                          3.10.0-5.15                             i386         Linux kernel image for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-3.10.0-6-generic                          3.10.0-6.17                             i386         Linux kernel image for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-0-generic                          3.11.0-0.3                              i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-11-generic                         3.11.0-11.17                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-12-generic                         3.11.0-12.19                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-13-generic                         3.11.0-13.20                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
iF  linux-image-3.11.0-14-generic                         3.11.0-14.21                            i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-2-generic                          3.11.0-2.5                              i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-3-generic                          3.11.0-3.8                              i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-4-generic                          3.11.0-4.9                              i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-7-generic                          3.11.0-7.13                             i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-8-generic                          3.11.0-8.15                             i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.10.0-2-generic                    3.10.0-2.11                             i386         Linux kernel extra modules for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-extra-3.10.0-3-generic                    3.10.0-3.12                             i386         Linux kernel extra modules for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-extra-3.10.0-4-generic                    3.10.0-4.13                             i386         Linux kernel extra modules for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-extra-3.10.0-5-generic                    3.10.0-5.15                             i386         Linux kernel extra modules for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-extra-3.10.0-6-generic                    3.10.0-6.17                             i386         Linux kernel extra modules for version 3.10.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-0-generic                    3.11.0-0.3                              i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-11-generic                   3.11.0-11.17                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                   3.11.0-12.19                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-13-generic                   3.11.0-13.20                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
iU  linux-image-extra-3.11.0-14-generic                   3.11.0-14.21                            i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-2-generic                    3.11.0-2.5                              i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-3-generic                    3.11.0-3.8                              i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-4-generic                    3.11.0-4.9                              i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-7-generic                    3.11.0-7.13                             i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-8-generic                    3.11.0-8.15                             i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
iU  linux-image-generic                                   3.11.0.14.15                            i386         Generic Linux kernel image
root@:~# ls -la /boot
total 52128
drwxr-xr-x  5 root root     3072 Nov 21 13:50 .
drwxr-xr-x 22 root root     4096 Nov 21 13:47 ..
-rw-r--r--  1 root root  1010091 Oct 23 13:00 abi-3.11.0-13-generic
-rw-r--r--  1 root root  1009311 Sep 10 15:59 abi-3.11.0-7-generic
-rw-r--r--  1 root root   168537 Oct 23 13:00 config-3.11.0-13-generic
-rw-r--r--  1 root root   168716 Sep 10 15:59 config-3.11.0-7-generic
drwxr-xr-x  3 root root     1024 Nov 21 13:50 extlinux
drwxr-xr-x  5 root root     1024 Nov 21 13:51 grub
-rw-r--r--  1 root root 16931748 Oct 28 19:45 initrd.img-3.11.0-13-generic
-rw-r--r--  1 root root 16921450 Sep 13 17:05 initrd.img-3.11.0-7-generic
drwxr-xr-x  2 root root    12288 Jul  5 17:38 lost+found
-rw-r--r--  1 root root   176500 Jun 17 04:52 memtest86+.bin
-rw-r--r--  1 root root   178680 Jun 17 04:52 memtest86+_multiboot.bin
-rw-------  1 root root  2621288 Oct 23 13:00 System.map-3.11.0-13-generic
-rw-------  1 root root  2640124 Sep 10 15:59 System.map-3.11.0-7-generic
-rw-------  1 root root  5633040 Oct 23 13:00 vmlinuz-3.11.0-13-generic
-rw-------  1 root root  5672464 Sep 10 15:59 vmlinuz-3.11.0-7-generic
root@:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
root@:~# uname -a
Linux  3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 17:26:33 UTC 2013 i686 i686 i686 GNU/Linux

---

### Post by Bashing-om on 2013-11-21
heavyonion; UUhhh,

Some one acted with out thinking it through, huh.
OK, lets do some cleanup:
let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Now let's see what results in an attempt to give the PM what it is asking for:
```

sudo apt-get update
sudo apt-get install linux-generic linux-image linux-image-generic
sudo apt-get install --reinstall linux-image-3.11.0-14-generic linux-image-extra-3.11.0-14-generic linux-headers-3.11.0-14-generic linux-headers-3.11.0-14

```

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by heavyonion on 2013-11-21
Actually I was just trying to change the repos to the Trusty Tahr Daily Builds and then when I tried to do-release-upgrade I started getting this linux image error. So I just left it alone but I ran into it every time I tried to update. I am pulling down the ISO Image of Tahr right now and I guess I can just upgrade from that or I can just start fresh. I am not too super invested in saving this Raring install because I was willing to try Tahr already witch is very unstable. Fun part is every time I jack something up I learn something new. That is why I test about 6 distro's at a time. Linux Rocks!!!
 Thank you sooooo much for your time.

---

### Post by Bashing-om on 2013-11-21
heavyonion; Hey,

Helping is not a problem !..
If you decide to upgrade-inplace, will have to fix this install first.

[INDENT][INDENT]what ever works best
[/INDENT][/INDENT]

---

