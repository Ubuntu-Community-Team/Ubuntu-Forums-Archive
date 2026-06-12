---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-11-11
forum: Installation &amp; Upgrades
---

### Post by in2survive on 2017-11-11
Hi guys, I'm trying to update Ubuntu 16.04, but I get the following (I believe due to my ignorance trying to clean the boot FS):

```
$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Fetched 306 kB in 0s (470 kB/s)
Reading package lists... Done
hans@PlexSever64:/media/BasVideos$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-96-generic : Depends: linux-image-4.4.0-96-generic but it is not installed
 linux-image-extra-4.4.0-98-generic : Depends: linux-image-4.4.0-98-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-98-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic
  linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83 linux-headers-4.4.0-83-generic
  linux-headers-4.4.0-87 linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-75-generic linux-image-4.4.0-78-generic
  linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic linux-image-4.4.0-89-generic linux-image-4.4.0-96-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-75-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-87-generic linux-image-extra-4.4.0-89-generic
  linux-image-extra-4.4.0-96-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-96-generic linux-image-4.4.0-98-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-96-generic linux-image-4.4.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
11 not fully installed or removed.
Need to get 0 B/43.9 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 466810 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-98-generic (4.4.0-98.121) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-98-generic' to '/boot/vmlinuz-4.4.0-98-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
Preparing to unpack .../linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-96-generic (4.4.0-96.119) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-96-generic' to '/boot/vmlinuz-4.4.0-96-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

```




Thanks

---

### Post by deadflowr on 2017-11-11
Try 
```
sudo apt-get autoremove
```
first.
If it errors, perhaps try removing a single older kernel first like
```
sudo dpkg --purge linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
```
then if that runs successfully try the autoremove command again.

Then if that runs successful, see if running the upgrade command works.

Since you have a bunch of older kernels autoremove wants to remove, it may take some time.

---

### Post by in2survive on 2017-11-12
Thanks, getting closer... auto remove didn't work... so:
```
$ sudo dpkg --purge linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
(Reading database ... 462148 files and directories currently installed.)
Removing linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-62-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-91-generic
Found initrd image: /boot/initrd.img-4.4.0-91-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
done
Purging configuration files for linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-62-generic
$

```

Then after running it again... then I had to do quite a few purges:
```
$ sudo dpkg --purge linux-image-extra-4.4.0-98-generic linux-image-4.4.0-93-generic  linux-image-extra-4.4.0-91-generic linux-image-extra-4.4.0-93-generic

```

But I still got an error:
```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-image-extra-4.4.0-91-generic
0 upgraded, 0 newly installed, 3 to remove and 5 not upgraded.
4 not fully installed or removed.
After this operation, 230 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 415147 files and directories currently installed.)
Removing linux-image-extra-4.4.0-91-generic (4.4.0-91.114) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-91-generic /boot/vmlinuz-4.4.0-91-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-91-generic /boot/vmlinuz-4.4.0-91-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-91-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-91-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-91-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-headers-4.4.0-93-generic (4.4.0-93.116) ...
dpkg: warning: while removing linux-headers-4.4.0-93-generic, directory '/lib/modules/4.4.0-93-generic' not empty so not removed
Removing linux-headers-4.4.0-93 (4.4.0-93.116) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-91-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

```


That last one, even after purge, it was still giving me the same error.

---

### Post by in2survive on 2017-11-12
Actually finally after 
```
$ sudo dpkg --purge   linux-image-4.4.0-91-generic  linux-image-extra-4.4.0-91-generic



```

Now it looks like this:
```
$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [653 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [618 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [544 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [518 kB]
Fetched 2,638 kB in 1s (2,376 kB/s)
Reading package lists... Done
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libegl1-mesa libgbm1 libgl1-mesa-dri libmirclient9 libwayland-egl1-mesa
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libegl1-mesa libgbm1 libgl1-mesa-dri libmirclient9 libwayland-egl1-mesa
0 upgraded, 0 newly installed, 0 to remove and **5 not upgraded.**
$

```
Not usre why the 5 not upgraded...
[COLOR=#DD4814]
[/COLOR][COLOR=#DD4814][[COLOR=#C61919]deadflowr[/COLOR]]("https://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000] [/COLOR][COLOR=#C61919][deadflowr]("https://ubuntuforums.org/member.php?u=1276577")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]

---

### Post by ian-weisser on 2017-11-12
Well done. Seems like you figured it out and fixed it a safe way.

The easiest way to prevent out-of-space errors in 16.04 and newer is either to enable unattended-upgrades or to monthly/quarterly run 'sudo apt upgrade'
You can safely mix the two methods , and even safely run both on the same day (not at the same time).

For the kept back packages, try 'sudo apt full-upgrade'

---

### Post by lisati on 2017-11-12
@in2survive: Using [noparse]```
 and 
``` tags works better than >  and [/noparse] for preserving formatting when posting terminal output.

---

### Post by in2survive on 2017-11-12
I think I'm all good after the:
```

[COLOR=#000000]sudo apt full-upgrade

```

Thanks guys!

PS: Using /code now! ;)[/COLOR]

---

