---
title: "Apt-Get and Broken Packages"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by quicky2g on 2011-10-23
I've installed Ubuntu Server 11.10 two times now and had the same issue. I'll install a few packages and eventually apt gets caught up on a package installation and only half installs it. I can't complete or force the installation or removal...so I can't upgrade or install new packages. The first time I installed 11.10, apt got caught on an snmp package installation. Now it got caught on squid. I ran "dpkg --remove --force-remove-reinstreq squid" and apt seemed to get rid of it's knowledge of squid but I still can't install new packages. I'm stuck on an installation of curl now. Here's my output during installation...

```

user@server:~$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libcurl3
The following NEW packages will be installed:
  curl libcurl3
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/364 kB of archives.
After this operation, 995 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libcurl3.
(Reading database ... 69381 files and directories currently installed.)
Unpacking libcurl3 (from .../libcurl3_7.21.6-3ubuntu3_amd64.deb) ...
Selecting previously deselected package curl.
Unpacking curl (from .../curl_7.21.6-3ubuntu3_amd64.deb) ...
Setting up man-db (2.6.0.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/man-db.postinst): Permission denied
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libcurl3 (7.21.6-3ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/libcurl3:amd64.postinst): Permission denied
dpkg: error processing libcurl3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of curl:
 curl depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not configured yet.
dpkg: error processing curl (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 man-db
 libcurl3
 curl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any help is greatly appreciated!

---

### Post by zvacet on 2011-10-24
```
sudo dpkg --configure -a
```

---

### Post by quicky2g on 2011-10-25
Still having issues after trying that command...

```

user@server:~$ sudo dpkg --configure -a
Setting up man-db (2.6.0.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/man-db.postinst): Permission denied
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libcurl3 (7.21.6-3ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/libcurl3:amd64.postinst): Permission denied
dpkg: error processing libcurl3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of curl:
 curl depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not configured yet.
dpkg: error processing curl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 libcurl3
 curl

```

---

### Post by matt_symes on 2011-10-25
Hi

Can you post the output of these two commands
```

ls -l /var/lib/dpkg/info/man-db.postinst
ls -l /var/lib/dpkg/info/libcurl3:amd64.postinst
```That is a small L after each ls.

Kind regards

---

### Post by quicky2g on 2011-10-29
```

user@server:~$ ls -l /var/lib/dpkg/info/man-db.postinst
-rwxr-xr-x 1 root root 3827 2011-07-27 07:33 /var/lib/dpkg/info/man-db.postinst

``````

user@server:~$ ls -l /var/lib/dpkg/info/libcurl3:amd64.postinst
-rwxr-xr-x 1 root root 135 2011-09-15 16:49 /var/lib/dpkg/info/libcurl3:amd64.postinst

```

---

### Post by quicky2g on 2011-11-05
Has anyone had a chance to take a look at this?...or any suggestions? Thanks in advance.

---

### Post by matt_symes on 2011-11-06
Hi

The two files being called have the correct permissions. I don't think your 'permission denied' error is coming directly from them or any files they might call (as they are lightly to call different files).

Can you post the output of

```
ls -l /var/lib/dpkg/
```Kind regards

---

### Post by raja.genupula on 2011-11-06
> **quicky2g said:**
> Still having issues after trying that command...

```

user@server:~$ sudo dpkg --configure -a
Setting up man-db (2.6.0.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/man-db.postinst): Permission denied
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libcurl3 (7.21.6-3ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/libcurl3:amd64.postinst): Permission denied
dpkg: error processing libcurl3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of curl:
 curl depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not configured yet.
dpkg: error processing curl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 libcurl3
 curl

```

Hi do this 
ope terminal and type this 
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install curl
```

if its not done then get libcurl3 pkg from ubuntu packages(googling can help you ) and install it.

All the best.

---

### Post by quicky2g on 2011-11-09
```

user@server:~$ ls -l /var/lib/dpkg/
total 1816
drwxr-xr-x 2 root root   4096 2011-10-21 06:20 alternatives
-rw-r--r-- 1 root root 418385 2011-10-29 13:14 available
-rw-r--r-- 1 root root 418596 2011-10-23 23:10 available-old
-rw-r--r-- 1 root root      8 2011-10-21 05:54 cmethopt
-rw-r--r-- 1 root root    268 2011-10-21 06:15 diversions
-rw-r--r-- 1 root root    337 2011-10-21 06:15 diversions-old
-rw-r--r-- 1 root root      1 2011-10-21 05:53 format
drwxr-xr-x 2 root root  86016 2011-10-23 23:10 info
-rw-r----- 1 root root      0 2011-10-29 13:14 lock
drwxr-xr-x 2 root root   4096 2011-10-06 04:04 parts
-rw-r--r-- 1 root root    105 2011-10-21 06:20 statoverride
-rw-r--r-- 1 root root     70 2011-10-21 06:14 statoverride-old
-rw-r--r-- 1 root root 441389 2011-10-29 13:14 status
-rw-r--r-- 1 root root 441146 2011-10-25 03:54 status-old
drwxr-xr-x 2 root root   4096 2011-10-21 06:53 triggers
drwxr-xr-x 2 root root   4096 2011-10-29 13:14 updates

```

---

### Post by quicky2g on 2011-11-09
Forcing the install doesn't seem to help either. I'm sure I could manually install files but why do I keep having this problem time and time again when trying to install different packages? I have other versions of Ubuntu server running elsewhere without ever running into this problem.

```

user@server:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
9 not fully installed or removed.
Need to get 56.6 kB/633 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libpam0g amd64 1.1.3-2ubuntu1 [56.6 kB]
Fetched 56.6 kB in 0s (101 kB/s)
Preconfiguring packages ...
(Reading database ... 69413 files and directories currently installed.)
Preparing to replace libpam0g 1.1.3-2ubuntu1 (using .../libpam0g_1.1.3-2ubuntu1_amd64.deb) ...
Unpacking replacement libpam0g ...
dpkg (subprocess): unable to execute old post-removal script (/var/lib/dpkg/info/libpam0g:amd64.postrm): Permission denied
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error processing /var/cache/apt/archives/libpam0g_1.1.3-2ubuntu1_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libpam0g_1.1.3-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@server:~$
user@server:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://security.ubuntu.com oneiric-security/main Sources
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates Release
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports Release
Hit http://us.archive.ubuntu.com oneiric/main Sources
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Reading package lists... Done
user@server:~$
user@server:~$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
curl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
9 not fully installed or removed.
Need to get 0 B/633 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 69413 files and directories currently installed.)
Preparing to replace libpam0g 1.1.3-2ubuntu1 (using .../libpam0g_1.1.3-2ubuntu1_amd64.deb) ...
Unpacking replacement libpam0g ...
dpkg (subprocess): unable to execute old post-removal script (/var/lib/dpkg/info/libpam0g:amd64.postrm): Permission denied
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error processing /var/cache/apt/archives/libpam0g_1.1.3-2ubuntu1_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libpam0g_1.1.3-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TomicaH on 2012-07-07
Hey,

This is really an old thread, but since it wasn't resolved, I may post a possible solution here :)
I've run into the same thing on my desktop today.

I was moving whole installation from regular SATA to SSD drive, and have set up a /var on separate partition, outside of that SSD drive. Since I was setting up everything automatically and was pretty tired when doing it, I've made a mistake with creating a mount point for /var partition, and have set noexec option for it.

IF anyone is still having this problem, please check your mount point for /var, if it's on separate partition, or for / if var is there. Make sure that you don't have noexec set there, like I did.

Wrong setting:
```
tomica@mish:~$ sudo mount|grep var
/dev/sdb1 on /var type ext4 (rw,nosuid,nodev,noexec,noatime)
```

Good one:
```
tomica@mish:~$ sudo mount|grep var
/dev/sdb1 on /var type ext4 (rw,nosuid,nodev,noatime)
```

If you ahve /var, or /, mounted noexec, open /etc/fstab, change that option and just remount /var:

```
sudo mount -o remount /var
```

---

