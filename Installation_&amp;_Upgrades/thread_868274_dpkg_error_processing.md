---
title: "dpkg error processing"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by MattiFIN on 2008-07-23
I have had lately problems upgrading with apt-get. Upgrading worked well until a week ago. Now Adept Updater could not commit changes. Any ideas?

matti@matti-laptop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
matti@matti-laptop:~$ sudo apt-get clean
matti@matti-laptop:~$ sudo dpkg --configure -a
matti@matti-laptop:~$ sudo apt-get upgrade && sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  language-pack-en language-pack-fi language-pack-kde-en language-pack-kde-fi libcamel1.2-11
  libebook1.2-9 libecal1.2-7 libedataserver1.2-9 libpango1.0-0 libpango1.0-common libpango1.0-dev
  libpcre3 linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic linux-image-2.6.24-19-generic
  linux-libc-dev ufw
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3MB of archives.
After this operation, 2384kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-en 1:8.04+20080708 [200kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-image-2.6.24-19-generic 2.6.24-19.36 [18.4MB]
Get:3 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-fi 1:8.04+20080708 [396kB]
Get:4 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-kde-en 1:8.04+20080708 [5374B]
Get:5 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-kde-fi 1:8.04+20080708 [223kB]
Get:6 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main ufw 0.16.2.2 [23.1kB]
Get:7 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libedataserver1.2-9 2.22.3-0ubuntu1 [114kB]
Get:8 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libcamel1.2-11 2.22.3-0ubuntu1 [304kB]
Get:9 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libebook1.2-9 2.22.3-0ubuntu1 [79.6kB]
Get:10 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libecal1.2-7 2.22.3-0ubuntu1 [244kB]
Get:11 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-dev 1.20.5-0ubuntu1 [348kB]
Get:12 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-common 1.20.5-0ubuntu1 [63.5kB]
Get:13 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-0 1.20.5-0ubuntu1 [284kB]
Get:14 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpcre3 7.4-1ubuntu2.1 [206kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19 2.6.24-19.36 [8131kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19-generic 2.6.24-19.36 [644kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-19.36 [696kB]
Fetched 30.3MB in 7min4s (71.5kB/s)
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20080708_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `python-apport': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20080708_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-07-23
Try:
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by MattiFIN on 2008-07-23
matti@matti-laptop:~$ sudo apt-get clean
matti@matti-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
The following packages will be REMOVED:
  linux-headers-2.6.24-18 linux-headers-2.6.24-18-generic
0 upgraded, 0 newly installed, 2 to remove and 17 not upgraded.
After this operation, 68.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing linux-headers-2.6.24-18-generic (--remove):
 failed in buffer_read(fd): files list for package `python-apport': Invalid argument
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by Pumalite on 2008-07-23
Post:
uname -a

---

### Post by MattiFIN on 2008-07-23
matti@matti-laptop:~$ uname -a
Linux matti-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by Pumalite on 2008-07-23
Go to /var/apt/cache/archives and remove them all by hand
(gksudo nautilus)
Then repeat the commands.

---

### Post by MattiFIN on 2008-07-23
root@matti-laptop:/var/cache/apt/archives# ls -la
total 44
drwxr-xr-x 3 root root 36864 2008-07-24 01:33 .
drwxr-xr-x 3 root root  4096 2008-07-24 01:36 ..
-rw-r----- 1 root root     0 2008-07-24 01:37 lock
drwxr-xr-x 2 root root  4096 2008-07-24 00:43 partial
root@matti-laptop:/var/cache/apt/archives/partial# ls -la
total 40
drwxr-xr-x 2 root root  4096 2008-07-24 00:43 .
drwxr-xr-x 3 root root 36864 2008-07-24 01:33 ..

Should I remove the lock file and the sub-folder?

---

### Post by MattiFIN on 2008-07-23
I removed the lock file and folder 'partial'.

matti@matti-laptop:~$ sudo apt-get clean
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to read /var/cache/apt/archives/partial/ - opendir (2 No such file or directory)
matti@matti-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
The following packages will be REMOVED:
  linux-headers-2.6.24-18 linux-headers-2.6.24-18-generic
0 upgraded, 0 newly installed, 2 to remove and 17 not upgraded.
E: Archive directory /var/cache/apt/archives/partial is missing.

Added folder 'partial' as root

matti@matti-laptop:~$ sudo apt-get clean
matti@matti-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
The following packages will be REMOVED:
  linux-headers-2.6.24-18 linux-headers-2.6.24-18-generic
0 upgraded, 0 newly installed, 2 to remove and 17 not upgraded.
After this operation, 68.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing linux-headers-2.6.24-18-generic (--remove):
 failed in buffer_read(fd): files list for package `python-apport': Invalid argument
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


matti@matti-laptop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
matti@matti-laptop:~$ sudo dpkg --configure -a
matti@matti-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
matti@matti-laptop:~$ sudo apt-get update
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy Release.gpg
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Packages [1178kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy Release.gpg
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy Release
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Sources
Err [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Packages
  404 Not Found
Err [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Sources
  404 Not Found
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 1178kB in 11s (102kB/s)
W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  rename failed, No such file or directory (/var/lib/apt/lists/partial/fi.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages.decomp -> /var/lib/apt/lists/fi.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages).

W: Failed to fetch [http://debian.websterwood.com/dists/hardy/main/binary-i386/Packages.gz](http://debian.websterwood.com/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://debian.websterwood.com/dists/hardy/main/source/Sources.gz](http://debian.websterwood.com/dists/hardy/main/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pumalite on 2008-07-23
You have a more severe problem in apt-get for which I have no solution. Maybe the Ubuntu staff can help you.

---

### Post by MattiFIN on 2008-07-23
Thanks Pumalite. I will wait for further assistance from others.

---

### Post by MattiFIN on 2008-07-23
I run forced fsck during the startup and it fixed some errors. Now the error message during apt-get has changed. Any ideas how to get apt-get working?


matti@matti-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
The following packages will be REMOVED:
  linux-headers-2.6.24-18 linux-headers-2.6.24-18-generic
0 upgraded, 0 newly installed, 2 to remove and 17 not upgraded.
After this operation, 68.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `python-apport' missing, assuming package has no files currently installed.
dpkg: error processing linux-headers-2.6.24-18-generic (--remove):
 unable to open files list file for package `x11proto-fixes-dev': No such device or address
E: Sub-process /usr/bin/dpkg exited unexpectedly
matti@matti-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-18-generic linux-headers-2.6.24-18
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
matti@matti-laptop:~$ sudo apt-get update
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy Release.gpg
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy Release.gpg
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy Release
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Packages
Ign [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Sources
Err [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Packages
  404 Not Found
Err [http://debian.websterwood.com](http://debian.websterwood.com) hardy/main Sources
  404 Not Found
W: Failed to fetch [http://debian.websterwood.com/dists/hardy/main/binary-i386/Packages.gz](http://debian.websterwood.com/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://debian.websterwood.com/dists/hardy/main/source/Sources.gz](http://debian.websterwood.com/dists/hardy/main/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
matti@matti-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  language-pack-en language-pack-fi language-pack-kde-en language-pack-kde-fi libcamel1.2-11
  libebook1.2-9 libecal1.2-7 libedataserver1.2-9 libpango1.0-0 libpango1.0-common libpango1.0-dev
  libpcre3 linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic linux-image-2.6.24-19-generic
  linux-libc-dev ufw
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3MB of archives.
After this operation, 2384kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-en 1:8.04+20080708 [200kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-image-2.6.24-19-generic 2.6.24-19.36 [18.4MB]
Get:3 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-fi 1:8.04+20080708 [396kB]
Get:4 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-kde-en 1:8.04+20080708 [5374B]
Get:5 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main language-pack-kde-fi 1:8.04+20080708 [223kB]
Get:6 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main ufw 0.16.2.2 [23.1kB]
Get:7 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libedataserver1.2-9 2.22.3-0ubuntu1 [114kB]
Get:8 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libcamel1.2-11 2.22.3-0ubuntu1 [304kB]
Get:9 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libebook1.2-9 2.22.3-0ubuntu1 [79.6kB]
Get:10 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libecal1.2-7 2.22.3-0ubuntu1 [244kB]
Get:11 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-dev 1.20.5-0ubuntu1 [348kB]
Get:12 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-common 1.20.5-0ubuntu1 [63.5kB]
Get:13 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpango1.0-0 1.20.5-0ubuntu1 [284kB]
Get:14 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main libpcre3 7.4-1ubuntu2.1 [206kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19 2.6.24-19.36 [8131kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19-generic 2.6.24-19.36 [644kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-19.36 [696kB]
Fetched 30.3MB in 7min4s (71.4kB/s)
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `python-apport' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20080708_all.deb (--unpack):
 unable to open files list file for package `x11proto-fixes-dev': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20080708_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ccomincini on 2011-06-15
I've found a solution for a similar problem here:
[URL="http://www.debian-administration.org/articles/251"]http://www.debian-administration.org/articles/251
[/URL]
maybe it chan help.

Bye
Carlo

---

