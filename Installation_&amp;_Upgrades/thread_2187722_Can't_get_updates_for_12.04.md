---
title: "Can't get updates for 12.04"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by lddimov on 2013-11-13
Any help will be appreciated - for a few months now I can't get updates for Ubuntu 12.04 due to not enough disk space, although there is more than enough disk space:

df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/sda6            7.2G  5.7G  1.2G  83% /
udev                 491M  4.0K  491M   1% /dev
tmpfs                201M  820K  200M   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                 501M  156K  501M   1% /run/shm
/dev/sda7            2.8G  719M  2.0G  27% /home
/home/user/.Private  2.8G  719M  2.0G  27% /home/user


user@user-Latitude-D810:~$ sudo apt-get clean
user@user-Latitude-D810:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-52-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

user@user-Latitude-D810:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libfile-find-rule-perl libnumber-compare-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-53 linux-headers-3.2.0-53-generic-pae
  linux-headers-generic-pae linux-image-3.2.0-53-generic-pae
  linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-53 linux-headers-3.2.0-53-generic-pae
  linux-image-3.2.0-53-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 0 to remove and 80 not upgraded.
4 not fully installed or removed.
Need to get 50.9 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-image-3.2.0-53-generic-pae i386 3.2.0-53.81 [38.3 MB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-generic-pae i386 3.2.0.53.63 [1,726 B]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-image-generic-pae i386 3.2.0.53.63 [2,358 B]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-3.2.0-53 all 3.2.0-53.81 [11.7 MB]
Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-3.2.0-53-generic-pae i386 3.2.0-53.81 [974 kB]
Get:6 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-generic-pae i386 3.2.0.53.63 [2,350 B]
Fetched 50.9 MB in 37s (1,373 kB/s)                                                 
(Reading database ... 461088 files and directories currently installed.)
Unpacking linux-image-3.2.0-53-generic-pae (from .../linux-image-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-53-generic-pae/kernel/net/bluetooth/bluetooth.ko.dpkg-new' (while processing `./lib/modules/3.2.0-53-generic-pae/kernel/net/bluetooth/bluetooth.ko'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
Unpacking linux-headers-3.2.0-53 (from .../linux-headers-3.2.0-53_3.2.0-53.81_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-53_3.2.0-53.81_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-53/include/sound/ak4641.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-53/include/sound/ak4641.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-53-generic-pae (from .../linux-headers-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-53-generic-pae/include/config/paride/kbic.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-53-generic-pae/include/config/paride/kbic.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-53_3.2.0-53.81_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-53-generic-pae_3.2.0-53.81_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2013-11-13
lddimov; Hi ! Welcome to the forum .

This:
> 
unable to create `/usr/src/linux-headers-3.2.0-53/include/sound/ak4641.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-53/include/sound/ak4641.h'): No space left on device

indeed says that you have space constraints. The ambiguous "No space left on device" can be misleading. It is not the hard disk in general that is referenced, but a particular partition.
Terminal codes:
```

df -h
df -i
du -h --max-depth=1 | sort -hr

```
points to where the problem lies ... I will surmise to the /boot partition:
show us the output - between code tags - of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-
ls -la /boot

```

And we will see what actions to be undertaken to get ya some room, and fix the kernels !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by lddimov on 2013-11-14
Here we go, all the output. Seems like the / is 100% full. Would deleting the old kernels help in this case? 
Thanks!

```

user@user-Latitude-D810:~$ df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/sda6            7.2G  5.7G  1.1G  85% /
udev                 491M  4.0K  491M   1% /dev
tmpfs                201M  816K  200M   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                 501M  156K  501M   1% /run/shm
/dev/sda7            2.8G  1.1G  1.6G  40% /home
/home/user/.Private  2.8G  1.1G  1.6G  40% /home/user

user@user-Latitude-D810:~$ df -i
Filesystem          Inodes  IUsed  IFree IUse% Mounted on
/dev/sda6           475136 474538    598  100% /
udev                125581    491 125090    1% /dev
tmpfs               128133    415 127718    1% /run
none                128133      3 128130    1% /run/lock
none                128133      8 128125    1% /run/shm
/dev/sda7           183264   6989 176275    4% /home
/home/user/.Private 183264   6989 176275    4% /home/user

user@user-Latitude-D810:~$ du -h --max-depth=1 | sort -hr
985M    .
339M    ./.cache
98M    ./Desktop
94M    ./tor-browser_en-US
88M    ./.clamtk
86M    ./.mozilla
84M    ./.adobe
69M    ./Pictures
50M    ./.thumbnails
42M    ./Documents
18M    ./Downloads
6.1M    ./.local
4.6M    ./.macromedia
2.6M    ./.thunderbird
2.6M    ./.config
2.4M    ./.compiz-1
892K    ./.gstreamer-0.10
584K    ./.gconf
520K    ./.dvdcss
84K    ./.pulse
76K    ./.gnupg
76K    ./.fontconfig
36K    ./.gnome2
24K    ./.vidalia
20K    ./.mission-control
20K    ./.dbus
8.0K    ./Ubuntu One
4.0K    ./Videos
4.0K    ./Templates
4.0K    ./Public
4.0K    ./Music
0    ./.gvfs

user@user-Latitude-D810:~$ dpkg -l | grep linux-image-
ii  linux-image-3.2.0-29-generic-pae       3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae       3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae       3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic-pae       3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae       3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic-pae       3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae       3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae       3.2.0-40.64                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic-pae       3.2.0-41.66                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic-pae       3.2.0-44.69                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae       3.2.0-48.74                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae       3.2.0-49.75                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae       3.2.0-51.77                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iF  linux-image-3.2.0-52-generic-pae       3.2.0-52.78                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae                3.2.0.52.62                             Generic Linux kernel image

user@user-Latitude-D810:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.2.0-32                 3.2.0-32.51                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic-pae     3.2.0-32.51                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic-pae     3.2.0-33.52                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic-pae     3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic-pae     3.2.0-37.58                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic-pae     3.2.0-38.61                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                 3.2.0-39.62                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic-pae     3.2.0-39.62                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic-pae     3.2.0-40.64                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic-pae     3.2.0-41.66                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                 3.2.0-44.69                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic-pae     3.2.0-44.69                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae     3.2.0-48.74                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                 3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic-pae     3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
iU  linux-headers-generic-pae              3.2.0.52.62                             Generic Linux kernel headers
user@user-Latitude-D810:~$ ls -la /boot
total 369224
drwxr-xr-x  3 root root     4096 Sep 20 21:57 .
drwxr-xr-x 23 root root     4096 Sep 20 22:55 ..
-rw-r--r--  1 root root   800453 Jul 27  2012 abi-3.2.0-29-generic-pae
-rw-r--r--  1 root root   801704 Sep 26  2012 abi-3.2.0-32-generic-pae
-rw-r--r--  1 root root   801704 Oct 18  2012 abi-3.2.0-33-generic-pae
-rw-r--r--  1 root root   801798 Dec  5  2012 abi-3.2.0-35-generic-pae
-rw-r--r--  1 root root   801908 Jan 24  2013 abi-3.2.0-37-generic-pae
-rw-r--r--  1 root root   802017 Feb 19  2013 abi-3.2.0-38-generic-pae
-rw-r--r--  1 root root   802017 Feb 27  2013 abi-3.2.0-39-generic-pae
-rw-r--r--  1 root root   804120 Mar 25  2013 abi-3.2.0-40-generic-pae
-rw-r--r--  1 root root   804183 Apr 25  2013 abi-3.2.0-41-generic-pae
-rw-r--r--  1 root root   804333 May 16 14:59 abi-3.2.0-44-generic-pae
-rw-r--r--  1 root root   804552 Jun  6 16:07 abi-3.2.0-48-generic-pae
-rw-r--r--  1 root root   804552 Jun 18 14:02 abi-3.2.0-49-generic-pae
-rw-r--r--  1 root root   804552 Jul 24 16:44 abi-3.2.0-51-generic-pae
-rw-r--r--  1 root root   804552 Jul 26 12:46 abi-3.2.0-52-generic-pae
-rw-r--r--  1 root root   147379 Jul 27  2012 config-3.2.0-29-generic-pae
-rw-r--r--  1 root root   147435 Sep 26  2012 config-3.2.0-32-generic-pae
-rw-r--r--  1 root root   147435 Oct 18  2012 config-3.2.0-33-generic-pae
-rw-r--r--  1 root root   147452 Dec  5  2012 config-3.2.0-35-generic-pae
-rw-r--r--  1 root root   147452 Jan 24  2013 config-3.2.0-37-generic-pae
-rw-r--r--  1 root root   147435 Feb 19  2013 config-3.2.0-38-generic-pae
-rw-r--r--  1 root root   147435 Feb 27  2013 config-3.2.0-39-generic-pae
-rw-r--r--  1 root root   147533 Mar 25  2013 config-3.2.0-40-generic-pae
-rw-r--r--  1 root root   147569 Apr 25  2013 config-3.2.0-41-generic-pae
-rw-r--r--  1 root root   147569 May 16 14:59 config-3.2.0-44-generic-pae
-rw-r--r--  1 root root   147569 Jun  6 16:07 config-3.2.0-48-generic-pae
-rw-r--r--  1 root root   147569 Jun 18 14:02 config-3.2.0-49-generic-pae
-rw-r--r--  1 root root   147576 Jul 24 16:44 config-3.2.0-51-generic-pae
-rw-r--r--  1 root root   147576 Jul 26 12:46 config-3.2.0-52-generic-pae
drwxr-xr-x  3 root root    12288 Aug 18 10:13 grub
-rw-r--r--  1 root root 20084589 Nov  5  2012 initrd.img-3.2.0-29-generic-pae
-rw-r--r--  1 root root 20090172 Nov  5  2012 initrd.img-3.2.0-32-generic-pae
-rw-r--r--  1 root root 20091084 Nov 17  2012 initrd.img-3.2.0-33-generic-pae
-rw-r--r--  1 root root 20090131 Feb  9  2013 initrd.img-3.2.0-35-generic-pae
-rw-r--r--  1 root root 20106085 Feb  9  2013 initrd.img-3.2.0-37-generic-pae
-rw-r--r--  1 root root 20096711 Mar  4  2013 initrd.img-3.2.0-38-generic-pae
-rw-r--r--  1 root root 20095665 Mar 28  2013 initrd.img-3.2.0-39-generic-pae
-rw-r--r--  1 root root 20138116 Apr 16  2013 initrd.img-3.2.0-40-generic-pae
-rw-r--r--  1 root root 20143217 May 10  2013 initrd.img-3.2.0-41-generic-pae
-rw-r--r--  1 root root 20143954 Jun 18 19:30 initrd.img-3.2.0-44-generic-pae
-rw-r--r--  1 root root 20144328 Jun 18 19:42 initrd.img-3.2.0-48-generic-pae
-rw-r--r--  1 root root 20145319 Jul  5 21:00 initrd.img-3.2.0-49-generic-pae
-rw-r--r--  1 root root 20144815 Aug 24 18:38 initrd.img-3.2.0-51-generic-pae
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2311324 Jul 27  2012 System.map-3.2.0-29-generic-pae
-rw-------  1 root root  2313078 Sep 26  2012 System.map-3.2.0-32-generic-pae
-rw-------  1 root root  2313292 Oct 18  2012 System.map-3.2.0-33-generic-pae
-rw-------  1 root root  2314162 Dec  5  2012 System.map-3.2.0-35-generic-pae
-rw-------  1 root root  2314545 Jan 24  2013 System.map-3.2.0-37-generic-pae
-rw-------  1 root root  2315698 Feb 19  2013 System.map-3.2.0-38-generic-pae
-rw-------  1 root root  2316522 Feb 27  2013 System.map-3.2.0-39-generic-pae
-rw-------  1 root root  2318451 Mar 25  2013 System.map-3.2.0-40-generic-pae
-rw-------  1 root root  2318965 Apr 25  2013 System.map-3.2.0-41-generic-pae
-rw-------  1 root root  2319343 May 16 14:59 System.map-3.2.0-44-generic-pae
-rw-------  1 root root  2320444 Jun  6 16:07 System.map-3.2.0-48-generic-pae
-rw-------  1 root root  2320444 Jun 18 14:02 System.map-3.2.0-49-generic-pae
-rw-------  1 root root  2320656 Jul 24 16:44 System.map-3.2.0-51-generic-pae
-rw-------  1 root root  2320656 Jul 26 12:46 System.map-3.2.0-52-generic-pae
-rw-r--r--  1 root root  5010176 Aug 17  2012 vmlinuz-3.2.0-29-generic-pae
-rw-------  1 root root  5014912 Sep 26  2012 vmlinuz-3.2.0-32-generic-pae
-rw-------  1 root root  5015328 Oct 18  2012 vmlinuz-3.2.0-33-generic-pae
-rw-------  1 root root  5017984 Dec  5  2012 vmlinuz-3.2.0-35-generic-pae
-rw-------  1 root root  5018144 Jan 24  2013 vmlinuz-3.2.0-37-generic-pae
-rw-------  1 root root  5018240 Feb 19  2013 vmlinuz-3.2.0-38-generic-pae
-rw-------  1 root root  5019712 Feb 27  2013 vmlinuz-3.2.0-39-generic-pae
-rw-------  1 root root  5022272 Mar 25  2013 vmlinuz-3.2.0-40-generic-pae
-rw-------  1 root root  5023424 Apr 25  2013 vmlinuz-3.2.0-41-generic-pae
-rw-------  1 root root  5024224 May 16 14:59 vmlinuz-3.2.0-44-generic-pae
-rw-------  1 root root  5026432 Jun  6 16:07 vmlinuz-3.2.0-48-generic-pae
-rw-------  1 root root  5026432 Jun 18 14:02 vmlinuz-3.2.0-49-generic-pae
-rw-------  1 root root  5028224 Jul 24 16:44 vmlinuz-3.2.0-51-generic-pae
-rw-------  1 root root  5028032 Jul 26 12:46 vmlinuz-3.2.0-52-generic-pae

```

---

### Post by lddimov on 2013-11-14
I tried to be proactive and tried the 3 lines of code listed here: [http://ubuntuforums.org/showthread.php?t=1435818#3](http://ubuntuforums.org/showthread.php?t=1435818#3) as well as the code here: [http://ubuntuforums.org/showthread.php?t=1435818#5](http://ubuntuforums.org/showthread.php?t=1435818#5) but couldn't remove any of the kernels:

```

user@user-Latitude-D810:~$ sudo dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done
[sudo] password for user: 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

user@user-Latitude-D810:~$ sudo apt-get remove linux-image-3.2.0-29-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-52-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2013-11-14
lddimov; Well. well ....

Let's try this approach to get some head room. Maybe "dpkg" will be able to operate as it is a lower level tool.

Firstly, see what kernel version you are running - under no circumstance remove this kernel !
Terminal code:
```

uname -r

```
With the above version in mind - so it is not in the list below - run these terminal commands:
Terminal code:
```

sudo dpkg -P linux-image-3.2.0-{29,32,35,37,38,39,40,41,44,48}-generic-pae
sudo dpkg -P linux-headers-3.2.0-{29,32,35,37,38,39,40,41,44,48}-generic-pae

```
We are trying to remove these kernels and related header files at one fell swoop.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by lddimov on 2013-11-14
That worked Bashing-om, thanks! Is there a way to automatically delete the old kernels and headers once they get updated?

---

### Post by lddimov on 2013-11-14
I spoke too early... This did remove the kernels and headers, but I still can't update... 
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Details:
The following packages have unmet dependencies:
linux-headers-generic-pae: Depends: linux-headers-3.2.0-52-generic-pae but it is not installed

And I definitely have not removed that particulat header.

And here is the output from sudo apt-get install -f

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libfile-find-rule-perl libnumber-compare-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 152 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,980 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-52-generic-pae; however:
  Package linux-headers-3.2.0-52-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.52.62); however:
  Version of linux-image-generic-pae on system is 3.2.0.56.66.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.52.62); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2013-11-14
lddimov; Great !

Let's make sure all is ship shape at this time; rerun terminal codes. and post back the output for me to confirm:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

And nope, the system will not second guess you and will not remove a kernel automatically. The system has no way to know if/when you may want to use one of those old kernels. That is left for the system administrator to preform along with the light general house cleaning that is performed on occasion.

Now it is a lot easier to remove those old kernels in later 'buntu versions - apt-get has been improved some more ! But does not apply to the 3.2 series kernels.

--------------------------
Just caught your update, still with kernel problems, try this:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get update
sudo apt-get install linux-generic-pae
sudo apt-get upgrade

```
Then if all runs good, do the above checks.

[INDENT][INDENT]still, just a thing
[/INDENT][/INDENT]

---

### Post by lddimov on 2013-11-15
This removed linux-generic-pae, but I still could not update after that. Among the erros I was getitng was
```

user@user-Latitude-D810:~$ sudo apt-get install linux-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.56.66) but 3.2.0.52.62 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-52-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@user-Latitude-D810:~$ sudo apt-get -f install
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-52-generic-pae; however:
  Package linux-headers-3.2.0-52-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                        Errors were encountered while processing:
 linux-headers-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so I run:
```

user@user-Latitude-D810:~$ sudo apt-get install linux-headers-3.2.0-52-generic-pae

```
and that fixed it! Now I can update again! Thanks for the help!

---

### Post by Bashing-om on 2013-11-15
lddimov; Great, you do good work !

now to see if any thing is left to clean up; Terminal codes:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-11-16
If the problem is solved please mark the thread so.

---

### Post by lddimov on 2013-11-17
Thanks Bashing-om! There were a few still left (other than the current kernel and headers), so I deleter them. Here is the output I got after that:

```
dpkg -l | grep linux-image-
ii  linux-image-3.2.0-56-generic-pae       3.2.0-56.86                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.56.66                             Generic Linux kernel image

dpkg -l | grep linux-headers-
ii  linux-headers-3.2.0-56                 3.2.0-56.86                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic-pae     3.2.0-56.86                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae              3.2.0.56.66                             Generic Linux kernel headers

```

The current version is 3.2.0-56. There are no other kernels and headers I can delete, are there?

---

### Post by Bashing-om on 2013-11-19
lddimov; Nope,

Looks good to me, all done.
Just remember in the general house cleaning routines to also remove the old unused kernels.

As we have resolution, at this time mark this thread as solved - aides others seeking the solution and helps keep the forum tidy.

'till our next adventure,
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

