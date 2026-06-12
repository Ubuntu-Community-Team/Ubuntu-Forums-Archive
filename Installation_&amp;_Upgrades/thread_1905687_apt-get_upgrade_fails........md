---
title: "apt-get upgrade fails......."
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by greggc2006 on 2012-01-07
.....I cannot explain my problems better than showing you this:-
```
gregg@ubuntu64-W150HRM:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nautilus-actions-extra
The following packages will be upgraded:
  python-gi python-gobject
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 644 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main python-gi amd64 3.0.3-2~oneiric1 [497 kB]
Get:2 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main python-gobject all 3.0.3-2~oneiric1 [148 kB]
Fetched 644 kB in 0s (677 kB/s)         
(Reading database ... 227897 files and directories currently installed.)
Preparing to replace python-gi 3.0.3-1~oneiric1 (using .../python-gi_3.0.3-2~oneiric1_amd64.deb) ...
Unpacking replacement python-gi ...
Preparing to replace python-gobject 3.0.3-1~oneiric1 (using .../python-gobject_3.0.3-2~oneiric1_all.deb) ...
Unpacking replacement python-gobject ...
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.25) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up python-gi (3.0.3-2~oneiric1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Setting up python-gobject (3.0.3-2~oneiric1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu64-W150HRM:~$ sudo apt-get install linux-headers-3.0.0-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gir1.2-nautilus-3.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.0.0-14
The following NEW packages will be installed
  linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 12.0 MB of archives.
After this operation, 98.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-headers-3.0.0-14 all 3.0.0-14.23 [11.2 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-headers-3.0.0-14-generic amd64 3.0.0-14.23 [857 kB]
Fetched 12.0 MB in 8s (1,399 kB/s)                                                                                  
Selecting previously deselected package linux-headers-3.0.0-14.
(Reading database ... 227897 files and directories currently installed.)
Unpacking linux-headers-3.0.0-14 (from .../linux-headers-3.0.0-14_3.0.0-14.23_all.deb) ...
Selecting previously deselected package linux-headers-3.0.0-14-generic.
Unpacking linux-headers-3.0.0-14-generic (from .../linux-headers-3.0.0-14-generic_3.0.0-14.23_amd64.deb) ...
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.25) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.0.0-14 (3.0.0-14.23) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Setting up linux-headers-3.0.0-14-generic (3.0.0-14.23) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu64-W150HRM:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nautilus-actions-extra
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.25) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu64-W150HRM:~$ sudo apt-get install linux-headers-3.0.0-15-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-15-generic is already the newest version.
linux-headers-3.0.0-15-generic set to manually installed.
The following package was automatically installed and is no longer required:
  gir1.2-nautilus-3.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.25) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu64-W150HRM:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nautilus-actions-extra
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.25) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's been happening ever since I used the Janitor in the new (and frankly, broken) version of Ubuntu Tweak a couple of weeks ago.

Can anybody help me!!

---

### Post by Basher101 on 2012-01-07
never use janitor. it is bad juju

to clean out leftbehinds do it with ```
sudo apt-get autoclean
```

otherwise i have little expirience with upgrades (as they tend to bug alot) beacuse i always make fresh installs.

hope someone will help you soon

---

### Post by greggc2006 on 2012-01-07
> **Basher101 said:**
> never use janitor. it is bad juju

to clean out leftbehinds do it with ```
sudo apt-get autoclean
```

otherwise i have little expirience with upgrades (as they tend to bug alot) beacuse i always make fresh installs.

hope someone will help you soon

Yeah, I use to use UbuTweak a lot but the new versions all borked up. I'll go back to apt-get ways! 

BTW, Love the profile pic' Bleachy awesomeness!

---

