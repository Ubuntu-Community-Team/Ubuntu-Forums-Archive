---
title: "Can't remove old kernel or some other problem"
date: 2019-12-19
forum: Installation &amp; Upgrades
---

### Post by vitaliy-zdrok on 2019-12-19
this is what i can see when trying to install something:
```
 @ :~# sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  python-cheetah python-json-pointer python-jsonpatch python-oauth python-prettytable python-yaml
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-image-4.4.0-170-generic linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic python3-blinker python3-cffi-backend python3-configobj python3-cryptography
  python3-jinja2 python3-json-pointer python3-jsonpatch python3-jwt python3-markupsafe python3-oauthlib python3-prettytable python3-serial
The following packages will be upgraded:
  cloud-init git git-man intel-microcode libpcap0.8 libsqlite3-0 linux-generic linux-headers-generic linux-image-generic linux-libc-dev python3-psutil
11 upgraded, 17 newly installed, 2 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0 B/74.8 MB of archives.
After this operation, 1,820 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-85-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
WARNING: missing /lib/modules/3.13.0-85-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-85-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_iWLxqA/lib/modules/3.13.0-85-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_iWLxqA/lib/modules/3.13.0-85-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-86-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
WARNING: missing /lib/modules/3.13.0-86-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-86-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_BDVSlZ/lib/modules/3.13.0-86-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_BDVSlZ/lib/modules/3.13.0-86-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2019-12-19
vitaliy-zdrok; Hello - long time,no comment 

Show us:
```

dpkg -l | grep linux-

```

[INDENT]together we can
[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-19
> **Bashing-om said:**
> vitaliy-zdrok; Hello - long time,no comment 

Show us:
```

dpkg -l | grep linux-

```
[INDENT]together we can
[/INDENT]

here 
```
:~# dpkg -l | grep linux-ii  linux-base                             4.5ubuntu1~16.04.1                              all          Linux image base package
iF  linux-firmware                         1.157.22                                        all          Firmware for Linux kernel drivers
iU  linux-generic                          4.4.0.166.174                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-170               3.13.0-170.220                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-166                4.4.0-166.195                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.4.0.166.174                                   amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-170-generic         3.13.0-170.220                                  amd64        Signed kernel image generic
rc  linux-image-3.13.0-77-generic          3.13.0-77.121                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic          3.13.0-79.123                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic          3.13.0-85.129                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic          3.13.0-86.131                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-166-generic          4.4.0-166.195                                   amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-77-generic    3.13.0-77.121                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic    3.13.0-79.123                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-85-generic    3.13.0-85.129                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-86-generic    3.13.0-86.131                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                    4.4.0.166.174                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.4.0-169.198                                   amd64        Linux Kernel Headers for development
ii  linux-modules-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-170-generic 3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-166-generic  4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
```
:KS

---

### Post by Bashing-om on 2019-12-19
vitaliy-zdrok;

As there is:
> 
iF  linux-image-4.4.0-166-generic 


What kernel are you presently booting ?
show us:
```

lsb_release -a
uname -r

```

Depending then is maybe try dpkg to remove these kernel remnants

[INDENT]if a 1st we do not succeed[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-19
> **Bashing-om said:**
> vitaliy-zdrok;

As there is:


What kernel are you presently booting ?
show us:
```

lsb_release -a
uname -r

```

Depending then is maybe try dpkg to remove these kernel remnants
[INDENT]if a 1st we do not succeed[/INDENT]


 @ :~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:        16.04
Codename:       xenial
 @ :~# uname -r
4.4.0-166-generic

---

### Post by Bashing-om on 2019-12-19
vitaliy-zdrok -

Ouch !

> 
iF  linux-image-4.4.0-166-generic 



Before else let's get your booting kernel installed.

What results:
```

sudo apt update
sudo apt install --reinstall linux-generic
sudo apt install --reinstall  linux-image-4.4.0-166-generic

```

[INDENT]maybe Yes
[INDENT][INDENT]could be, not so yes[/INDENT][/INDENT][/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-19
Here the output, i've seen it many times ;/
```

root@ :~# sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Fetched 109 kB in 0s (221 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
11 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ :~# sudo apt install --reinstall linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-headers-generic linux-image-4.4.0-170-generic
  linux-image-generic linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-image-4.4.0-170-generic
  linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 2 to remove and 8 not upgraded.
7 not fully installed or removed.
Need to get 0 B/66.2 MB of archives.
After this operation, 2,167 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-85-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
WARNING: missing /lib/modules/3.13.0-85-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-85-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_Kqrakr/lib/modules/3.13.0-85-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Kqrakr/lib/modules/3.13.0-85-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-86-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
WARNING: missing /lib/modules/3.13.0-86-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-86-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_G7gfL4/lib/modules/3.13.0-86-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_G7gfL4/lib/modules/3.13.0-86-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ :~# sudo apt install --reinstall  linux-image-4.4.0-166-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] y
E: Internal Error, No file name for linux-image-4.4.0-166-generic:amd64 



```

---

### Post by Bashing-om on 2019-12-19
vitaliy-zdrok; Yukkie

Before we go getting dirty. let's try dpkg:

```

sudo dpkg -P linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic

```

[INDENT]maybe ?[/INDENT]

---

### Post by ubfan1 on 2019-12-19
Although there may be an appropriate set of switches to force the package manager to purge a package, even if its files are already deleted, I found that simply creating (empty)  files/directories (with touch and mkdir) will satisfy the delete attempt, and allow the purge to complete.

---

### Post by vitaliy-zdrok on 2019-12-20
It shows same errors: 
```

:~# sudo dpkg -P linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-85-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
WARNING: missing /lib/modules/3.13.0-85-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-85-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-86-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
WARNING: missing /lib/modules/3.13.0-86-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-86-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
depmod: WARNING: could not open /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.builtin: No such file or directory
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic

```

---

### Post by vitaliy-zdrok on 2019-12-20
I also want to give you some background, it is a remote digital ocean ubuntu server that was updated from 14 to 16, i had some problems after it but it has been fixed and worked fine ([https://askubuntu.com/questions/1187420/no-priority-or-zero-specified-for-pin/1187579#1187579](https://askubuntu.com/questions/1187420/no-priority-or-zero-specified-for-pin/1187579#1187579)) i could install new packages, what happened again i don't know ;/

---

### Post by ubfan1 on 2019-12-20
Grepping (for the word such) and editing the output of the dpkg package to make a script to create the missing files and directories gives the below (try running it as a script, and then repeat the dpkg purge). Repeat as necessary until the purge works.
-----
sudo touch /boot/System.map-3.13.0-85-generic

sudo mkdir /lib/modules/3.13.0-85-generic

sudo mkdir -p /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic
sudo touch /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.order
sudo touch /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.builtin


sudo touch /boot/System.map-3.13.0-86-generic

sudo mkdir /lib/modules/3.13.0-86-generic

sudo mkdir -p /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic
sudo touch /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.order
sudo touch /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.builtin

---

### Post by vitaliy-zdrok on 2019-12-20
> **ubfan1 said:**
> Grepping (for the word such) and editing the output of the dpkg package to make a script to create the missing files and directories gives the below (try running it as a script, and then repeat the dpkg purge). Repeat as necessary until the purge works.
-----
sudo touch /boot/System.map-3.13.0-85-generic

sudo mkdir /lib/modules/3.13.0-85-generic

sudo mkdir -p /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic
sudo touch /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.order
sudo touch /var/tmp/mkinitramfs_U4mJX9/lib/modules/3.13.0-85-generic/modules.builtin


sudo touch /boot/System.map-3.13.0-86-generic

sudo mkdir /lib/modules/3.13.0-86-generic

sudo mkdir -p /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic
sudo touch /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.order
sudo touch /var/tmp/mkinitramfs_3O4oGA/lib/modules/3.13.0-86-generic/modules.builtin

doesn't work ;(

---

### Post by ubfan1 on 2019-12-20
What fails now when you repeat the 
sudo dpkg -P linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic  
command?  All the previous fatal missing... errors should be gone.  New errors for missing... get the same treatment, the package manager does not really care if the file is zero length.

---

### Post by vitaliy-zdrok on 2019-12-21
> **ubfan1 said:**
> What fails now when you repeat the 
sudo dpkg -P linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic  
command?  All the previous fatal missing... errors should be gone.  New errors for missing... get the same treatment, the package manager does not really care if the file is zero length.

```
:~# sudo dpkg -P linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
```

---

### Post by ubfan1 on 2019-12-21
Ouch, looks like the 3.13 kernels are too old for the current tools.  More investigation of the dpkg options is needed to see if they offer any fixes.  See if dpkg --audit suggests any actions, then maybe try --force-bad-path.  I'll look on an old system to see if I have one with an old 3.13 to experiment with. Worst case would be a direct edit of the package database, but that's a last resort, and I've never done that.

---

### Post by vitaliy-zdrok on 2019-12-21
> **ubfan1 said:**
> Ouch, looks like the 3.13 kernels are too old for the current tools.  More investigation of the dpkg options is needed to see if they offer any fixes.  See if dpkg --audit suggests any actions, then maybe try --force-bad-path.  I'll look on an old system to see if I have one with an old 3.13 to experiment with. Worst case would be a direct edit of the package database, but that's a last resort, and I've never done that.

here what it suggest
```
:~# dpkg --auditThe following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-generic  Generic Linux kernel image


The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      generic modular initramfs generator (automation)
 linux-firmware       Firmware for Linux kernel drivers
 linux-image-4.4.0-166-generic Signed kernel image generic


The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-extra-3.13.0-85-generic Linux kernel extra modules for version 3.1
 linux-image-extra-3.13.0-86-generic Linux kernel extra modules for version 3.1
```

---

### Post by ubfan1 on 2019-12-21
I looked, and must have cleaned out the old 3.13 kernel.  It was on a 14.04 system, unupgraded, so there was no real problem purging it.
Some other things to try, after looking at the dpkg man pages:
--post-invoke=command Try to replace the broken post-removal script with a command line arg.
Look at the linux...postrm scripts in /var/lib/dpkg/info replace the old kernel ones with an empty file or maybe just an exit 0 line.  Backup ones you alter just in case it doesn't work, so they can be restored if you choose.
What if you just edited the /var/lib/dpkg/status file to claim the old kernel was deinstalled?
--no-triggers  Try to suppress the postrm script?
Take a look at some of the other deb-xxx man pages to see if it is possible to override the postrm scripts.

---

### Post by mörgæs on 2019-12-22
Your installation appears to be around five years old and has suffered several upgrades.

Ubuntu has made many experiments back and forth during that period of time which might have left various amounts of cruft behind.

In addition to the kernel problem you could have other undetected problems, and most likely some hard disk space is wasted. The latter can be investigated by running (for example) the two commands
```
du -hs ~/.[^.]* 
sudo du -hs /var/log

```You could consider a fresh install which solves all the aforementioned problems in one go.

---

### Post by vitaliy-zdrok on 2019-12-22
> **ubfan1 said:**
> I looked, and must have cleaned out the old 3.13 kernel.  It was on a 14.04 system, unupgraded, so there was no real problem purging it.
Some other things to try, after looking at the dpkg man pages:
--post-invoke=command Try to replace the broken post-removal script with a command line arg.
Look at the linux...postrm scripts in /var/lib/dpkg/info replace the old kernel ones with an empty file or maybe just an exit 0 line.  Backup ones you alter just in case it doesn't work, so they can be restored if you choose.
What if you just edited the /var/lib/dpkg/status file to claim the old kernel was deinstalled?
--no-triggers  Try to suppress the postrm script?
Take a look at some of the other deb-xxx man pages to see if it is possible to override the postrm scripts.
i really don't understand what you're saying here =/

---

### Post by vitaliy-zdrok on 2019-12-22
> **mörgæs said:**
> Your installation appears to be around five years old and has suffered several upgrades.

Ubuntu has made many experiments back and forth during that period of time which might have left various amounts of cruft behind.

In addition to the kernel problem you could have other undetected problems, and most likely some hard disk space is wasted. The latter can be investigated by running (for example) the two commands
```
du -hs ~/.[^.]* 
sudo du -hs /var/log

```You could consider a fresh install which solves all the aforementioned problems in one go.

```
 du -hs ~/.[^.]*16K     /root/.aptitude
44K     /root/.bash_history
4.0K    /root/.bashrc
20K     /root/.cache
0       /root/.cloud-locale-test.skip
20K     /root/.config
8.0K    /root/.distlib
4.0K    /root/.gitconfig
8.0K    /root/.local
889M    /root/.meteor
4.0K    /root/.mysql_history
8.0K    /root/.nano
82M     /root/.npm
310M    /root/.nvm
16K     /root/.pip
2.5G    /root/.pm2
4.0K    /root/.profile
4.0K    /root/.rnd
4.0K    /root/.selected_editor
16K     /root/.ssh
8.0K    /root/.vim
12K     /root/.viminfo

4.0K    /root/.w3m
```

```
:~# sudo du -hs /var/log
1.1G    /var/log
```

---

### Post by mörgæs on 2019-12-22
That's around 5 GB. A clean-up might be possible but I take the number of forgotten files as akin to the odometer of a car. Fresh install is still my advice. 

By the way, are you root during normal operations?

---

### Post by vitaliy-zdrok on 2019-12-22
> **mörgæs said:**
> That's around 5 GB. 
i can just clean it

> **mörgæs said:**
> By the way, are you root during normal operations?
It always been that way before me i suppose

---

### Post by Impavidus on 2019-12-23
When you remove linux-image-extra-3.13.0-85-generic, the package manager runs a post-removal script to ensure that you can safely remove that package while keeping linux-image-3.13.0-85-generic. It's pointless, as you don't want to keep linux-image-3.13.0-85-generic (in fact, it has already been removed), but this post-removal script is causing the package manager to crash.

I only see two ways to fix this. The first is to do this:
> **ubfan1 said:**
> I looked, and must have cleaned out the old 3.13 kernel.  It was on a 14.04 system, unupgraded, so there was no real problem purging it.
Some other things to try, after looking at the dpkg man pages:
--post-invoke=command Try to replace the broken post-removal script with a command line arg.
Look at the linux...postrm scripts in /var/lib/dpkg/info replace the old kernel ones with an empty file or maybe just an exit 0 line.  Backup ones you alter just in case it doesn't work, so they can be restored if you choose.
What if you just edited the /var/lib/dpkg/status file to claim the old kernel was deinstalled?
--no-triggers  Try to suppress the postrm script?
Take a look at some of the other deb-xxx man pages to see if it is possible to override the postrm scripts.
This allows you to skip the post-removal script. After that, you'll probably have to do some cleanup manually. If you have difficulty understanding this option, it's probably better to try the alternative.

The other solution is a fresh install.

It appears you run Ubuntu 16.04, with kernel 4.4.0. Kernel 3.13.0 is a leftover from before your upgrade from Ubuntu 14.04. Somehow, you got conflicting packages installed, leading to this problem. Adding to that, I see that you run many commands from a root shell (the prompt looks like root@...:~#), but still use sudo for those commands. That's pointless and harmless, but indicates that you're not very familiar with the concept of the root account (no blame, none of us were born with that knowledge). Now you write> **vitaliy-zdrok said:**
> 
It always been that way before me i supposewhich make me believe your computer is a big mess and you've only begun to see the effects of that.

My suggestion, seeing that Ubuntu 16.04 is getting a bit old anyway, is a fresh install of Ubuntu 18.04. So I'm with mörgæs.

---

### Post by rsteinmetz70112 on 2019-12-23
I'm new to this thread I'm sorry if I missed it but I don't see that you have tried:

```
sudo dpkg --configure -a
```

Which is supposed to configure all currently installed packages and fix any problems. If it doesn't work it will usually give you a list of broken or missing packages.


```
sudo apt install -f
```

Which will fix broken packages. 

However if the packages you need aren't in the repositories you have configured they can 't be installed. You may need to add the old repositories or go to he archive, download those old packages and install them. I've found that if you have a system in this state often installing one key package will allow the rest of the problems to work them selves out. I'm not sure if the 14.04 repositories are still on line, but if they're not these is an archive of them.

---

### Post by vitaliy-zdrok on 2019-12-23
> **rsteinmetz70112 said:**
>  
```
sudo dpkg --configure -a
``` 

```
Setting up initramfs-tools (0.122ubuntu8.14) ...update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.4.0-166-generic (4.4.0-166.195) ...
Setting up linux-firmware (1.157.22) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.166.174); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for linux-image-4.4.0-166-generic (4.4.0-166.195) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-4.4.0-166-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-generic
 linux-generic
 initramfs-tools
 linux-image-4.4.0-166-generic
```

> **rsteinmetz70112 said:**
>  

```
sudo apt install -f
```

```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ubfan1 on 2019-12-23
I'd vote for the reinstall too -- I've never actually tried to override a package script.  For a list of packages you installed, try the below, but I'm not sure if the list is totally accurate across releases(14 to 16), so consider it just a starting point of what to reinstall.

---

### Post by vitaliy-zdrok on 2019-12-23
but what if reinstall is no go? Are there some topics that might help me with it?

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok; Hey -

There is a dirty way to fix this. But it does result in breaking the package manager, a lot of command line "fu", and then having the package manager heal it's self. You will learn a bit about the operating system and system management taking this course. As others say, a clean fresh install could be your best option - depending on what you want to do.

[INDENT]It's ubuntu
[INDENT]break it, we get to keep the pieces -
[INDENT][INDENT][INDENT]and put it back together
[/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-23
> **Bashing-om said:**
> vitaliy-zdrok; Hey -

There is a dirty way to fix this. But it does result in breaking the package manager, a lot of command line "fu", and then having the package manager heal it's self. You will learn a bit about the operating system and system management taking this course. As others say, a clean fresh install could be your best option - depending on what you want to do.[INDENT]It's ubuntu[INDENT]break it, we get to keep the pieces -[INDENT][INDENT][INDENT]and put it back together
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I was planning to ream some linux-ubuntu-centos books, but not this month.
Is there any way to install packages without apt-get install? Gonna reinstall this OS anyway...
Those probems with package manager because OS was administrated through root?

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok - Hey hey :)

> 
Is there any way to install packages without apt-get install? Gonna reinstall this OS anyway...

Sure ! "wget" the files and That is a function of "dpkg"  to install. But you will have to manually handle any dependencies. 

Now, if you want to salvage this install, we can start by knowing what kernel that is fully installed that you can boot:
```

uname -r
dpkg -l | grep linux-

```

I will be preoccupied for the next couple of hours (now 20:30 GMT). and then I can fully focus on the salvage operation.

[INDENT]we can do that
[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-23
:popcorn: super!
> **Bashing-om said:**
> vitaliy-zdrok - Hey hey :)


Sure ! "wget" the files and That is a function of "dpkg"  to install. But you will have to manually handle any dependencies. 

Now, if you want to salvage this install, we can start by knowing what kernel that is fully installed that you can boot:
```

uname -r
dpkg -l | grep linux-

```

I will be preoccupied for the next couple of hours (now 20:30 GMT). and then I can fully focus on the salvage operation.[INDENT]we can do that
[/INDENT]


```

root@ghost:~# uname -r
4.4.0-166-generic
root@ghost:~# dpkg -l | grep linux-
ii  linux-base                             4.5ubuntu1~16.04.1                              all          Linux image base package
iF  linux-firmware                         1.157.22                                        all          Firmware for Linux kernel drivers
iU  linux-generic                          4.4.0.166.174                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-170               3.13.0-170.220                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-166                4.4.0-166.195                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.4.0.166.174                                   amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-170-generic         3.13.0-170.220                                  amd64        Signed kernel image generic
rc  linux-image-3.13.0-77-generic          3.13.0-77.121                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic          3.13.0-79.123                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic          3.13.0-85.129                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic          3.13.0-86.131                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-166-generic          4.4.0-166.195                                   amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-77-generic    3.13.0-77.121                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic    3.13.0-79.123                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-85-generic    3.13.0-85.129                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-86-generic    3.13.0-86.131                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                    4.4.0.166.174                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.4.0-169.198                                   amd64        Linux Kernel Headers for development
ii  linux-modules-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-170-generic 3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-166-generic  4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

```

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok - ouch !

> 
iF  linux-image-4.4.0-166-generic

And there is no fully installed kernels ! I do not see presently a way forward.

Let's give it a poke:
```

sudo apt install --reinstall linux-image-generic

```
see if we can pull in 4.4.0-166-generic to complete the package.

[INDENT]maybe yes
[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-23
> **Bashing-om said:**
> vitaliy-zdrok - ouch !


And there is no fully installed kernels ! I do not see presently a way forward.

Let's give it a poke:
```

sudo apt install --reinstall linux-image-generic

```
see if we can pull in 4.4.0-166-generic to complete the package.
[INDENT]maybe yes
[/INDENT]


```
sudo apt install --reinstall linux-image-genericReading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  linux-generic linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-headers-generic
  linux-image-4.4.0-170-generic linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-image-4.4.0-170-generic
  linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 2 to remove and 8 not upgraded.
7 not fully installed or removed.
Need to get 66.2 MB of archives.
After this operation, 2,167 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-modules-4.4.0-170-generic amd64 4.4.0-170.199 [12.0 MB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-4.4.0-170-generic amd64 4.4.0-170.199 [6,936 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-modules-extra-4.4.0-170-generic amd64 4.4.0-170.199 [36.6 MB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-generic amd64 4.4.0.170.178 [1,788 B]
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-image-generic amd64 4.4.0.170.178 [2,446 B]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-170 all 4.4.0-170.199 [9,989 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-4.4.0-170-generic amd64 4.4.0-170.199 [796 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-headers-generic amd64 4.4.0.170.178 [2,276 B]
Fetched 66.2 MB in 2s (26.2 MB/s)
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1.........................................]
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok; Maybe to the good :)

What now have we to work with ?
show us a new
```

dpkg -l | grep linux-

```

[INDENT]off and running now ?
[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-23
> **Bashing-om said:**
> vitaliy-zdrok; Maybe to the good :)

What now have we to work with ?
show us a new
```

dpkg -l | grep linux-

```
[INDENT]off and running now ?
[/INDENT]

same as before :-?

```

ii  linux-base                             4.5ubuntu1~16.04.1                              all          Linux image base package
iF  linux-firmware                         1.157.22                                        all          Firmware for Linux kernel drivers
iU  linux-generic                          4.4.0.166.174                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-170               3.13.0-170.220                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-166                4.4.0-166.195                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.4.0.166.174                                   amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-170-generic         3.13.0-170.220                                  amd64        Signed kernel image generic
rc  linux-image-3.13.0-77-generic          3.13.0-77.121                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic          3.13.0-79.123                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic          3.13.0-85.129                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic          3.13.0-86.131                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-166-generic          4.4.0-166.195                                   amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-77-generic    3.13.0-77.121                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic    3.13.0-79.123                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-85-generic    3.13.0-85.129                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-86-generic    3.13.0-86.131                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                    4.4.0.166.174                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.4.0-169.198                                   amd64        Linux Kernel Headers for development
ii  linux-modules-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-170-generic 3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-166-generic  4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

```

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok - yukkie

Does not look good for the home team :(

However. let's give a poke again:
```

sudo apt install --reinstall linux-generic

```

As this is the meta-package, maybe.

else, well yeah we can attempt a direct pull with "wget" from the library and install with "dpkg". Never been there in this situation,,but, in theory should be doable :)

[INDENT]if at 1st we do not succeed .........[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-23
> **Bashing-om said:**
> vitaliy-zdrok - yukkie

Does not look good for the home team :(

However. let's give a poke again:
```

sudo apt install --reinstall linux-generic

```

As this is the meta-package, maybe.

else, well yeah we can attempt a direct pull with "wget" from the library and install with "dpkg". Never been there in this situation,,but, in theory should be doable :)
[INDENT]if at 1st we do not succeed .........[/INDENT]


;/

```
 sudo apt install --reinstall linux-genericReading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-headers-generic linux-image-4.4.0-170-generic linux-image-generic linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-170 linux-headers-4.4.0-170-generic linux-image-4.4.0-170-generic linux-modules-4.4.0-170-generic linux-modules-extra-4.4.0-170-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 2 to remove and 8 not upgraded.
7 not fully installed or removed.
Need to get 0 B/66.2 MB of archives.
After this operation, 2,167 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)




dpkg -l | grep linux-
ii  linux-base                             4.5ubuntu1~16.04.1                              all          Linux image base package
iF  linux-firmware                         1.157.22                                        all          Firmware for Linux kernel drivers
iU  linux-generic                          4.4.0.166.174                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-170               3.13.0-170.220                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-166                4.4.0-166.195                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.4.0.166.174                                   amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-170-generic         3.13.0-170.220                                  amd64        Signed kernel image generic
rc  linux-image-3.13.0-77-generic          3.13.0-77.121                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic          3.13.0-79.123                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic          3.13.0-85.129                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic          3.13.0-86.131                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-166-generic          4.4.0-166.195                                   amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-77-generic    3.13.0-77.121                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic    3.13.0-79.123                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-85-generic    3.13.0-85.129                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-86-generic    3.13.0-86.131                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                    4.4.0.166.174                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.4.0-169.198                                   amd64        Linux Kernel Headers for development
ii  linux-modules-3.13.0-170-generic       3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-166-generic        4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-170-generic 3.13.0-170.220                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-166-generic  4.4.0-166.195                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
```

---

### Post by Bashing-om on 2019-12-23
vitaliy-zdrok; Welp !

Not giving up yet !

Let's try and install a mainline kernel - boot to grub and see if you can boot this 4.4.207 kernel.
run:
```

mkdir -p /tmp/kernel
cd /tmp/kernel

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-headers-4.4.207-0404207_4.4.207-0404207.201912210540_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-headers-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-image-unsigned-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-modules-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb

sudo dpkg -i *.deb

```

reboot into the 4.4.207 kernel from grub's boot menu (HOPE) and verify -
```

uname -r

```

then we can go back to getting dirty allover and try and clean this mess up.

[INDENT]where there is a will there is a way[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-24
> **Bashing-om said:**
> vitaliy-zdrok; Welp !

Not giving up yet !

Let's try and install a mainline kernel - boot to grub and see if you can boot this 4.4.207 kernel.
run:
```

mkdir -p /tmp/kernel
cd /tmp/kernel

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-headers-4.4.207-0404207_4.4.207-0404207.201912210540_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-headers-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-image-unsigned-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.207/linux-modules-4.4.207-0404207-generic_4.4.207-0404207.201912210540_amd64.deb

sudo dpkg -i *.deb

```

reboot into the 4.4.207 kernel from grub's boot menu (HOPE) and verify -
```

uname -r

```

then we can go back to getting dirty allover and try and clean this mess up.[INDENT]where there is a will there is a way[/INDENT]


Nice, thanks, i'll try it, but i want to ask, will my server stop for a while if i'll boot into grub?

---

### Post by rsteinmetz70112 on 2019-12-24
dpkg can install, reinstall, remove and purge packages, it has a lot fewer checks than apt which basically runs dpkg.

You are basically getting errors with a few packages;

>  linux-firmware
 linux-image-generic
 linux-generic
 initramfs-tools
 linux-image-4.4.0-166-generic
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic


I would first try reinstall initramfs-tools
```

sudo apt install --reinstall initramfs-tools
```

Then move to the linux packages one at a time.

---

### Post by vitaliy-zdrok on 2019-12-24
> **rsteinmetz70112 said:**
> dpkg can install, reinstall, remove and purge packages, it has a lot fewer checks than apt which basically runs dpkg.

You are basically getting errors with a few packages;




I would first try reinstall initramfs-tools
```

sudo apt install --reinstall initramfs-tools
```

Then move to the linux packages one at a time.
it can't be reinstalled

```

sudo apt install --reinstall initramfs-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] Y
E: Internal Error, No file name for initramfs-tools:amd64

```

---

### Post by Bashing-om on 2019-12-24
vitaliy-zdrok; Yukkie-ouch

Hey looks like rsteinmetz70112 has pointed us to the root of the issue !

We got to have that package;
see:
```

apt show initramfs-tools

```

So let's put the 'wget/install' back in out pocket and see what we can do with initramfs.

show us:
```

dpkg -l initramfs-tools

```

[INDENT][INDENT]on the right path ?
[/INDENT][/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-24
> **Bashing-om said:**
> vitaliy-zdrok; Yukkie-ouch

Hey looks like rsteinmetz70112 has pointed us to the root of the issue !

We got to have that package;
see:
```

apt show initramfs-tools

```

So let's put the 'wget/install' back in out pocket and see what we can do with initramfs.

show us:
```

dpkg -l initramfs-tools

```
[INDENT][INDENT]on the right path ?
[/INDENT]
[/INDENT]

dunno 

```
apt show initramfs-toolsPackage: initramfs-tools
Version: 0.122ubuntu8.14
Priority: important
Section: utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 128 kB
Provides: linux-initramfs-tool
Depends: initramfs-tools-core (= 0.122ubuntu8.14), linux-base
Suggests: bash-completion
Conflicts: linux-initramfs-tool, usplash (<< 0.5.50)
Breaks: console-setup (<< 1.72), cryptsetup (<< 2:1.6.6-4~), elilo (<< 3.12-3.1~), initscripts (<< 2.88dsf-59.3~), isc-dhcp-client (= 4.3.3-5ubuntu13), lilo (<< 22.8-8.2~), lvm2 (<< 2.02.111-2.1~), mountall (<< 2.0~), nplan (<< 0.32~16.04.5), s390-tools (<< 1.8.3-2~), systemd-sysv (<< 186)
Task: minimal, ubuntu-sdk
Supported: 5y
Download-Size: 8,938 B
APT-Manual-Installed: yes
APT-Sources: http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Description: generic modular initramfs generator (automation)
 This package builds a bootable initramfs for Linux kernel packages.  The
 initramfs is loaded along with the kernel and is responsible for
 mounting the root filesystem and starting the main init system.


N: There is 1 additional record. Please use the '-a' switch to see it
```

```
 dpkg -l initramfs-toolsDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-=======================================================================
iF  initramfs-tools                   0.122ubuntu8.14       all                   generic modular initramfs generator (automation)
```

---

### Post by Bashing-om on 2019-12-24
vitaliy-zdrok; Well- well well

Let'stry:
```

sudo apt install --reinstall initramfs-tools

```

somehow - someway; we got to get it installed.

[INDENT]looking for that way forward
[/INDENT]

---

### Post by vitaliy-zdrok on 2019-12-24
> **Bashing-om said:**
> vitaliy-zdrok; Well- well well

Let'stry:
```

sudo apt install --reinstall initramfs-tools

```

somehow - someway; we got to get it installed.[INDENT]looking for that way forward
[/INDENT]


it thorows error :popcorn:
```
sudo apt install --reinstall initramfs-toolsReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] y
E: Internal Error, No file name for initramfs-tools:amd64
```

---

### Post by Bashing-om on 2019-12-24
vitaliy-zdrok - As the plot thickens

A bit more direction ?
```

sudo apt install -f initramfs-tools

```

Maybe take a gander at what to we have to work with:
```

ls -al /var/cache/apt/archives/

```

^ consider here to force 'dpkg' and then "dpkg --configure -a".

-gots to be a way-

---

### Post by vitaliy-zdrok on 2019-12-25
> **Bashing-om said:**
> vitaliy-zdrok - As the plot thickens

A bit more direction ?
```

sudo apt install -f initramfs-tools

```

Maybe take a gander at what to we have to work with:
```

ls -al /var/cache/apt/archives/

```

^ consider here to force 'dpkg' and then "dpkg --configure -a".

-gots to be a way-

```

root@ghost:~# sudo apt install -f initramfs-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
initramfs-tools is already the newest version (0.122ubuntu8.14).
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ghost:~# ls -al /var/cache/apt/archives/
total 75168
drwxr-xr-x 3 root root    69632 Dec 24 13:19 .
drwxr-xr-x 3 root root     4096 Dec 25 06:21 ..
-rw-r--r-- 1 root root  3160452 Dec 10 14:03 git_1%3a2.7.4-0ubuntu1.7_amd64.deb
-rw-r--r-- 1 root root   736500 Dec 10 14:03 git-man_1%3a2.7.4-0ubuntu1.7_all.deb
-rw-r--r-- 1 root root    90152 Feb  7  2016 goaccess_1%3a0.9.4-1build1_amd64.deb
-rw-r--r-- 1 root root  2408010 Dec  3 18:53 intel-microcode_3.20191115.1ubuntu0.16.04.2_amd64.deb
-rw-r--r-- 1 root root   116898 Dec 10 12:33 libpcap0.8_1.7.4-2ubuntu0.1_amd64.deb
-rw-r--r-- 1 root root   397236 Dec  2 07:54 libsqlite3-0_3.11.0-1ubuntu1.3_amd64.deb
-rw-r--r-- 1 root root     1788 Nov 14 10:33 linux-generic_4.4.0.170.178_amd64.deb
-rw-r--r-- 1 root root  9989430 Nov 14 10:34 linux-headers-4.4.0-170_4.4.0-170.199_all.deb
-rw-r--r-- 1 root root   795846 Nov 14 10:34 linux-headers-4.4.0-170-generic_4.4.0-170.199_amd64.deb
-rw-r--r-- 1 root root     2276 Nov 14 10:33 linux-headers-generic_4.4.0.170.178_amd64.deb
-rw-r--r-- 1 root root  6935986 Nov 14 11:43 linux-image-4.4.0-170-generic_4.4.0-170.199_amd64.deb
-rw-r--r-- 1 root root     2446 Nov 14 10:33 linux-image-generic_4.4.0.170.178_amd64.deb
-rw-r--r-- 1 root root   839100 Nov 14 10:34 linux-libc-dev_4.4.0-170.199_amd64.deb
-rw-r--r-- 1 root root 11950326 Nov 14 10:34 linux-modules-4.4.0-170-generic_4.4.0-170.199_amd64.deb
-rw-r--r-- 1 root root 36567910 Nov 14 10:34 linux-modules-extra-4.4.0-170-generic_4.4.0-170.199_amd64.deb
-rw-r----- 1 root root        0 Apr 16  2014 lock
drwx------ 2 _apt root     4096 Dec 24 13:19 partial
-rw-r--r-- 1 root root   390208 Mar 28  2016 phoronix-test-suite_5.2.1-1ubuntu2_all.deb
-rw-r--r-- 1 root root  1282638 Oct 28 13:44 php7.0-cli_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root   843924 Oct 28 13:44 php7.0-common_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root    27174 Oct 28 13:44 php7.0-gd_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root    16886 Oct 28 13:44 php7.0-json_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root    77242 Oct 28 13:43 php7.0-opcache_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root    12806 Oct 28 13:44 php7.0-readline_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root   112494 Oct 28 13:44 php7.0-xml_7.0.33-0ubuntu0.16.04.7_amd64.deb
-rw-r--r-- 1 root root     2920 Apr  5  2016 php-cli_1%3a7.0+35ubuntu6_all.deb
-rw-r--r-- 1 root root    10774 Apr  5  2016 php-common_1%3a35ubuntu6_all.deb
-rw-r--r-- 1 root root     1928 Apr  5  2016 php-gd_1%3a7.0+35ubuntu6_all.deb
-rw-r--r-- 1 root root     1954 Apr  5  2016 php-xml_1%3a7.0+35ubuntu6_all.deb
-rw-r--r-- 1 root root    55652 Nov 28 07:43 python3-psutil_3.4.2-1ubuntu0.1_amd64.deb
root@ghost:~# dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.4.0-166-generic (4.4.0-166.195) ...
Setting up linux-firmware (1.157.22) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.166.174); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for linux-image-4.4.0-166-generic (4.4.0-166.195) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.4.0-166-generic
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-4.4.0-166-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-generic
 linux-generic
 initramfs-tools
 linux-image-4.4.0-166-generic
```

---

### Post by rsteinmetz70112 on 2019-12-26
Looks like the install version does not support the older kernel version.

> update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: **unsupported kernel version!**

I've never seen that error and have had numerous old kernel versions installed. 

You could try reinstall other initramfs packages it is possible something in one of them is messed up.

I also see this error 

> linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

I would try to configure linux-firmware

```
sudo dpkg --configure linux-firmware
```

You could try reinstalling the  kernel version or removing it with dpkg.

Before doing that you should verify the currently running kernel version with 

```
 uname -r 
or 
 cat /proc/version_signature
```

If the currently running kernel version is something other than 3.13.0-85 removing that kernel should not affect your computer, although anything could happen.
One way to remove a kernel and all of the associated packages is 

```
sudo apt-get remove *3.13.0-85*
```

That should remove the kernel and other packages related to the specific kernel.

Running 
```
sudo apt-get remove --simulate *3.13.0-85*
```
should run the command without changing anything.

---

### Post by vitaliy-zdrok on 2019-12-29
> **rsteinmetz70112 said:**
> Looks like the install version does not support the older kernel version.



I've never seen that error and have had numerous old kernel versions installed. 

You could try reinstall other initramfs packages it is possible something in one of them is messed up.

I also see this error 



I would try to configure linux-firmware

```
sudo dpkg --configure linix-firmware
```

You could try reinstalling the  kernel version or removing it with dpkg.

Before doing that you should verify the currently running kernel version with 

```
 uname -r 
or 
 cat /proc/version_signature
```

If the currently running kernel version is something other than 3.13.0-85 removing that kernel should not affect your computer, although anything could happen.
One way to remove a kernel and all of the associated packages is 

```
sudo apt-get remove *3.13.0-85*
```

That should remove the kernel and other packages related to the specific kernel.

Running 
```
sudo apt-get remove --simulate *3.13.0-85*
```
should run the command without changing anything.

```
root@ghost:~# sudo dpkg --configure linix-firmwaredpkg: error processing package linix-firmware (--configure):
 no package named 'linix-firmware' is installed, cannot configure
Errors were encountered while processing:
 linix-firmware
root@ghost:~#  uname -r
4.4.0-166-generic
root@ghost:~# sudo apt-get remove *3.13.0-85*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.13.0-85-generic' for glob '*3.13.0-85*'
Note, selecting 'linux-image-extra-3.13.0-85-generic' for glob '*3.13.0-85*'
Note, selecting 'linux-headers-3.13.0-85-generic' for glob '*3.13.0-85*'
Package 'linux-headers-3.13.0-85-generic' is not installed, so not removed
Package 'linux-image-3.13.0-85-generic' is not installed, so not removed
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 106213 files and directories currently installed.)
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-85-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-86-generic (3.13.0-86.131) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-86-generic /boot/vmlinuz-3.13.0-86-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-86-generic
E: amd64-microcode: unsupported kernel version!
W: plymouth module (/lib/x86_64-linux-gnu/plymouth//ubuntu-text.so) missing, skipping that theme.
sync: invalid option -- 'f'
Try 'sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-86-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-85-generic
 linux-image-extra-3.13.0-86-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ghost:~# sudo apt-get remove --simulate *3.13.0-85*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.13.0-85-generic' for glob '*3.13.0-85*'
Note, selecting 'linux-image-extra-3.13.0-85-generic' for glob '*3.13.0-85*'
Note, selecting 'linux-headers-3.13.0-85-generic' for glob '*3.13.0-85*'
Package 'linux-headers-3.13.0-85-generic' is not installed, so not removed
Package 'linux-image-3.13.0-85-generic' is not installed, so not removed
The following packages will be REMOVED:
  linux-image-extra-3.13.0-85-generic linux-image-extra-3.13.0-86-generic
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
7 not fully installed or removed.
Remv linux-image-extra-3.13.0-85-generic [3.13.0-85.129] [linux-image-extra-3.13.0-86-generic:amd64 ]
Remv linux-image-extra-3.13.0-86-generic [3.13.0-86.131]
Conf initramfs-tools (0.122ubuntu8.14 Ubuntu:16.04/xenial-security [all])
Conf linux-firmware (1.157.22 Ubuntu:16.04/xenial-security [all])
Conf linux-image-4.4.0-166-generic (4.4.0-166.195 Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-generic (4.4.0.170.178 Ubuntu:16.04/xenial-security [amd64])
Conf linux-generic (4.4.0.170.178 Ubuntu:16.04/xenial-security [amd64]) 
```

---

### Post by mörgæs on 2019-12-30
If you are given the task of administrating a server you should pay attention to each and every command you execute. Blind copy-paste could bring you into trouble especially since you are doing everything as root.

Competent people are helping you but competent people also make mistakes, for example there is an obvious typo in ```
sudo dpkg --configure linix-firmware
``` 

You were lucky that no harm was done but in GNU/Linux commands one character often has a big impact. For your own sake you need to put more effort into learning and understading what the proposed commands do.

---

### Post by Impavidus on 2019-12-30
> **vitaliy-zdrok said:**
> but what if reinstall is no go? Are there some topics that might help me with it?

Simple, just make sure you never get into that situation. And if you get into a situation where you can't reinstall, make sure you get out again.

Although pretty much every problem in Linux can be fixed, there are cases when a fresh install is the best way out of trouble. How much progress have you made in the past week? With proper backups this can be solved with a fresh install and a few hours of downtime (maybe less), while at the same time upgrading to a more recent release of Ubuntu. That would be necessary anyway when 16.04 reaches end of life 15 months from now.

---

### Post by vitaliy-zdrok on 2020-02-08
would be so great if someone have ideas to try :D

---

### Post by deadflowr on 2020-02-08
What does this stuff currently show:
[https://ubuntuforums.org/showthread.php?t=2433495&p=13918343#post13918343]("https://ubuntuforums.org/showthread.php?t=2433495&p=13918343#post13918343")
as well as the output of the upgrade commands.

And how feasible is Impavidus' suggestion to backup/reinstall?

---

