---
title: "How to solve dependency issues when package is stated two times in dpkg status file?"
date: 2023-06-18
forum: Installation &amp; Upgrades
---

### Post by tata414151 on 2023-06-18
I upgraded from Ubuntu 18.04 to 20.04 and now want to reinstall `gnome-control-center` as it seems broken. Due to some issues I get the advice to fix broken packages via `apt --fix-broken install`. This fails with: 

```
dpkg: error processing archive /var/cache/apt/archives/libgcc1_1%3a10.3.0-1ubuntu1~20.04_amd64.deb (--unpack):
 package libgcc1:amd64 (1:10.3.0-1ubuntu1~20.04) with field 'Multi-Arch: no' is not co-installable with libgcc1 which has multiple installed instances
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a10.3.0-1ubuntu1~20.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

full output: [https://pastebin.com/jCySi2LQ](https://pastebin.com/jCySi2LQ)   

The solution suggested here: 
[https://askubuntu.com/a/485293](https://askubuntu.com/a/485293)
does not work, as the file `/var/lib/dpkg/status` looks somehow differently. 

The package `libgcc1` seems to exist two times in the `status` file (see excerpt below). 

How would a solution look like in this case? Thanks in advance!  :)


```
 Package: libgcc1
Status: deinstall ok config-files
Priority: optional
Section: libs
Installed-Size: 150
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: gcc-9 (9.1.0-2ubuntu2~14.04.2)
Version: 1:9.1.0-2ubuntu2~14.04.2
Config-Version: 1:9.1.0-2ubuntu2~14.04.2
Depends: gcc-9-base (= 9.1.0-2ubuntu2~14.04.2), libc6 (>= 2.2.4)
Pre-Depends: multiarch-support
Breaks: gcc-4.3 (<< 4.3.6-1), gcc-4.4 (<< 4.4.6-4), gcc-4.5 (<< 4.5.3-2)
Description: GCC support library
 Shared version of the support library, a library of internal subroutines
 that GCC uses to overcome shortcomings of particular machines, or
 special needs for some languages.
Homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>

---------------------------------------------
Package: libgcc1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 135
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: gcc-9 (9.1.0-2ubuntu2~14.04.2)
Version: 1:9.1.0-2ubuntu2~14.04.2
Depends: gcc-9-base (= 9.1.0-2ubuntu2~14.04.2), libc6 (>= 2.14)
Pre-Depends: multiarch-support
Breaks: gcc-4.3 (<< 4.3.6-1), gcc-4.4 (<< 4.4.6-4), gcc-4.5 (<< 4.5.3-2)
Description: GCC support library
 Shared version of the support library, a library of internal subroutines
 that GCC uses to overcome shortcomings of particular machines, or
 special needs for some languages.
Homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>

```

---

### Post by ian-weisser on 2023-06-18
Try `sudo apt autoremove` to clean up that huge list of orphaned packages.

---

### Post by tata414151 on 2023-06-18
Hi,

thanks for you answer.

After using the usual commands (also the one suggested by you), I ended up doing:

```

sudo apt-get install --reinstall multiarch-support libgcc1-
sudo apt-get install --reinstall multiarch-support libgcc1

```

That was the essential command to proceed further.

---

