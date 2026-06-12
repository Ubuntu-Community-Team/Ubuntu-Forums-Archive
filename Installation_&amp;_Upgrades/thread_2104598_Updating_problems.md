---
title: "Updating problems"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by Trekky0623 on 2013-01-13
Hi

I'm trying to run the Update Manager on Ubuntu 12.04

This is what happens:

```
The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
```

```
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.15-0ubuntu10) but 2.15-0ubuntu10.3 is installed
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10 is installed
           Depends: libc-dev-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.3 is installed

```

When I run apt-get install -f I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxfce4util-bin anthy-common anthy caribou libxfce4util4
  xfce-keyboard-shortcuts libxfce4util-common libxfce4ui-1-0 libanthy0 xfconf
  libxfconf-0-2 flashplugin-downloader libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 1 to remove and 310 not upgraded.
4 not fully installed or removed.
Need to get 0 B/3,940 kB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
Setting up tzdata (2012e-0ubuntu0.12.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Help is appreciated.

---

### Post by fantab on 2013-01-13
```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
```This usually means that another package manager is running. You have to close any other package manager your may be running.

Run following Command:

```
$ sudo apt-get remove --purge ttf-mscorefonts-installer
```Then run apt-get update.

---

