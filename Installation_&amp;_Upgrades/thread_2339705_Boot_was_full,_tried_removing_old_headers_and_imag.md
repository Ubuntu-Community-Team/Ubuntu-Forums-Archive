---
title: "Boot was full, tried removing old headers and images. Ended up with errors."
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by airplanesimen on 2016-10-12
```
Fetched 1,918 kB in 8s (214 kB/s)Reading package lists... Done
root@serverhost:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-3.19.0-64-generic (3.19.0-64.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.19.0-65-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-64-generic /boot/vmlinuz-3.19.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-64-generic /boot/vmlinuz-3.19.0-64-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-64-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-64-generic.postinst line 1025.
dpkg: error processing package linux-image-3.19.0-64-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.19.0-65-generic (3.19.0-65.73) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.19.0-64-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-65-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-65-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-65-generic.postinst line 1025.
dpkg: error processing package linux-image-3.19.0-65-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-65-generic:
 linux-image-extra-3.19.0-65-generic depends on linux-image-3.19.0-65-generic; however:
  Package linux-image-3.19.0-65-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.19.0-65-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.19.0-65-generic; however:
  Package linux-image-3.19.0-65-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.19.0-65-generic; however:
  Package linux-image-extra-3.19.0-65-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.19.0.65.63); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependeNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                  No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                                                                                                ncy problems - leaving unconfigured
Setting up linux-image-extra-3.19.0-61-generic (3.19.0-61.69) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-61-generic /boot/vmlinuz-3.19.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-61-generic /boot/vmlinuz-3.19.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-61-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-61-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-61-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-64-generic:No apport report written because MaxReports is reached already


 linux-image-extra-3.19.0-64-generic depends on linux-image-3.19.0-64-generic; however:
  Package linux-image-3.19.0-64-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.19.0-64-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.19.0-64-generic
 linux-image-3.19.0-65-generic
 linux-image-extra-3.19.0-65-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.19.0-61-generic
 linux-image-extra-3.19.0-64-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@serverhost:~#



```



This is what i get upon doing apt-get upgrade.

I was trying to manually remove some old headers and images, which i see now was stupid. I shouldn't do things I'm not sure how to do, and it's crucial i get my server stable again. It's on ubuntu server (I think).


More info:

```
root@serverhost:~# lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid

```
```



root@serverhost:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            484M     0  484M   0% /dev
tmpfs            99M   13M   87M  13% /run
/dev/xvda2       99G   11G   83G  12% /
tmpfs           495M     0  495M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           495M     0  495M   0% /sys/fs/cgroup
/dev/xvda1      180M  160M  7.4M  96% /boot
tmpfs            99M     0   99M   0% /run/user/0
root@serverhost:~#



```


I'm averagely familiar with Ubuntu as I'm an old user, however i had periods where i didn't use it at all. I'm hosting several game servers on this client, and would like it up 100% of the time. I need to install a package named "vsftpd" in order to manage clients who's connecting to specific directories, but this is stopping me.

Any help would be awesome
Also, sorry about my name here on the forum. It's old..
Simen

---

### Post by Impavidus on 2016-10-12
You can use```
dpkg --list | grep -E 'linux-(headers|image)'
```to get a list of the installed kernel and header packages, then use dpkg to uninstall old versions. dpkg is a lower level tool that should still work when apt-get doesn't.```
dpkg --purge first-package second-package
```That should give you some free disk space.

However, I see you run Ubuntu 15.04. That release is no longer supported. You should move on to Ubuntu 16.04 LTS. As 15.10 is dead too, the best way is a fresh install of 16.04 LTS, which will be supported until april 2021.

Also, there's no need for sudo when you're root already.

---

### Post by airplanesimen on 2016-10-12
Thanks for reply, I'll give dpkg a try, and doing sudo is by an old habit i have.

I'll report back here when I'm done and to see if it helps.

---

### Post by airplanesimen on 2016-10-12
Okay, purging using dpkg was genius. Previous attempt i did was by using apt-get, but apt-get again had a problem and so on.

I thank you for the help, and I'll consider upgrading my version to something more recent.

**Solved**

---

