---
title: "can't remove not used kernel files and setup anything new"
date: 2018-07-07
forum: Installation &amp; Upgrades
---

### Post by vfotop1 on 2018-07-07
This is really very embarassing for me,never had to create a thread until now as always reading threads from this forum solved my problems. However this time I can't find a solution so i'm asking for your help. I have reads tens of threads about systems stuck with kernels that can't be removed but none of the solutions provided seems to solve my case.
My server is running on a 4.4.0-87-generic kernel...however when I try to upgrade or even add a new package, all are stacked because old packages can't be removed. Especially
 ```
Errors were encountered while processing:
 linux-image-extra-4.4.0-101-generic
 linux-image-extra-4.4.0-103-generic
 linux-image-extra-4.4.0-104-generic
 linux-image-extra-4.4.0-109-generic
 linux-image-extra-4.4.0-112-generic
 linux-image-extra-4.4.0-116-generic
 linux-image-extra-4.4.0-119-generic
 linux-image-extra-4.4.0-121-generic
 linux-image-extra-4.4.0-124-generic
 linux-image-extra-4.4.0-127-generic
 linux-image-extra-4.4.0-128-generic
 linux-image-extra-4.4.0-96-generic
 linux-image-extra-4.4.0-97-generic
 linux-image-extra-4.4.0-98-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Trying to do apt install -f, various purge methods with dpkg as well, manually remove files as proposed to other threads here, reinstall first, but in vain. An output of errors looks like this:
```
Removing linux-image-extra-4.4.0-96-generic (4.4.0-96.119) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-96-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-96-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_7Gs0WJ/lib/modules/4.4.0-96-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_7Gs0WJ/lib/modules/4.4.0-96-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Generating grub configuration file ...
grub-probe: error: disk `mduuid/a41897fab803fd1759180dfca667926e,1' not found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-96-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
```
Any help would be gladly appreciated!
my ls -la /boot/ output, looks like this:
```
ls -la /boot/
total 172732
drwxr-xr-x  3 root root     4096 Jul  7 14:09 .
drwxr-xr-x 23 root root     4096 Jul  5 10:50 ..
-rw-r--r--  1 root root  1251634 Jun 14 16:24 abi-4.4.0-130-generic
-rw-r--r--  1 root root  1246670 Jul 18  2017 abi-4.4.0-87-generic
-rw-r--r--  1 root root   190566 Jun 14 16:24 config-4.4.0-130-generic
-rw-r--r--  1 root root   190356 Jul 18  2017 config-4.4.0-87-generic
drwxr-xr-x  5 root root     4096 Jul  7 14:09 grub
-rw-r--r--  1 root root  8138167 Jul  7 14:07 initrd.img-4.4.0-101-generic
-rw-r--r--  1 root root  8138511 Jul  7 14:07 initrd.img-4.4.0-103-generic
-rw-r--r--  1 root root  8138511 Jul  7 14:07 initrd.img-4.4.0-104-generic
-rw-r--r--  1 root root  8138128 Jul  7 14:07 initrd.img-4.4.0-109-generic
-rw-r--r--  1 root root  8138130 Jul  7 14:08 initrd.img-4.4.0-112-generic
-rw-r--r--  1 root root  8138517 Jul  7 14:08 initrd.img-4.4.0-116-generic
-rw-r--r--  1 root root  8138239 Jul  7 14:08 initrd.img-4.4.0-119-generic
-rw-r--r--  1 root root  8138233 Jul  7 14:08 initrd.img-4.4.0-121-generic
-rw-r--r--  1 root root  8138253 Jul  7 14:08 initrd.img-4.4.0-124-generic
-rw-r--r--  1 root root  8138263 Jul  7 14:08 initrd.img-4.4.0-127-generic
-rw-r--r--  1 root root  8138259 Jul  7 14:08 initrd.img-4.4.0-128-generic
-rw-r--r--  1 root root 37979238 May 19 06:53 initrd.img-4.4.0-87-generic
-rw-r--r--  1 root root  8138271 Jul  7 14:09 initrd.img-4.4.0-96-generic
-rw-r--r--  1 root root  8138315 Jul  7 14:09 initrd.img-4.4.0-97-generic
-rw-r--r--  1 root root  8138306 Jul  7 14:09 initrd.img-4.4.0-98-generic
-rw-r--r--  1 root root      255 Jun 14 16:24 retpoline-4.4.0-130-generic
-rw-------  1 root root  3900257 Jun 14 16:24 System.map-4.4.0-130-generic
-rw-------  1 root root  3884173 Jul 18  2017 System.map-4.4.0-87-generic
-rw-------  1 root root  7156160 Jun 14 16:24 vmlinuz-4.4.0-130-generic
-rw-------  1 root root  7095888 Jul 18  2017 vmlinuz-4.4.0-87-generic

```

dpkg shows the following about kernels
```
dpkg -l | grep 'linux-*'
ii  console-setup-linux                 1.108ubuntu15.3                                          all          Linux specific part of console-setup
ii  libselinux1:amd64                   2.4-3build2                                              amd64        SELinux runtime shared libraries
ii  linux-base                          4.5ubuntu1~16.04.1                                       all          Linux image base package
ii  linux-firmware                      1.157.18                                                 all          Firmware for Linux kernel drivers
iU  linux-generic                       4.4.0.130.136                                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-130             4.4.0-130.156                                            all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-130-generic     4.4.0-130.156                                            amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-87              4.4.0-87.110                                             all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-87-generic      4.4.0-87.110                                             amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic               4.4.0.130.136                                            amd64        Generic Linux kernel headers
iF  linux-image-4.4.0-130-generic       4.4.0-130.156                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-87-generic        4.4.0-87.110                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-101-generic 4.4.0-101.124                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-103-generic 4.4.0-103.126                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-104-generic 4.4.0-104.127                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-109-generic 4.4.0-109.132                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-112-generic 4.4.0-112.135                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-116-generic 4.4.0-116.140                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-119-generic 4.4.0-119.143                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-121-generic 4.4.0-121.145                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-124-generic 4.4.0-124.148                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-127-generic 4.4.0-127.153                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-128-generic 4.4.0-128.154                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-130-generic 4.4.0-130.156                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-87-generic  4.4.0-87.110                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-96-generic  4.4.0-96.119                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-97-generic  4.4.0-97.120                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-98-generic  4.4.0-98.121                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                 4.4.0.130.136                                            amd64        Generic Linux kernel image
ii  util-linux                          2.27.1-6ubuntu3.3                                        amd64        miscellaneous system utilities
```

---

### Post by TheFu on 2018-07-07
Everyone need help some times. Often, it is just another pair of eyes.

Thanks for using code tags.  Helpful, but if you could edit and show the exact command run before the output, that would be useful too.  I'd rather not guess.

Don't think I can help except to say a few things for the future.
a) never manually remove files that are installed by a package. NEVER.
b) it is seldom a good idea to remove packages using dpkg directly, unless those specific packages were manually installed that way.
c) avoid installing .deb files directly. Usually, in 3-6 months, there will be dependency issues and you'll end up in "APT hell". Stick with the official repos and if those aren't working, go to trusted PPAs from reputable sources.
d) Always check there is sufficient storage.  **df -h** and **df -i** btrfs lies, so if you are using that file system, figure out how to get the truth.

I'd start by running 
* df -h
* df -i
* sudo apt update
* sudo apt upgrade
and fix any errors around those.  If there aren't any issues, we can move on. Please show your work, but we don't need to see everything for the "update", just the first 10 and last 10 lines, and any errors. Same for the "upgrade", first 10, last 10, any interesting errors.

---

### Post by ubfan1 on 2018-07-07
There are many "/boot full" problems at askubuntu, If really all else fails, see [https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367](https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367) for manually zeroing out some unwanted files to produce enough space to finish the latest install.  You apparently are running ...87, the oldest, since I don't see any other complete install.

---

### Post by vfotop1 on 2018-07-09
> **TheFu said:**
> Everyone need help some times. Often, it is just another pair of eyes.

...........

I'd start by running 
* df -h
* df -i
* sudo apt update
* sudo apt upgrade
and fix any errors around those.  If there aren't any issues, we can move on. Please show your work, but we don't need to see everything for the "update", just the first 10 and last 10 lines, and any errors. Same for the "upgrade", first 10, last 10, any interesting errors.

I really thank you for the advices. I really avoid (a), (b) and (c) but now it seemed I ran out of choices. Here's the output of the 4...
```
vfotop1@dsmc2:/lib/modules$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           395M   11M  384M   3% /run
/dev/md126p1     73G   57G   13G  83% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           395M     0  395M   0% /run/user/1000

```

```
vfotop1@dsmc2:/lib/modules$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            499941    535  499406    1% /dev
tmpfs           504997    692  504305    1% /run
/dev/md126p1   4825088 138215 4686873    3% /
tmpfs           504997      1  504996    1% /dev/shm
tmpfs           504997      7  504990    1% /run/lock
tmpfs           504997     16  504981    1% /sys/fs/cgroup
tmpfs           504997      4  504993    1% /run/user/1000

```

```
vfotop1@dsmc2:/lib/modules$ sudo apt update
[sudo] password for vfotop1:
Hit:1 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]
Hit:3 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Fetched 323 kB in 1s (206 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
111 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

```
vfotop1@dsmc2:/lib/modules$ sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-extra-4.4.0-101-generic : Depends: linux-image-4.4.0-101-generic but it is not going to be installed
 linux-image-extra-4.4.0-103-generic : Depends: linux-image-4.4.0-103-generic but it is not going to be installed
 linux-image-extra-4.4.0-104-generic : Depends: linux-image-4.4.0-104-generic but it is not going to be installed
---I removed here similar messages for kernels 109-128---
 linux-image-extra-4.4.0-96-generic : Depends: linux-image-4.4.0-96-generic but it is not going to be installed
 linux-image-extra-4.4.0-97-generic : Depends: linux-image-4.4.0-97-generic but it is not going to be installed
 linux-image-extra-4.4.0-98-generic : Depends: linux-image-4.4.0-98-generic but it is not going to be installed
E: Broken packages

```

---

### Post by vfotop1 on 2018-07-09
> **ubfan1 said:**
> There are many "/boot full" problems at askubuntu, If really all else fails, see [https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367](https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367) for manually zeroing out some unwanted files to produce enough space to finish the latest install.  You apparently are running ...87, the oldest, since I don't see any other complete install.

It is true i'm running 87... currently I'm sure there is enough space in the system (see df -h output in my previous post) but a few days earlier I realized the system was full and I had to remove manually some very heavy multimedia files in order to save space. Maybe things were wrong before that? I really dont know.
Thanks for having a look to my problem.

---

### Post by TheFu on 2018-07-09
Thanks for the output.   Checking for out of storage when it comes to kernel issues is the most likely issue.  Having the disk full will make new kernels fail to install properly.  Looks like that problem existed for months.  Yes? 

The current issues aren't with the kernels or space.  It is the extra stuff tied to the kernels.  You don't need it except for the kernel that is being run.  

Try this:
**sudo apt-get purge linux-image-extra-4.4.0-9[0-9]-generic**
If it works, do the same for all the "extra" that are NOT -87-.  Don't remove any -87- kernel related files. And if you have -86- related packages, I wouldn't remove them either. Good to have 2 kernels that boot.

Let us know how it goes.   If it refuses to remove the "extra" packages, add a --force option.  After all that is handled, there might be issues remaining and we'll try to address them.

---

### Post by vfotop1 on 2018-07-12
Hi TheFu, thanks for your help again...

> Thanks for the output.   Checking for out of storage when it comes to kernel issues is the most likely issue.  Having the disk full will make new kernels fail to install properly.  Looks like that problem existed for months.  Yes? 
Yes indeed...haven't noticed what was going on until one of the system's users informed me that she couldn,t upload files with ftp. It was then that I found what was hapenning

> The current issues aren't with the kernels or space.  It is the extra stuff tied to the kernels.  You don't need it except for the kernel that is being run.  
Try this:
**sudo apt-get purge linux-image-extra-4.4.0-9[0-9]-generic**
Let us know how it goes.   If it refuses to remove the "extra" packages, add a --force option.  After all that is handled, there might be issues remaining and we'll try to address them.

I tried to purge with the command you suggest...this is the output:
```
vfotop1@dsmc2:~$ sudo apt-get purge linux-image-extra-4.4.0-9[0-9]-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-extra-4.4.0-92-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Note, selecting 'linux-image-extra-4.4.0-91-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Note, selecting 'linux-image-extra-4.4.0-93-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Note, selecting 'linux-image-extra-4.4.0-97-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Note, selecting 'linux-image-extra-4.4.0-96-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Note, selecting 'linux-image-extra-4.4.0-98-generic' for glob 'linux-image-extra-4.4.0-9[0-9]-generic'
Package 'linux-image-extra-4.4.0-91-generic' is not installed, so not removed
Package 'linux-image-extra-4.4.0-92-generic' is not installed, so not removed
Package 'linux-image-extra-4.4.0-93-generic' is not installed, so not removed
The following packages will be REMOVED:
  linux-image-extra-4.4.0-101-generic linux-image-extra-4.4.0-103-generic
  linux-image-extra-4.4.0-104-generic linux-image-extra-4.4.0-109-generic
  linux-image-extra-4.4.0-112-generic linux-image-extra-4.4.0-116-generic
  linux-image-extra-4.4.0-119-generic linux-image-extra-4.4.0-121-generic
  linux-image-extra-4.4.0-124-generic linux-image-extra-4.4.0-127-generic
  linux-image-extra-4.4.0-128-generic linux-image-extra-4.4.0-96-generic
  linux-image-extra-4.4.0-97-generic linux-image-extra-4.4.0-98-generic
0 upgraded, 0 newly installed, 14 to remove and 9 not upgraded.
22 not fully installed or removed.
After this operation, 2,156 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 101570 files and directories currently installed.)
Removing linux-image-extra-4.4.0-101-generic (4.4.0-101.124) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-101-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-101-generic
WARNING: missing /lib/modules/4.4.0-101-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-101-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_TWYU2M/lib/modules/4.4.0-101-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_TWYU2M/lib/modules/4.4.0-101-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/x-grub-legacy-ec2 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-4.4.0-128-generic
Found kernel: /boot/vmlinuz-4.4.0-98-generic
Found kernel: /boot/vmlinuz-4.4.0-87-generic
Found kernel: /boot/vmlinuz-4.4.0-128-generic
Found kernel: /boot/vmlinuz-4.4.0-98-generic
Found kernel: /boot/vmlinuz-4.4.0-87-generic
Updating /boot/grub/menu.lst ... done

run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Generating grub configuration file ...
grub-probe: error: disk `mduuid/a41897fab803fd1759180dfca667926e,1' not found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-101-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
```
Unfortunately the is no "--force" parameter in apt, only in dpkg I believe but the erros are the same invoking dpkg.
The "no such file/directory" messages can be fixed by touching and creating dirs, but the only message I don't know what to do, is the grub-probe error at the end. 
I just copy it here because you might lose it in the long previous output
```
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Generating grub configuration file ...
grub-probe: error: disk `mduuid/a41897fab803fd1759180dfca667926e,1' not found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-101-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
```

There was a move of this system from a previous disk to a new one, so this might actually be a grub error instead!
my blkid shows the following disks
```
vfotop1@dsmc2:~$ blkid
/dev/sda: UUID="LSI     M-^@M-^F&M-^BM-^@M-^F4M-^E2]6^C8`DM-0" TYPE="ddf_raid_member"
/dev/sdd1: UUID="cac214ec-284e-4dc7-957f-9f0099041409" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000383cf-01"
/dev/sdd5: UUID="7309d624-0ccd-466a-899f-9d2f15365dd1" TYPE="ext4" PARTUUID="000383cf-05"
/dev/sdb1: UUID="e9252d1c-0e4b-4332-a6b0-e3e2f6b38cb9" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="00096bcd-01"
/dev/md126p1: UUID="c3ed324a-e103-4234-9ea6-1833b7e1d7ac" TYPE="ext4"
/dev/md126p2: UUID="9091718a-7252-4a03-96b3-cf2711f0ecd6" TYPE="swap"
/dev/md126p5: UUID="0d59b948-8b80-4443-866f-71a057c01475" SEC_TYPE="ext2" TYPE="ext3"

```
The /dev/md126p1 is the disk where the whole system resides (mounted as "/")

---

### Post by TheFu on 2018-07-12
FTP?  That's a problem.  Plain FTP cannot be allowed for security reasons. sftp should be forced onto users. They don't get a choice.

No user should be allowed to fill the disks for the OS and critical partitions.
A method to solve that would be to follow best practices for server partitioning.  It is NOT having 1 huge partition, BTW. Or have per-user quotas enforced.

Repartitioning generally is easiest when installing the OS, so trying to fix this wouldn't be useful. Time to reload it.  If you use LVM, many things are much more flexible, for the cost of a little more complexity.

There might be a way to fix the APT, but at this point, I'd wipe and reload everything, repartitioning.

---

