---
title: "Broken Package Fix"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by tianhaupt on 2009-12-11
Hi,
  I'm fairly new to Ubuntu and have a "broken" package that occurred after an update.  I've tried reinstall using synaptic package manager but it stops without completing with this message in details:
dpk8:parse error, in file '/var/lib/dpkg/status' near line 19516 package 'initsscipts' missing version. 
The package that won't install is upstart 0-6.3-10 I have no idea where to go next to repair it.  Thanks

---

### Post by Shazaam on 2009-12-12
Three commands to try in terminal...
```
sudo apt-get update
```
This code will try to configure any unconfigured packages-
```
sudo dpkg --configure -a
```
This one should fix your broken package(s)-
```
sudo apt-get install -f
```

---

### Post by tianhaupt on 2009-12-12
Shazaam,
 
I tried your code in terminal, see below.  It still did not update properly.  Looks like there's an issue with initscripts. Marty

jeh@jeh-desktop:~$ sudo apt-get update

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg

Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                     

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                     

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                        

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                    

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources              

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources

Reading package lists... Done

jeh@jeh-desktop:~$ sudo apt-get install -f

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Correcting dependencies... Done

The following packages were automatically installed and are no longer required:

  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic

Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:

  initscripts

The following NEW packages will be installed:

  initscripts

0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.

5 not fully installed or removed.

Need to get 0B/72.5kB of archives.

After this operation, 340kB of additional disk space will be used.

Do you want to continue [Y/n]? y

dpkg: parse error, in file '/var/lib/dpkg/status' near line 19516 package 'initscripts':

 missing version

E: Sub-process /usr/bin/dpkg returned an error code (2)

jeh@jeh-desktop:~$ apt-get autoremove

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

jeh@jeh-desktop:~$

---

### Post by phillw on 2009-12-12
Hi, as always ... there's a hint ...

> jeh@jeh-desktop:~$ apt-get autoremove

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


spot the missing sudo !!

```
sudo apt-get autoremove
```

Yeah, we all do it from time to time - maddening isn't it ;-)

Regards,

Phill

---

### Post by Shazaam on 2009-12-12
Your dpkg/status file is probably corrupted. Two things you can try; your choice...

A-
1. Open nautilus as root (be careful)-
```
gksudo nautilus
```
2. Go to /var/lib/dpkg
3. Rename status to status.bak
4. Rename status-old to status
5. Run apt-get update
6. Install initscripts




B-
1. Open nautilus as root (again, be careful)-
```
gksudo nautilus
```
2. Go to /var/lib/dpkg/status-old
3. Remame the file by adding .bak in place of -old (this makes sure it doesn't get auto-deleted)
4. Close nautilus
5. Open the current file for editing (as root)-
```
gksudo gedit /var/lib/dpkg/status
```
6. Go to Search>Find, enter initscripts in the search box 
7. Highlight the initscripts section (Package:initscripts) and delete it
My initscripts section-
```
Package: initscripts
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 332
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: sysvinit
Version: 2.87dsf-4ubuntu12
Replaces: libc0.1, libc0.3, libc6, libc6.1
Depends: libc6 (>= 2.4), mount (>= 2.11x-1), debianutils (>= 2.13.1), lsb-base (>= 3.2-14), sysvinit-utils (>= 2.86.ds1-39), sysv-rc | file-rc, passwd
Recommends: psmisc, e2fsprogs
Breaks: hostname (<< 2.95ubuntu1~boot2), rsyslog (<< 4.2.0-2ubuntu3~boot1), udev (<< 146-2~boot6), upstart (<< 0.6.3-2~boot4)
Conflicts: libdevmapper1.02.1 (<< 2:1.02.24-1)
Conffiles:
 /etc/init.d/bootlogd 6e90878c898804bf9059f8a304faed5d
 /etc/init.d/stop-bootlogd e1a190ec1150ff0c1514eb318be9e227
 /etc/init.d/stop-bootlogd-single 1046585487345dd2d5d4b2841fb4a75b
 /etc/init.d/halt 6ae1b3b1b8198567a5e32116077f12a2
 /etc/init.d/killprocs 5e404d35091fab6c4889302736ed4602
 /etc/init.d/ondemand cc2a79a545967eec1170dc2bb44468e0
 /etc/init.d/rc.local 2964c1446c6453cdde4213eede97ac38
 /etc/init.d/reboot 1b9db1ef7bfd79b128ef85d5065721a6
 /etc/init.d/sendsigs 80f76e4cc5a0b2860507a5ffb7e107b1
 /etc/init.d/single dc13cb373c5c098a8fb95424701373e3
 /etc/init.d/umountfs 842eba3cdd65c66a424f80a53f87d704
 /etc/init.d/umountnfs.sh b824a44ff24087eb2bf6780db7dfd9dc
 /etc/init.d/umountroot aa9aa9db438cc99f76b065827971ff42
 /etc/init.d/urandom d0385e199d51b19181b77dc55211ac02
 /etc/default/bootlogd 70a108da715299a6e33470eb450669fb
 /etc/default/devpts fc857c5ac5fb84d80720ed4d1c624f6e
 /etc/default/halt 18d9844cf8ca8608e2a559a4555e593a
 /etc/default/tmpfs d959a98cfb571cd7fdfb36bbb3d0a5c8
Description: scripts for initializing and shutting down the system
 The scripts in this package initialize a standard Debian
 GNU/Linux system at boot time and shut it down at halt or
 reboot time.
Homepage: http://freshmeat.net/projects/sysvinit/
Original-Maintainer: Debian sysvinit maintainers <pkg-sysvinit-devel@lists.alioth.debian.org>

```
8. Go to File>Save. This should also back up the original file and give the backup file the filename of status~
9. Run apt-get update; then you should be able to install initscripts again

+1 to what phillw said (thanks phillw).

---

### Post by tianhaupt on 2009-12-12
Shazzam,
 
I took option 1 renaming the status-old to status in file in /var/lib/dpkg and then updating the system.  It worked.  My system is now up to date.  Many, many thanks.  Marty

---

