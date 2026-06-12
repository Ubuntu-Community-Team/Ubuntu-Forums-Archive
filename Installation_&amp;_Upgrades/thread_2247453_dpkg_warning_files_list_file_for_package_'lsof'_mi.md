---
title: "dpkg: warning: files list file for package 'lsof' missing; assuming package has no fi"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by neitono on 2014-10-08
can some one help me with this im srsly stuck here and im a n00b when it comes to linux i used sudo apt-get upgrade and i got this. [COLOR=black]```
[/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk bsdutils evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts file
  flashplugin-installer fonts-droid gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-gudev-1.0 language-selector-common
  language-selector-gnome libblkid1 libcamel-1.2-45 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libgudev-1.0-0 libmagic1 libmount1
  libpam-systemd libsystemd-daemon0 libsystemd-journal0 libsystemd-login0
  libudev1 libunity-control-center1 libuuid1 libvncserver0 man-db mount
  python-apport python-problem-report python3-apport python3-problem-report
  systemd-services udev unity-control-center util-linux uuid-runtime
46 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 886 kB/9,108 kB of archives.
After this operation, 127 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main bsdutils i386 1:2.20.1-5.1ubuntu20.2 [34.0 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main man-db i386 2.6.7.1-1ubuntu1 [852 kB]
Fetched 886 kB in 1s (572 kB/s) 
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: files list file for package 'lsof' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libitm1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgomp1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasyncns0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pulseaudio' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `x11-xfs-utils': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)
```[COLOR=black][FONT=Consolas] [/FONT][/COLOR]&#8203;:-({|=

---

### Post by ubfan1 on 2014-10-08
Did you run     sudo apt-get update       first?  That's necessary before the upgrade.

---

### Post by ian-weisser on 2014-10-08
The error messages seem to indicate a corruption of the dpkg database files in /var/lib/dpkg/info .
That's rather rare. And serious.

Do you have _any_ other 'file not found' or 'missing data' errors?
Possible causes are numerous, but can include a dying hard drive.

Back up your data, in case the problem is due to hardware or requires a reinstall.

That particular database is filled when you install a package, so one solution is to reinstall the affected packages.
```
sudo apt-get install --reinstall lsof libitm1:i386 libgomp1:i386 libasyncns0:i386 pulseaudio x11-xfs-utils
```
You may need to make a few tries, as new error messages uncover more damaged files to add to the list.

---

### Post by BuntuSeriously on 2014-12-24
```
dpkg: warning: files list file for package `x' missing; assuming package has no files currently installed
```This type of thing can also be brought about by a /var/lib/dpkg/info/format file which may need to be regenerated afresh by dpkg.```
sudo rm -f /var/lib/dpkg/info/format
```...then```
sudo dpkg --configure -a
```YMMV ;)

Cheers!

---

