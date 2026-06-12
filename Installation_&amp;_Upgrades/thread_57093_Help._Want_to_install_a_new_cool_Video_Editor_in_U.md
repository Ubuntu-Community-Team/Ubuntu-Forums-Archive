---
title: "Help. Want to install a new cool Video Editor in Ubuntu. Have problems."
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by bongobongo on 2005-08-15
There is a new Video Editor, Compositor and Effects application out.

It called Jahshaka.

Have tried to install Jahshaka on Ubuntu 5.04 without any luck.

The files are here:
[http://www.mediainlinux.org/index.php/mediainlinux/downloads/multimedia_debian_packages/jahshaka_debian_package](http://www.mediainlinux.org/index.php/mediainlinux/downloads/multimedia_debian_packages/jahshaka_debian_package)

First it complained about missing/wrong versioned dependencies.

Then I tried to install using --force-all option at it did not complain anymore.

Hovever, I cannot launch the Jahshaka application.

If I open synaptic then the installed .deb apps show up in the 
Installed (Local or obsolete) section, marked for removal.......???????

Have asked for help here before without any luck.....

If you could try to install and come back with a "How to that would be nice"

If not I have the terminal responds when I "installed" the .deb packages below:

Best regards

got these messages when installing the Jahshaka .deb files:

tore@ubuntu-xp:~$ sudo dpkg -i --force-all mlt_0.2.0-1_i386.deb
Selecting previously deselected package mlt.
(Reading database ... 58062 files and directories currently installed.)
Unpacking mlt (from mlt_0.2.0-1_i386.deb) ...
dpkg: mlt: dependency problems, but configuring anyway as you request:
 mlt depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 mlt depends on libgcc1 (>= 1:4.0.1); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 mlt depends on libglib2.0-0 (>= 2.7.1); however:
  Version of libglib2.0-0 on system is 2.6.3-1.
 mlt depends on libgtk2.0-0 (>= 2.7.0); however:
  Version of libgtk2.0-0 on system is 2.6.4-0ubuntu3.
 mlt depends on libpango1.0-0 (>= 1.9.0); however:
  Version of libpango1.0-0 on system is 1.8.1-0ubuntu2.
 mlt depends on libstdc++6 (>= 4.0.1); however:
  Package libstdc++6 is not installed.
 mlt depends on libvorbis0a (>= 1.1.0); however:
  Version of libvorbis0a on system is 1.0.1-1.
 mlt depends on libvorbisfile3 (>= 1.1.0); however:
  Version of libvorbisfile3 on system is 1.0.1-1.
 mlt depends on libxml2 (>= 2.6.20); however:
  Version of libxml2 on system is 2.6.17-0ubuntu1.
Setting up mlt (0.2.0-1) ...
tore@ubuntu-xp:~$ sudo dpkg -i --force-all mlt++_0.2.0-1_i386.deb
Selecting previously deselected package mlt++.
(Reading database ... 58162 files and directories currently installed.)
Unpacking mlt++ (from mlt++_0.2.0-1_i386.deb) ...
dpkg: mlt++: dependency problems, but configuring anyway as you request:
 mlt++ depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 mlt++ depends on libgcc1 (>= 1:4.0.1); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
Setting up mlt++ (0.2.0-1) ...
tore@ubuntu-xp:~$ sudo dpkg -i --force-all jahshaka_0.2.0-1_i386.deb
dpkg: error processing jahshaka_0.2.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 jahshaka_0.2.0-1_i386.deb
tore@ubuntu-xp:~$ sudo dpkg -i --force-all jahshaka_0.2.0rc1-1_i386.deb
Selecting previously deselected package jahshaka.
(Reading database ... 58188 files and directories currently installed.)
Unpacking jahshaka (from jahshaka_0.2.0rc1-1_i386.deb) ...
dpkg: jahshaka: dependency problems, but configuring anyway as you request:
 jahshaka depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 jahshaka depends on libgcc1 (>= 1:4.0.1); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 jahshaka depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
Setting up jahshaka (0.2.0rc1-1) ...

---

### Post by bongobongo on 2005-08-15
Calling ubuntu gurus to make Jahshaka work in Ubuntu 5.04

---

### Post by claydoh on 2005-08-16
You can try using alien to convert the rpm version to a deb, but you may have better luck building from the source code.

---

