---
title: "Ubuntu software centre in error"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by herveb on 2010-05-13
Hi

I am trying to install a few package, and I keep getting this kind of error. Some of the package are functional despite it though

```
installArchives() failed: Selecting previously deselected package libmp3lame0.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 154054 files and directories currently installed.)
Unpacking libmp3lame0 (from .../libmp3lame0_3.98.2+debian-0ubuntu3_i386.deb) ...
Selecting previously deselected package lame.
Unpacking lame (from .../lame_3.98.2+debian-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
Setting up libmp3lame0 (3.98.2+debian-0ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up lame (3.98.2+debian-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by zvacet on 2010-05-13
```
sudo dpkg --configure -a
```

---

### Post by herveb on 2010-05-14
thanks - here it goes

```
boisson@boisson-laptop:~$ sudo dpkg --configure -a
[sudo] password for boisson: 
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish

```

---

### Post by herveb on 2010-05-14
I don't know if this is linked, I suppose it might, but when trying to get the drivers for my nVidia (using System>administration>hardware drivers) I get the following in a message box:

```
 SystemError: install archives() failed
```

Also when trying to install software through the terminal I get something like

```
Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

here is the total history - I also did a sudo apt-get update before, which seems to be OK

```
boisson@boisson-laptop:~$ sudo apt-get install inkscape
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmagick++2 libwmf-bin perlmagick python-lxml python-renderpm python-reportlab python-reportlab-accel
  python-uniconvertor
Suggested packages:
  dia dia-gnome ruby libsvg-perl libxml-xql-perl skencil pstoedit imagemagick-doc python-lxml-dbg
  python-renderpm-dbg python-egenix-mxtexttools python-reportlab-doc python-uniconvertor-dbg
The following NEW packages will be installed
  inkscape libmagick++2 libwmf-bin perlmagick python-lxml python-renderpm python-reportlab python-reportlab-accel
  python-uniconvertor
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 22.1MB of archives.
After this operation, 95.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libmagick++2 7:6.5.7.8-1ubuntu1 [207kB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/main inkscape 0.47.0-2ubuntu2 [20.0MB]
Get: 3 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libwmf-bin 0.2.8.4-6.1ubuntu2 [16.7kB]                      
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid/main perlmagick 7:6.5.7.8-1ubuntu1 [210kB]                       
Get: 5 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-lxml 2.2.4-1 [530kB]                                 
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-renderpm 2.4-1 [34.2kB]                              
Get: 7 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-reportlab 2.4-1 [543kB]                              
Get: 8 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-reportlab-accel 2.4-1 [35.3kB]                       
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-uniconvertor 1.1.4-1build1 [443kB]                   
Fetched 22.1MB in 1min 31s (240kB/s)                                                                               
Selecting previously deselected package libmagick++2.
(Reading database ... 155181 files and directories currently installed.)
Unpacking libmagick++2 (from .../libmagick++2_7%3a6.5.7.8-1ubuntu1_i386.deb) ...
Selecting previously deselected package inkscape.
Unpacking inkscape (from .../inkscape_0.47.0-2ubuntu2_i386.deb) ...
Selecting previously deselected package libwmf-bin.
Unpacking libwmf-bin (from .../libwmf-bin_0.2.8.4-6.1ubuntu2_i386.deb) ...
Selecting previously deselected package perlmagick.
Unpacking perlmagick (from .../perlmagick_7%3a6.5.7.8-1ubuntu1_i386.deb) ...
Selecting previously deselected package python-lxml.
Unpacking python-lxml (from .../python-lxml_2.2.4-1_i386.deb) ...
Selecting previously deselected package python-renderpm.
Unpacking python-renderpm (from .../python-renderpm_2.4-1_i386.deb) ...
Selecting previously deselected package python-reportlab.
Unpacking python-reportlab (from .../python-reportlab_2.4-1_all.deb) ...
Selecting previously deselected package python-reportlab-accel.
Unpacking python-reportlab-accel (from .../python-reportlab-accel_2.4-1_i386.deb) ...
Selecting previously deselected package python-uniconvertor.
Unpacking python-uniconvertor (from .../python-uniconvertor_1.1.4-1build1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
Setting up libmagick++2 (7:6.5.7.8-1ubuntu1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.

Setting up inkscape (0.47.0-2ubuntu2) ...

Setting up libwmf-bin (0.2.8.4-6.1ubuntu2) ...
Setting up perlmagick (7:6.5.7.8-1ubuntu1) ...
Setting up python-lxml (2.2.4-1) ...

Setting up python-renderpm (2.4-1) ...
Setting up python-reportlab (2.4-1) ...

Processing triggers for python-central ...
Setting up python-reportlab-accel (2.4-1) ...
Setting up python-uniconvertor (1.1.4-1build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by herveb on 2010-05-16
fix: I removed the offending softwares (tex-common, texlive-binaries, winefish), I have no more failure message when installing software.

I used ```
sudo aptitude
``` to remove texlive and tex-common

---

### Post by IzByFl on 2010-07-07
[http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/)

post #6 worked for me

---

### Post by TTGRULES on 2010-08-02
I had the same error after installing WineFish. Whenever I would try to install or uninstall a package, it would give an error and leave it partially unconfigured. 
All I did was uninstall winefish with the software center and then use sudo apt-get remove tex-common it removed both the offending addons that were causing the problem. Thanks!!!

---

