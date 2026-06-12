---
title: "Kernel not upgrading"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2016-09-11
Hi:

I'm running Lubuntu 16.04.1 on a number of Thinkpad X-40 systems; one of them, for some odd reason, upgrades well except for the kernel: it's still running 3.13.0.9. It's downloaded as late as 4.4.0-39.66, but won't install any of the 4-series kernels that have been downloaded. 

Is this a bug or a feature?

Thanks,

Bill

---

### Post by Impavidus on 2016-09-11
No, that's not a feature. I can imagine three possible reasons. Maybe the package manager somehow failes to install the new kernels, for example because you don't have enough disk space available. Or update-grub failes to run. Or you are dual booting with another Linux, which is in control of grub and you didn't boot into the other Linux to run update-grub.

I think you upgraded this system from 14.04, right?

Edit:
Do you dual boot with another Linux? Maybe another Ubuntu version?

Run```
sudo update-grub
```What is the output? Does it show the more recent kernels? It should list the detected kernels.

Run```
dpkg -l | grep linux-image
```What is the output? It should show you the installed kernel packages.

---

### Post by wjbmd48 on 2016-09-12
Thanks so much!!

No, it's not a dual-boot, but is an upgrade from 14.04.1.

Here are the outputs:

bill@bill-ThinkPad-X40:~$ sudo update-grub
[sudo] password for bill: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.13.0-39-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done


bill@bill-ThinkPad-X40:~$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-39-generic                3.13.0-39.66                               i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic          3.13.0-39.66                               i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic          3.13.0-43.72                               i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic           4.4.0-31.50                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP

---

### Post by Impavidus on 2016-09-12
linux-image-extra-4.4.0-31-generic is reported as removed, with remaining configuration. That's strange. It's part of an older kernel version for Xenial. The metapackages that are supposed to pull in new kernel versions aren't there either.

Try this to install the metapackage:```
sudo apt update
sudo apt install linux-generic
```It should pull in some more packages and make sure you'll get the upgrades when they become available.

---

### Post by wjbmd48 on 2016-09-12
OK, here's what I get when I ran the two commands you recommended.

The punch lines are the last 4, to save you the trouble:

```
Unpacking linux-generic (4.4.0.36.38) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


which is also what I see when I try to install the linux-image kernels in synaptic.

Any ideas?

Thanks!

Bill

 


```
bill@bill-ThinkPad-X40:~$ sudo apt update
Ign:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease                     
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Ign:3 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release            
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Hit:7 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release                 
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]     
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Sources [187 kB]   
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [92.8 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [378 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [321 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [111 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main Sources [38.7 kB] 
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe Sources [9,332 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [134 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [57.0 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [41.4 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe Translation-en [25.1 kB]
Fetched 1,586 kB in 2min 20s (11.3 kB/s)                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.
bill@bill-ThinkPad-X40:~$ sudo apt install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  baloo-kf5 catdoc cpp-4.8 dolphin fonts-lato gstreamer0.10-pulseaudio kfind
  kinit kio kubuntu-debug-installer libamd2.3.1 libatk-wrapper-java
  libatk-wrapper-java-jni libbaloocore4 libbaloofiles4 libbaloowidgets4
  libbalooxapian4 libbasicusageenvironment0 libbit-vector-perl
  libboost-date-time1.54.0 libboost-filesystem1.54.0 libboost-regex1.54.0
  libboost-system1.54.0 libcairomm-1.0-1v5 libcamd2.3.1 libcarp-clan-perl
  libccolamd2.8.0 libcdr-0.0-0 libcholmod2.1.2 libcloog-isl4 libcmis-0.4-4
  libcolamd2.8.0 libcolord1 libdate-calc-perl libdate-calc-xs-perl
  libdirac-encoder0 libdolphinvcs5 libdvbpsi8 libegl1-mesa-drivers libelfg0
  libepub0 libetpan15 libexiv2-12 libgconf2-4 libgegl-0.2-0 libgif4 libglamor0
  libgnome-desktop-3-7 libgphoto2-port10 libgraphicsmagick++3
  libgraphicsmagick3 libgroupsock1 libhdb9-heimdal libidl-common libilmbase6
  libisl10 libjavascriptcoregtk-1.0-0 libkactivities-models1 libkdc2-heimdal
  libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets5
  libkf5bookmarks-data libkf5bookmarks5 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkf5gpgmepp5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kiofilewidgets5 libkf5kiontlm5
  libkf5newstuff-data libkf5newstuff5 libkf5parts-data libkf5parts-plugins
  libkf5parts5 libkf5solid5 libkf5solid5-data libkf5wallet-bin
  libkf5wallet-data libkf5wallet5 libkfilemetadata4 libkidletime4
  libkonq-common libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a
  libkwalletbackend5-5 liblept4 liblivemedia23 libllvm3.4 liblmdb0
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmspub-0.0-0
  libmysqlclient18 libnepomukcleaner4 libnepomukcore4abi1 libntdb1
  libobrender29 libopenexr6 libopenvg1-mesa liborcus-0.6-0
  libparted-fs-resize0 libpoppler-qt4-4 libpoppler-qt5-1 libpoppler44 libqapt3
  libqapt3-runtime libqjson0 libqmobipocket1 libqpdf13 libqt5test5
  libqtwebkit-qmlwebkitplugin libreadonly-xs-perl libruby1.9.1 libruby2.3
  libservlet3.0-java libsigc++-2.0-0v5 libsoprano4 libssh-4 libtar0
  libtinyxml2.6.2 libumfpack5.6.2 libusageenvironment1 libvirtodbc0
  libvisio-0.0-0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwxbase2.8-0
  libwxgtk2.8-0 libxcb-util0 libzeitgeist-1.0-1 libzip2 libzip4
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic lubuntu-artwork-14-04
  nepomuk-core-data phonon-backend-gstreamer1.0 python-dbus-dev python-gst0.10
  python-imaging python-ntdb python-pexpect python-pil python-ptyprocess
  python-renderpm python-reportlab python-reportlab-accel python-support
  python-webkit qapt-batch rake rhythmbox-mozilla ruby ruby-did-you-mean
  ruby-minitest ruby-net-telnet ruby-power-assert ruby-test-unit ruby1.9.1
  ruby2.3 rubygems-integration shared-desktop-ontologies soprano-daemon
  syslinux-themes-debian syslinux-themes-debian-wheezy ttf-dejavu-core
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  xfonts-mathml
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-36-generic linux-image-extra-4.4.0-36-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-image-4.4.0-36-generic
  linux-image-extra-4.4.0-36-generic linux-image-generic
0 upgraded, 4 newly installed, 0 to remove and 18 not upgraded.
Need to get 56.1 MB of archives.
After this operation, 161 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-4.4.0-36-generic i386 4.4.0-36.55 [17.5 MB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-extra-4.4.0-36-generic i386 4.4.0-36.55 [38.6 MB]
67% [2 linux-image-extra-4.4.0-36-generic 25.7 MB/38.6 MB 67%]                 
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-generic i386 4.4.0.36.38 [2,360 B]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-generic i386 4.4.0.36.38 [1,784 B]
Fetched 56.1 MB in 1h 4min 10s (14.6 kB/s)                                     
Selecting previously unselected package linux-image-4.4.0-36-generic.
(Reading database ... 724918 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb ...
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Selecting previously unselected package linux-image-extra-4.4.0-36-generic.
Preparing to unpack .../linux-image-extra-4.4.0-36-generic_4.4.0-36.55_i386.deb ...
Unpacking linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_4.4.0.36.38_i386.deb ...
Unpacking linux-image-generic (4.4.0.36.38) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_4.4.0.36.38_i386.deb ...
Unpacking linux-generic (4.4.0.36.38) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2016-09-12
The real punchlines are higher up.

> **wjbmd48 said:**
> 
The following packages were automatically installed and are no longer required:
[...very long list...]
Use '**sudo apt autoremove**' to remove them.


Preparing to unpack .../linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb ...
**This kernel does not support a non-PAE CPU.**
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-36-generic_4.4.0-36.55_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1

If you are not sure what the PAE error message means, then see [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by wjbmd48 on 2016-09-13
Ah, OK, I was wondering about that. The X40 comes in a number of flavors, from 1.0 GHz to 1.6, and the 1.0-1.4 versions indeed require a force PAE on direct install.

The link you provided is for force PAE on install, which I'm familiar with (and which is how I did the 14.04 install on this system.)

So is there a way to force PAE on upgrade/install of a 4.0 kernel with synaptic, or am I looking at reinstalling the operating system?

Thanks,

Bill

---

