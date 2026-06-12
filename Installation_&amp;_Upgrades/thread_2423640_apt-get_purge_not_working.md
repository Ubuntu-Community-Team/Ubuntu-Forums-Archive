---
title: "apt-get purge not working"
date: 2019-07-26
forum: Installation &amp; Upgrades
---

### Post by in2survive on 2019-07-26
My /boot is full and I can't free space. Current version 4.4.0-151-generic:
```
user@server:~$ sudo apt-get purge linux-headers-4.4.0-134
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-4.4.0-134-generic : Depends: linux-headers-4.4.0-134 but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-157-generic but it is not going to be installed or
                                linux-image-unsigned-4.4.0-157-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
 linux-modules-extra-4.4.0-154-generic : Depends: linux-image-4.4.0-154-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-154-generic but it is not going to be installed
 linux-modules-extra-4.4.0-157-generic : Depends: linux-image-4.4.0-157-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-157-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@server:~$

```
Same type of error if I try auto-remove:
```
user@server:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.4.0-157-generic but it is not installed or
                                linux-image-unsigned-4.4.0-157-generic but it is not installed
                       Recommends: thermald but it is not installed
 linux-modules-extra-4.4.0-154-generic : Depends: linux-image-4.4.0-154-generic but it is not installed or
                                                  linux-image-unsigned-4.4.0-154-generic but it is not installed
 linux-modules-extra-4.4.0-157-generic : Depends: linux-image-4.4.0-157-generic but it is not installed or
                                                  linux-image-unsigned-4.4.0-157-generic but it is not installed
E: Unmet dependencies. Try using -f.
user@server:~$

```

---

### Post by ajgreeny on 2019-07-26
Can you please show us the output of ```
df -hT
dpkg -l | grep linux
``` which will show us the current situation of space available and the kernels installed.

Once we know the details we can offer you a ***dpkg*** command which will remove packages even when apt will not as ***dpkg*** does not need the headroom space that ***apt*** does.

---

### Post by in2survive on 2019-07-26
Thanks @ajgreeny here you go:
```
user@server64:~$ df -hT
Filesystem                               Type      Size  Used Avail Use% Mounted on
udev                                     devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs                                    tmpfs     797M  9.1M  788M   2% /run
/dev/mapper/server64--vg-root              ext4      238G   58G  169G  26% /
tmpfs                                    tmpfs     3.9G  8.0K  3.9G   1% /dev/shm
tmpfs                                    tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                                    tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                                ext2      472M  471M     0 100% /boot
cgmfs                                    tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs                                    tmpfs     797M     0  797M   0% /run/user/1000
user@server64:~$ dpkg -l | grep linux
ii  console-setup-linux                   1.108ubuntu15.4                            all          Linux specific part of console-setup
ii  libselinux1:amd64                     2.4-3build2                                amd64        SELinux runtime shared libraries
ii  linux-base                            4.5ubuntu1~16.04.1                         all          Linux image base package
ii  linux-firmware                        1.157.21                                   all          Firmware for Linux kernel drivers
iU  linux-generic                         4.4.0.157.165                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-134               4.4.0-134.160                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-134-generic       4.4.0-134.160                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-137               4.4.0-137.163                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-137-generic       4.4.0-137.163                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-141               4.4.0-141.167                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-141-generic       4.4.0-141.167                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-142               4.4.0-142.168                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-142-generic       4.4.0-142.168                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-143               4.4.0-143.169                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-143-generic       4.4.0-143.169                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-145               4.4.0-145.171                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-145-generic       4.4.0-145.171                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-148               4.4.0-148.174                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-148-generic       4.4.0-148.174                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-150               4.4.0-150.176                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-150-generic       4.4.0-150.176                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-151               4.4.0-151.178                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-151-generic       4.4.0-151.178                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-154               4.4.0-154.181                              all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-154-generic       4.4.0-154.181                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-157               4.4.0-157.185                              all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-157-generic       4.4.0-157.185                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic                 4.4.0.157.165                              amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-109-generic         4.4.0-109.132                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-112-generic         4.4.0-112.135                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-116-generic         4.4.0-116.140                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-119-generic         4.4.0-119.143                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-121-generic         4.4.0-121.145                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-124-generic         4.4.0-124.148                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-127-generic         4.4.0-127.153                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-128-generic         4.4.0-128.154                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-130-generic         4.4.0-130.156                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-133-generic         4.4.0-133.159                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-134-generic         4.4.0-134.160                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-137-generic         4.4.0-137.163                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-141-generic         4.4.0-141.167                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-142-generic         4.4.0-142.168                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-143-generic         4.4.0-143.169                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-145-generic         4.4.0-145.171                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-148-generic         4.4.0-148.174                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-150-generic         4.4.0-150.176                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-151-generic         4.4.0-151.178                              amd64        Signed kernel image generic
rc  linux-image-4.4.0-62-generic          4.4.0-62.83                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic   4.4.0-109.132                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic   4.4.0-112.135                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-116-generic   4.4.0-116.140                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-119-generic   4.4.0-119.143                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-121-generic   4.4.0-121.145                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-124-generic   4.4.0-124.148                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-127-generic   4.4.0-127.153                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-128-generic   4.4.0-128.154                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-130-generic   4.4.0-130.156                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-133-generic   4.4.0-133.159                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-134-generic   4.4.0-134.160                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-142-generic   4.4.0-142.168                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic    4.4.0-62.83                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                   4.4.0.157.165                              amd64        Generic Linux kernel image
ii  linux-modules-4.4.0-143-generic       4.4.0-143.169                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-145-generic       4.4.0-145.171                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-148-generic       4.4.0-148.174                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-150-generic       4.4.0-150.176                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-151-generic       4.4.0-151.178                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-4.4.0-154-generic       4.4.0-154.181                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-143-generic 4.4.0-143.169                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-145-generic 4.4.0-145.171                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-148-generic 4.4.0-148.174                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-150-generic 4.4.0-150.176                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-151-generic 4.4.0-151.178                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.4.0-154-generic 4.4.0-154.181                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.4.0-157-generic 4.4.0-157.185                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  python-selinux                        2.4-3build2                                amd64        Python bindings to SELinux shared libraries
ii  selinux-policy-default                2:2.20140421-9                             all          Strict and Targeted variants of the SELinux policy
ii  selinux-policy-dev                    2:2.20140421-9                             all          Headers from the SELinux reference policy for building modules
ii  selinux-utils                         2.4-3build2                                amd64        SELinux utility programs
ii  util-linux                            2.27.1-6ubuntu3.6                          amd64        miscellaneous system utilities
user@server64:~$
```

If I try to remove with dpkg, I still have errors:
```

user@server:~$ sudo dpkg -r  linux-image-4.4.0-134-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-134-generic:
 linux-image-extra-4.4.0-134-generic depends on linux-image-4.4.0-134-generic.


dpkg: error processing package linux-image-4.4.0-134-generic (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-134-generic
user@server:~$

```

---

### Post by ubfan1 on 2019-07-26
Try the command with purge and force-depends switches: sduo  dpkg -P -force-depends linux-image-4.4.0-134-generic
For kernels, I get a list of all the packages with the matching numbers (installed or not) with
apt-cache pkgnames |grep 4.4.0-134
Check it for just kernel packages, just in case, then feed the whole group to the purge:
sudo apt-get purge `!!`
Don't type anything between the two commands or the !! last command recall wont work.
If/when you get complaints about "cannot purge, some files are missing" (Ha Ha!), note carefully what file/dir is in the complaint and make it with sudo touch <missingfile>
That should hush those complaints, and let the rest of the package be purged.
There may be switches  to force the removes/purges, but I haven't checked that carefully (maybe force-remove-reinstreq ).

---

### Post by in2survive on 2019-07-26
Awesome!! Thanks a lot, I was really stuck! This did the trick:
```
sudo  dpkg -P --force-depends linux-image-4.4.0-134-generic

```
But when I ran the second command, I ran into troubles:
```
user@server:~$ [COLOR=#000000]apt-cache pkgnames |grep 4.4.0-134
[/COLOR]linux-cloud-tools-4.4.0-134-generic
linux-signed-image-4.4.0-134-generic
linux-headers-4.4.0-134
linux-tools-4.4.0-134-lowlatency
linux-image-extra-4.4.0-134-generic
linux-image-4.4.0-134-lowlatency
linux-tools-4.4.0-134-generic
linux-cloud-tools-4.4.0-134
linux-headers-4.4.0-134-generic
linux-tools-4.4.0-134
linux-signed-image-4.4.0-134-lowlatency
linux-headers-4.4.0-134-lowlatency
linux-image-4.4.0-134-generic
linux-cloud-tools-4.4.0-134-lowlatency

user@server:~$ [COLOR=#000000]sudo apt-get purge `!!`
[/COLOR]sudo apt-get purge `apt-cache pkgnames |grep 4.4.0-134`
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'linux-cloud-tools-4.4.0-134' is not installed, so not removed
Package 'linux-cloud-tools-4.4.0-134-generic' is not installed, so not removed
Package 'linux-cloud-tools-4.4.0-134-lowlatency' is not installed, so not removed
Package 'linux-headers-4.4.0-134-lowlatency' is not installed, so not removed
Package 'linux-image-4.4.0-134-generic' is not installed, so not removed
Package 'linux-image-4.4.0-134-lowlatency' is not installed, so not removed
Package 'linux-signed-image-4.4.0-134-generic' is not installed, so not removed
Package 'linux-signed-image-4.4.0-134-lowlatency' is not installed, so not removed
Package 'linux-tools-4.4.0-134' is not installed, so not removed
Package 'linux-tools-4.4.0-134-generic' is not installed, so not removed
Package 'linux-tools-4.4.0-134-lowlatency' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.4.0-157-generic but it is not going to be installed or
                                linux-image-unsigned-4.4.0-157-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
 linux-modules-extra-4.4.0-154-generic : Depends: linux-image-4.4.0-154-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-154-generic but it is not going to be installed
 linux-modules-extra-4.4.0-157-generic : Depends: linux-image-4.4.0-157-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-157-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

user@server:~$
```

So, I cleaned a few manually, then ran:
```
sudo apt-get -f install
sudo purge-old-kernels --keep 3
```
[FONT=Verdana]
Voila:
[/FONT]```
/dev/sda1                                     482922      198107     259881  44% /boot
```

[FONT=Verdana]
[/FONT]

---

