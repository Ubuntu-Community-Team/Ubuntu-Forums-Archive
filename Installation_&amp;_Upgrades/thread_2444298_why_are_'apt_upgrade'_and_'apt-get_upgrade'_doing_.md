---
title: "why are 'apt upgrade' and 'apt-get upgrade' doing different things?"
date: 2020-05-28
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2020-05-28
I thought 'apt' was just supposed to break out some useful commands from 'apt-get' but that they are supposed to do the same thing.  But when I 'upgrade', I get different results using 'apt' vs 'apt-get'.  Also, different responses with 'update'... (For example, with update, one stops at Reading package lists, but the other builds dependency tree and reads state information..)

```
anotherChris@HAL9000:~$ sudo apt-get upgrade
[sudo] password for anotherChris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  linux-libc-dev ubuntu-minimal ubuntu-standard
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,102 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-minimal amd64 1.450.1 [2,748 B]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-standard amd64 1.450.1 [2,788 B]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-libc-dev amd64 5.4.0-33.37 [1,096 kB]
Fetched 1,102 kB in 3s (324 kB/s)         
(Reading database ... 270708 files and directories currently installed.)
Preparing to unpack .../ubuntu-minimal_1.450.1_amd64.deb ...
Unpacking ubuntu-minimal (1.450.1) over (1.450) ...
Preparing to unpack .../ubuntu-standard_1.450.1_amd64.deb ...
Unpacking ubuntu-standard (1.450.1) over (1.450) ...
Preparing to unpack .../linux-libc-dev_5.4.0-33.37_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-33.37) over (5.4.0-31.35) ...
Setting up ubuntu-minimal (1.450.1) ...
Setting up linux-libc-dev:amd64 (5.4.0-33.37) ...
Setting up ubuntu-standard (1.450.1) ...
anotherChris@HAL9000:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-5.4.0-33 linux-headers-5.4.0-33-generic linux-image-5.4.0-33-generic
  linux-modules-5.4.0-33-generic linux-modules-extra-5.4.0-33-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.9 MB of archives.
After this operation, 359 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-5.4.0-33-generic amd64 5.4.0-33.37 [14.4 MB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.4.0-33-generic amd64 5.4.0-33.37 [8,869 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.4.0-33-generic amd64 5.4.0-33.37 [38.5 MB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-generic amd64 5.4.0.33.38 [1,900 B]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-generic amd64 5.4.0.33.38 [2,708 B]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-33 all 5.4.0-33.37 [10.9 MB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-33-generic amd64 5.4.0-33.37 [1,211 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-generic amd64 5.4.0.33.38 [2,592 B]
Fetched 73.9 MB in 38s (1,932 kB/s)                                                         
Selecting previously unselected package linux-modules-5.4.0-33-generic.
(Reading database ... 270708 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.4.0-33-generic_5.4.0-33.37_amd64.deb ...
Unpacking linux-modules-5.4.0-33-generic (5.4.0-33.37) ...
Selecting previously unselected package linux-image-5.4.0-33-generic.
Preparing to unpack .../1-linux-image-5.4.0-33-generic_5.4.0-33.37_amd64.deb ...
Unpacking linux-image-5.4.0-33-generic (5.4.0-33.37) ...
Selecting previously unselected package linux-modules-extra-5.4.0-33-generic.
Preparing to unpack .../2-linux-modules-extra-5.4.0-33-generic_5.4.0-33.37_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-33-generic (5.4.0-33.37) ...
Preparing to unpack .../3-linux-generic_5.4.0.33.38_amd64.deb ...
Unpacking linux-generic (5.4.0.33.38) over (5.4.0.31.36) ...
Preparing to unpack .../4-linux-image-generic_5.4.0.33.38_amd64.deb ...
Unpacking linux-image-generic (5.4.0.33.38) over (5.4.0.31.36) ...
Selecting previously unselected package linux-headers-5.4.0-33.
Preparing to unpack .../5-linux-headers-5.4.0-33_5.4.0-33.37_all.deb ...
Unpacking linux-headers-5.4.0-33 (5.4.0-33.37) ...
Selecting previously unselected package linux-headers-5.4.0-33-generic.
Preparing to unpack .../6-linux-headers-5.4.0-33-generic_5.4.0-33.37_amd64.deb ...
Unpacking linux-headers-5.4.0-33-generic (5.4.0-33.37) ...
Preparing to unpack .../7-linux-headers-generic_5.4.0.33.38_amd64.deb ...
Unpacking linux-headers-generic (5.4.0.33.38) over (5.4.0.31.36) ...
Setting up linux-modules-5.4.0-33-generic (5.4.0-33.37) ...
Setting up linux-headers-5.4.0-33 (5.4.0-33.37) ...
Setting up linux-image-5.4.0-33-generic (5.4.0-33.37) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.4.0-31-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-31-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.4.0-33-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.4.0-33-generic
Setting up linux-modules-extra-5.4.0-33-generic (5.4.0-33.37) ...
Setting up linux-headers-5.4.0-33-generic (5.4.0-33.37) ...
Setting up linux-image-generic (5.4.0.33.38) ...
Setting up linux-headers-generic (5.4.0.33.38) ...
Setting up linux-generic (5.4.0.33.38) ...
Processing triggers for linux-image-5.4.0-33-generic (5.4.0-33.37) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-33-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-33-generic
Found initrd image: /boot/initrd.img-5.4.0-33-generic
Found linux image: /boot/vmlinuz-5.4.0-31-generic
Found initrd image: /boot/initrd.img-5.4.0-31-generic
Found linux image: /boot/vmlinuz-5.4.0-29-generic
Found initrd image: /boot/initrd.img-5.4.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  /dev/sdb: open failed: No medium found
  /dev/sdb: open failed: No medium found
done
anotherChris@HAL9000:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-29 linux-headers-5.4.0-29-generic linux-image-5.4.0-29-generic
  linux-modules-5.4.0-29-generic linux-modules-extra-5.4.0-29-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anotherChris@HAL9000:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-29 linux-headers-5.4.0-29-generic linux-image-5.4.0-29-generic
  linux-modules-5.4.0-29-generic linux-modules-extra-5.4.0-29-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anotherChris@HAL9000:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]                   
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease                                      
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]                     
Get:4 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [18.7 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security/main DEP-11 48x48 Icons [4,655 B]
Get:6 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [208 B]
Get:7 http://archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [66.9 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [145 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [92.6 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [30.2 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [74.0 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [136 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [532 B]
Fetched 881 kB in 3s (257 kB/s)        
Reading package lists... Done
anotherChris@HAL9000:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease 
Hit:3 http://archive.ubuntu.com/ubuntu focal-backports InRelease                     
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
anotherChris@HAL9000:~$ sudo apt-get update
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done

```

---

### Post by dino99 on 2020-05-28
apt-get may be considered as lower-level and "back-end", and support other APT-based tools. apt is designed for end-users (human) and its output may be changed between versions.
[http://manpages.ubuntu.com/manpages/focal/en/man8/apt.8.html](http://manpages.ubuntu.com/manpages/focal/en/man8/apt.8.html)

---

### Post by anotherChris on 2020-05-28
> **dino99 said:**
> apt-get may be considered as lower-level and "back-end", and support other APT-based tools. apt is designed for end-users (human) and its output may be changed between versions.
[http://manpages.ubuntu.com/manpages/focal/en/man8/apt.8.html](http://manpages.ubuntu.com/manpages/focal/en/man8/apt.8.html)


I think you just re-stated the basis of my question.  My question is, why is the "upgrade" command doing different upgrades depending on whether its apt or apt-get?  Shouldn't they be doing the same thing?  

If they shouldn't be doing the same thing, which one is equivalent to the "Apply Full Upgrade" GUI interface?

---

### Post by broadcast23 on 2020-05-28
I would think that apt-get dist-upgrade is equivalent to apt full-upgrade

---

### Post by Impavidus on 2020-05-28
It appears that the developers of apt decided that it was more useful to have a command that installs all available upgrades, even if that means installing new packages, but not if that means removing packages. That option isn't available from apt-get, but because of the scripts that use apt-get, apt-get's behaviour cannot be changed. So they made a new tool and added a warning that its behaviour might change in the future. If apt had done exactly the same as apt-get, there would have been no need to make apt.

---

