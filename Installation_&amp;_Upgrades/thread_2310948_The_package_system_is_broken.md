---
title: "The package system is broken"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by glenberg on 2016-01-23
**do a apt-get install -f**

Unpacking linux-image-extra-3.19.0-47-generic (3.19.0-47.53) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-3.19.0-47-generic_3.19.0-47.53_amd64.deb (--unpack):
 unable to create `/lib/modules/3.19.0-47-generic/kernel/drivers/net/usb/kalmia.ko.dpkg-new' (while processing `./lib/modules/3.19.0-47-generic/kernel/drivers/net/usb/kalmia.ko'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-generic_3.19.0.47.46_amd64.deb ...
Unpacking linux-generic (3.19.0.47.46) over (3.19.0.42.41) ...
Preparing to unpack .../linux-image-generic_3.19.0.47.46_amd64.deb ...
Unpacking linux-image-generic (3.19.0.47.46) over (3.19.0.42.41) ...
Selecting previously unselected package linux-headers-3.19.0-47.
Preparing to unpack .../linux-headers-3.19.0-47_3.19.0-47.53_all.deb ...
Unpacking linux-headers-3.19.0-47 (3.19.0-47.53) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.19.0-47_3.19.0-47.53_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.19.0-47/drivers/net/wireless/rtl818x/rtl8187/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.19.0-47/drivers/net/wireless/rtl818x/rtl8187/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.19.0-47-generic.
Preparing to unpack .../linux-headers-3.19.0-47-generic_3.19.0-47.53_amd64.deb ...
Unpacking linux-headers-3.19.0-47-generic (3.19.0-47.53) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.19.0-47-generic_3.19.0-47.53_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.19.0-47-generic/include/config/media/tuner/mt20xx.h.dpkg-new' (while processing `./usr/src/linux-headers-3.19.0-47-generic/include/config/media/tuner/mt20xx.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-generic_3.19.0.47.46_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.47.46) over (3.19.0.42.41) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-3.19.0-47-generic_3.19.0-47.53_amd64.deb
 /var/cache/apt/archives/linux-headers-3.19.0-47_3.19.0-47.53_all.deb
 /var/cache/apt/archives/linux-headers-3.19.0-47-generic_3.19.0-47.53_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.7G     0  1.7G   0% /dev
tmpfs           332M   11M  322M   4% /run
/dev/sdb3        20G   17G  2.5G  88% /
tmpfs           1.7G  196K  1.7G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sdb5       418G   46G  352G  12% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           332M   56K  332M   1% /run/user/1000

**desktop:~$ df -i**
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             421046     554   420492    1% /dev
tmpfs            423826     746   423080    1% /run
/dev/sdb3       1330080 1327655     2425  100% /
tmpfs            423826       7   423819    1% /dev/shm
tmpfs            423826       6   423820    1% /run/lock
tmpfs            423826      17   423809    1% /sys/fs/cgroup
/dev/sdb5      27820032   73992 27746040    1% /home
cgmfs            423826      13   423813    1% /run/cgmanager/fs
tmpfs            423826      32   423794    1% /run/user/1000

---

### Post by glenberg on 2016-01-23
Also got this
 dpkg -l | grep linux-image
rc  linux-image-3.19.0-15-generic               3.19.0-15.15                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic               3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic               3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic               3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic               3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic               3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-23-generic               3.19.0-23.24                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-25-generic               3.19.0-25.26                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic               3.19.0-26.28                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic               3.19.0-28.30                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic               3.19.0-30.34                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic               3.19.0-31.36                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic               3.19.0-32.37                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-33-generic               3.19.0-33.38                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic               3.19.0-37.42                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic               3.19.0-39.44                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-41-generic               3.19.0-41.46                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic               3.19.0-42.48                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-3.19.0-47-generic               3.19.0-47.53                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic         3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-16-generic         3.19.0-16.16                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic         3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic         3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic         3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic         3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-23-generic         3.19.0-23.24                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic         3.19.0-25.26                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic         3.19.0-26.28                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic         3.19.0-28.30                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic         3.19.0-30.34                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic         3.19.0-31.36                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic         3.19.0-32.37                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-33-generic         3.19.0-33.38                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic         3.19.0-37.42                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic         3.19.0-39.44                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-41-generic         3.19.0-41.46                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic         3.19.0-42.48                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic                         3.19.0.47.46                               amd64        Generic Linux kernel image

---

### Post by grahammechanical on 2016-01-23
Which partition is Ubuntu installed on? sdb3? How big is the partition? 20GB? 

> /dev/sdb3        20G   17G  2.5G  88% /

sdb3 is 88% used. You need to remove most of the old kernels. To find the present kernel run

```
uname -a
```

Make a note of the kernel number. Then use the Grub menu Advanced options for Ubuntu to load into the first previous kernel and run uname -a again and note the number of the kernel. Having proved that those two kernels work you can remove most of the others.

Or increase the size of sdb3. That would be another way to solve this problem.

You can also run Advanced options for Ubuntu and select a option with recovery mode and at the recovery menu select Clean - try to make free space. That may make enough free space to solve this problem temporarily. But you do need to remove most of those old kernels or increase the size of the partition.

Regards.

---

### Post by glenberg on 2016-01-23
~$ uname -a
Linux chris-desktop 3.19.0-42-generic #48-Ubuntu SMP Thu Dec 17 22:54:45 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ajgreeny on 2016-01-23
Your problem is that you have run out of inodes on sda3, 
```
desktop:~$ df -i
Filesystem Inodes IUsed IFree IUse% Mounted on
udev 421046 554 420492 1% /dev
tmpfs 423826 746 423080 1% /run
[COLOR="#FF0000"]/dev/sdb3 1330080 1327655 2425 100% /[/COLOR]
tmpfs 423826 7 423819 1% /dev/shm
tmpfs 423826 6 423820 1% /run/lock
tmpfs 423826 17 423809 1% /sys/fs/cgroup
/dev/sdb5 27820032 73992 27746040 1% /home
cgmfs 423826 13 423813 1% /run/cgmanager/fs
tmpfs 423826 32 423794 1% /run/user/1000
```
and as far as I'm aware there is no simple way to free inodes by removing files or folders from the partition short of reformatting.

However, I have just searched for a possible answer and came across this page [http://askubuntu.com/questions/231585/running-out-of-inodes](http://askubuntu.com/questions/231585/running-out-of-inodes) which may give you something to investigate further and if you can find any folder with millions of very small files it looks as if you may be able to free some inodes.

Totally unexpected to me and I will be very interested to see if you can get it to work at all.

Good luck!

---

### Post by matt_symes on 2016-01-23
Hi

I would suggest removing any old linux header packages you have installed. They're full a many small files.

Kind regards

---

### Post by glenberg on 2016-01-29
Removed linux headers and then did the update then I upgraded to 15.10 thanks evertyone

---

