---
title: "linux-image-3.5.0-36-generic problem or grub problem on apt-get install?"
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by helio3 on 2015-06-23
I'm just trying to use apt-get to install python-pip, or ANY other software (Ubuntu 14.04.2 LTS) and the returner error message is the following:

> sudo apt-get install python-pip

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-4.8-base:i386 libcairo-gobject2:i386 libcairo2:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libelf1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libllvm3.4:i386
  libpciaccess0:i386 libpixman-1-0:i386 libstdc++6:i386 libx11-xcb1:i386
  libxatracker1 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxshmfence1:i386 libxxf86vm1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-colorama python-distlib python-html5lib python-setuptools
  python-wheel
Suggested packages:
  python-genshi
Recommended packages:
  python-dev-all
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic
The following NEW packages will be installed:
  python-colorama python-distlib python-html5lib python-pip python-setuptools
  python-wheel
0 upgraded, 6 newly installed, 1 to remove and 4 not upgraded.
124 not fully installed or removed.
Need to get 0 B/589 kB of archives.
After this operation, 154 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 399644 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At this point I have no idea if this is a kernell problem or a gru problem...

Does anyone have any hint on how/where to start solving this issue?? 

In advance, I'm posting some outputs that may be relevant....:

> dpkg -l | grep linux-image
```

ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-55-generic                         3.13.0-55.94                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.5.0-36-generic                          3.5.0-36.57~precise1                                   amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-60-generic                          3.5.0-60.87~precise1                                   amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-61-generic                          3.5.0-61.90                                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.55.62                                           amd64        Generic Linux kernel image
iU  linux-image-generic-lts-quantal                       3.13.0.55.62                                           amd64        Generic Linux kernel image

```

> dpkg -l | grep linux-header
```

ii  linux-headers-3.13.0-52                               3.13.0-52.86                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.5.0-60                                3.5.0-60.87~precise1                                   all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-60-generic                        3.5.0-60.87~precise1                                   amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-3.5.0-61                                3.5.0-61.90                                            all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-61-generic                        3.5.0-61.90                                            amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
iU  linux-headers-generic                                 3.13.0.55.62                                           amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-quantal                     3.13.0.55.62                                           amd64        Generic Linux kernel headers

```

Any help is appreciated! Thanks in advance for your patience...

Cheers

---

### Post by sudodus on 2015-06-23
Welcome to the Ubuntu Forums :-)

In Ubuntu 14.04 LTS you use the kernel linux-image-3.13 (or newer). linux-image-3.5 is left from a previous version of Ubuntu. I guess you have upgraded the system, and I suggest that you try to remove those old kernel files.

But in order to avoid problems (maybe with some old program package, that might need the old kernel), I suggest that you ***backup*** your current system or at least all your important personal data files.

After that you can try
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

and if that does not remove all linux-image-3.5.0-36 files you can try explicitly with
```
sudo apt-get remove linux-image-3.5.0-36-generic
```
I think you should also remove the other 3.5 kernel files
```
sudo apt-get remove linux-image-3.5.0-60-generic
sudo apt-get remove linux-image-3.5.0-61-generic
```

and after that you can run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

There is also this list of commands, originally posted by *oldfred:*
```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update
```


Come back if there are still problems to install new program packages!

---

### Post by ubfan1 on 2015-06-23
I'd suggest using "apt-get purge" instead of remove (or a --purge switch with remove).  That gets rid of all the "configuration" files too, which you don't need, and can take up considerable space (in /usr/src for instance).

---

### Post by helio3 on 2015-06-23
Thanks for the warm welcome sudodus and for the suggestion both sudodus and ubfan1. Sorry for the delay in answering you. Had a long working day today...

And yes, sudodus...I did upgrade my system from 12.04...

Tried the suggestions above and actually got about the same error message as before...

> sudo apt-get autoremove" (with or without --purge)

> 
 Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gcc-4.8-base:i386 libcairo-gobject2:i386 libcairo2:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libelf1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libllvm3.4:i386
  libpciaccess0:i386 libpixman-1-0:i386 libstdc++6:i386 libx11-xcb1:i386
  libxatracker1 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxshmfence1:i386 libxxf86vm1:i386 linux-image-3.5.0-36-generic
0 upgraded, 0 newly installed, 27 to remove and 6 not upgraded.
124 not fully installed or removed.
After this operation, 225 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 399644 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.4) ...
Removing libllvm3.4:i386 (1:3.4-1ubuntu3) ...
Removing libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcairo2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libelf1:i386 (0.158-0ubuntu5.2) ...
Removing libglu1-mesa:i386 (9.0.0-2) ...
Removing libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4) ...
Removing libglapi-mesa:i386 (10.1.3-0ubuntu0.4) ...
Removing libpciaccess0:i386 (0.13.2-1) ...
Removing libpixman-1-0:i386 (0.30.2-2ubuntu1) ...
Removing libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Removing libxatracker1:amd64 (9.2.0~git20131002+9.2.2eb55601-0ubuntu0sarvatt~precise) ...
Removing libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-glx0:i386 (1.10-2ubuntu1) ...
Removing libxcb-present0:i386 (1.10-2ubuntu1) ...
Removing libxcb-render0:i386 (1.10-2ubuntu1) ...
Removing libxcb-shm0:i386 (1.10-2ubuntu1) ...
Removing libxcb-sync1:i386 (1.10-2ubuntu1) ...
Removing libxshmfence1:i386 (1.1-2) ...
Removing libxxf86vm1:i386 (1:1.1.3-1) ...
Removing libstdc++6:i386 (4.8.4-2ubuntu1~14.04) ...
Removing gcc-4.8-base:i386 (4.8.4-2ubuntu1~14.04) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



 

> sudo apt-get remove linux-image-3.5.0-36-generic returned:

> 
 Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-4.8-base:i386 libcairo-gobject2:i386 libcairo2:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libelf1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libllvm3.4:i386
  libpciaccess0:i386 libpixman-1-0:i386 libstdc++6:i386 libx11-xcb1:i386
  libxatracker1 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxshmfence1:i386 libxxf86vm1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
124 not fully installed or removed.
After this operation, 157 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 399644 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)




I tried to upgrade anyway, and of course, more of the same happened...:(

Any other ideas..?...Anything else I could try..??

Thanks again!

Cheers!

---

### Post by ubfan1 on 2015-06-23
Seems the package manager is miffed that a file you are asking it to remove has already been deleted.;)  It's not exactly clear which file is causing the problem, but start with ls /var/lib/dpkg/info/linux-image*   and see if the linux-image-3.5.0-36-generic.postrm file is present.  If not, just make an empty one, and set the execute bits like the other linux-image...postrm files.  Try the purge again.  If you get any specific complaints of missing files before the failure, just create empty ones (usual places are in /boot or /usr/src/...  Eventually, it should succeed in getting through the purge.

---

### Post by helio3 on 2015-06-23
Thanks again ubfan1...but unfortunately, no success...:(

[COLOR=#000000] linux-image-3.5.0-36-generic.postrm was in there, like other [/COLOR][COLOR=#000000]linux-image*postrm as well...and a[/COLOR]s suggested, I created an empty video.lst file (there was acomplaint...there isn't anymore...), but error related to GRUBE_TIMEOUT grub-probe persist...

> ls -l /var/lib/dpkg/info/linux-image*postrm
> 
-rwxr-xr-x 1 root root 13694 May  4 02:10 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.postrm
-rwxr-xr-x 1 root root 13694 Jun 17 22:04 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.postrm
-rwxr-xr-x 1 root root 13693 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm
-rwxr-xr-x 1 root root 13693 Mar  6 01:35 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.postrm
-rwxr-xr-x 1 root root 13693 Apr 26 08:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.postrm
-rwxr-xr-x 1 root root   391 May  4 02:10 /var/lib/dpkg/info/linux-image-extra-3.13.0-52-generic.postrm
-rwxr-xr-x 1 root root   391 Jun 17 22:04 /var/lib/dpkg/info/linux-image-extra-3.13.0-55-generic.postrm


> ls -l /var/lib/dpkg/info

> 
-rw-r--r-- 1 root root  55754 May 18 22:53 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.list
-rw-r--r-- 1 root root  71663 May  4 02:19 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.md5sums
-rwxr-xr-x 1 root root  39259 May  4 02:10 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.postinst
-rwxr-xr-x 1 root root  13694 May  4 02:10 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.postrm
-rwxr-xr-x 1 root root  11548 May  4 02:10 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.preinst
-rwxr-xr-x 1 root root  11359 May  4 02:10 /var/lib/dpkg/info/linux-image-3.13.0-52-generic.prerm
-rw-r--r-- 1 root root  55990 Jun 20 13:42 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.list
-rw-r--r-- 1 root root  71948 Jun 17 22:14 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.md5sums
-rwxr-xr-x 1 root root  39259 Jun 17 22:04 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.postinst
-rwxr-xr-x 1 root root  13694 Jun 17 22:04 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.postrm
-rwxr-xr-x 1 root root  11548 Jun 17 22:04 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.preinst
-rwxr-xr-x 1 root root  11359 Jun 17 22:04 /var/lib/dpkg/info/linux-image-3.13.0-55-generic.prerm
-rw-r--r-- 1 root root     48 Jun 23 23:34 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.list
-rw-r--r-- 1 root root 359764 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.md5sums
-rwxr-xr-x 1 root root  38643 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postinst
-rwxr-xr-x 1 root root  13693 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm
-rwxr-xr-x 1 root root  11547 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.preinst
-rwxr-xr-x 1 root root  11358 Jun 20  2013 /var/lib/dpkg/info/linux-image-3.5.0-36-generic.prerm
-rw-r--r-- 1 root root 283434 Apr 30 03:14 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.list
-rw-r--r-- 1 root root 359873 Mar  6 01:37 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.md5sums
-rwxr-xr-x 1 root root  38643 Mar  6 01:35 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.postinst
-rwxr-xr-x 1 root root  13693 Mar  6 01:35 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.postrm
-rwxr-xr-x 1 root root  11547 Mar  6 01:35 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.preinst
-rwxr-xr-x 1 root root  11358 Mar  6 01:35 /var/lib/dpkg/info/linux-image-3.5.0-60-generic.prerm
-rw-r--r-- 1 root root 283434 May  1 04:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.list
-rw-r--r-- 1 root root 359873 Apr 26 08:45 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.md5sums
-rwxr-xr-x 1 root root  38643 Apr 26 08:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.postinst
-rwxr-xr-x 1 root root  13693 Apr 26 08:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.postrm
-rwxr-xr-x 1 root root  11547 Apr 26 08:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.preinst
-rwxr-xr-x 1 root root  11358 Apr 26 08:43 /var/lib/dpkg/info/linux-image-3.5.0-61-generic.prerm
-rw-r--r-- 1 root root 279454 May 18 23:02 /var/lib/dpkg/info/linux-image-extra-3.13.0-52-generic.list
-rw-r--r-- 1 root root 338165 May  4 02:19 /var/lib/dpkg/info/linux-image-extra-3.13.0-52-generic.md5sums
-rwxr-xr-x 1 root root    391 May  4 02:10 /var/lib/dpkg/info/linux-image-extra-3.13.0-52-generic.postinst
-rwxr-xr-x 1 root root    391 May  4 02:10 /var/lib/dpkg/info/linux-image-extra-3.13.0-52-generic.postrm
-rw-r--r-- 1 root root 279268 Jun 20 13:44 /var/lib/dpkg/info/linux-image-extra-3.13.0-55-generic.list
-rw-r--r-- 1 root root 337880 Jun 17 22:14 /var/lib/dpkg/info/linux-image-extra-3.13.0-55-generic.md5sums
-rwxr-xr-x 1 root root    391 Jun 17 22:04 /var/lib/dpkg/info/linux-image-extra-3.13.0-55-generic.postinst
-rwxr-xr-x 1 root root    391 Jun 17 22:04 /var/lib/dpkg/info/linux-image-extra-3.13.0-55-generic.postrm
-rw-r--r-- 1 root root    162 Jun 20 13:44 /var/lib/dpkg/info/linux-image-generic.list
-rw-r--r-- 1 root root    198 Jun 20 13:44 /var/lib/dpkg/info/linux-image-generic-lts-quantal.list
-rw-r--r-- 1 root root     90 Jun 14 15:40 /var/lib/dpkg/info/linux-image-generic-lts-quantal.md5sums
-rw-r--r-- 1 root root    159 Jun 14 15:42 /var/lib/dpkg/info/linux-image-generic.md5sums


> sudo apt-get autoremove --purge

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
124 not fully installed or removed.
After this operation, 157 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 399560 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)




Thanks again!

Cheers

---

### Post by Bucky Ball on 2015-06-24
Welcome. Open a terminal and open the file:

```
sudo nano /etc/apt/sources.list
```

Look for anything that ends in or mentions 12.04, i.e. contains 'Precise' in the repo name and not 'Trusty'. Disable them but putting a hashtag (#) at the beginning of the line. Update. Any issue?

If not, you can completely remove the 3.5 kernels as suggested. You are not booting from a 12.04 kernel? What is the result of:

```
uname -a
```

---

### Post by helio3 on 2015-06-24
Thanks for the input Bucky Balls!

All 12.04* or *Precise* in /etc/apt/sources.list were already disabled

There was no problem at all in updating, but in upgrading...

> sudo apt-get upgrade

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic
The following packages have been kept back:
  gnuplot-nox gnuplot-x11
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin google-chrome-stable patch
4 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
124 not fully installed or removed.
Need to get 58.6 MB of archives.
After this operation, 157 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates/main patch amd64 2.7.1-4ubuntu2.3 [86.4 kB]
Get:2 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main google-chrome-stable amd64 43.0.2357.130-1 [48.3 MB]
Get:3 [http://archive.canonical.com/](http://archive.canonical.com/) trusty/partner adobe-flash-properties-gtk amd64 1:20150623.1-0trusty1 [113 kB]
Get:4 [http://archive.canonical.com/](http://archive.canonical.com/) trusty/partner adobe-flashplugin amd64 1:20150623.1-0trusty1 [10.0 MB]
Fetched 58.6 MB in 57s (1,017 kB/s)                                            
(Reading database ... 399560 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


> uname -a
> 
Linux hesicata-Inspiron-3647 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux



Trying to remove, results:
> sudo apt-get remove linux-image-3.5.0-36-generic
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
124 not fully installed or removed.
After this operation, 157 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 399560 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic (3.5.0-36.57~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.5.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


...

---

### Post by Bucky Ball on 2015-06-24
Yep, as I suspected. You are booting a 3.5 kernel so you are, effectively, running 12.04. 

```
Linux hesicata-Inspiron-3647 ***3.5.0-61-generic*** #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 
```

Boot into one of the 14.04 kernels (which will start with 3.13) and try again. This may not fix your problem - you should still be able to remove that kernel in 12.04 as you're not booted into it - but it will get us on the right track and provide some clarity. You should be doing this from 14.04 and we are not sure what's going on there if you are booting into a 12.04 kernel still. (By choice?)

Are you absolutely positive the upgrade worked? When you boot, do you get a screen with a kernel list to choose from? If not, try hitting the shift key just after boot.

---

### Post by helio3 on 2015-06-24
Thanks again Bucky Ball!

Well, I thought the upgrade had worked...at least until I saw your last post...I just did the regular system upgrade from 12.04 to 14.04...I guess(ed)...

Does it mean I'm using a 12.04 kernel under 14.04 LTS..? :confused:

> lsb_release -a
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

There is no kernel list to choose from...hitting shift after reboot didn't help either...

Hope there is a solution for the issue...other than the naive one I'm thinking. There are a lot of work-related installed things around here. It'd be a work for a week or more...

Cheers

---

### Post by Bucky Ball on 2015-06-24
Don't give up yet. Open this file:

```
sudo nano /etc/default/grub
```

Make these lines look like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Then:

```
sudo update-grub
```

Reboot. You should get a list of kernels. Choose the first 3.13 kernel on the list. Once (if) you're in, run 'uname -a' again. What do you get now? If you're running the 3.13, try the updates/upgrades again. 

PS: Please use code tags for terminal output rather than quote ones. Thanks. (Just replace [quote] with [code] in the tag basically or see the last link in my signature).

---

### Post by helio3 on 2015-06-24
Thanks Bucky Ball! Sorry for the bad use of tools in the forum. It's always time to learn! :). Hope it works now...

grub file was exactly as you described...I had already commented the line 
```
#GRUB_HIDDEN_TIMEOUT=0
```

```
sudo update-grub
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
```

Thanks!

---

### Post by Bucky Ball on 2015-06-24
You're missing a hyphen. 

```
sudo update-grub
```

... after making the changes.

---

### Post by helio3 on 2015-06-24
Sorry Bucky Ball!
The output is correct. Because I edited the post I mistyped the command...reedited again...
Thanks for the patience.

---

### Post by helio3 on 2015-06-24
Just tried again...no typo errors now...:

```

~$ sudo update-grub
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.

```

Any suggestion(s)?

Thanks in advance!

Cheers

---

### Post by sudodus on 2015-06-26
In cases like this it is often easier and faster to save the personal data (documents, pictures, mailboxes, video-clips etc) and then make a fresh install of the new version.

---

### Post by helio3 on 2015-06-29
Hello everyone! Thank you all for the help and patience. I ended up solving the issue after insisting in searching "a bit more" around forums...here's what I found out/did:

1. found out that GRUB_PREFIX variable wasn't defined anywhere. I read some saying that this is a common bug after the upgrade (that was my case) and that this  line is from an earlier version of grub-common that was removed after grub 2.00...there is some discussion about this here [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1078653](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1078653) ...anyway, I defined it pointing to my grub folder and exported it...:

```

GRUB_PREFIX="/etc/default"
export GRUB_PREFIX

```

2. by running the following debug command and writing the output to a file:

```

~$sudo sh -x /usr/sbin/grub-mkconfig >/dev/null 2>grub-mkconfig.err

```

I found out that there were two 00_header* files in my /etc/grub.d/ folder...(see resumed output below):

```

...
...
+ cat
+ grub_file_is_not_garbage /etc/grub.d/00_header
+ test -f /etc/grub.d/00_header
+ return 0
+ test -x /etc/grub.d/00_header
+ echo
+ echo ### BEGIN /etc/grub.d/00_header ###
+ /etc/grub.d/00_header
+ echo ### END /etc/grub.d/00_header ###
+ grub_file_is_not_garbage /etc/grub.d/00_header.orig
+ test -f /etc/grub.d/00_header.orig
+ return 0
+ test -x /etc/grub.d/00_header.orig
+ echo
+ echo ### BEGIN /etc/grub.d/00_header.orig ###
+ /etc/grub.d/00_header.orig
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.

```

I removed 00_header.orig file and the magic was done! I updated, upgraded and could finally install/re-install packages!! :)

Now I'm having other issues, which are probably not related to this, but they are topic of another thread...

For me, you can consider this thread as solved.

 Once again, thank you all for all the inputs!

Cheers!

---

### Post by sudodus on 2015-06-29
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

