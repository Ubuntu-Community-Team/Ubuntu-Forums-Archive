---
title: "jetty error"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by endurance001 on 2010-02-24
I have been having issues installing and removing program from the synaptic package manager  when a install or remove a program it says 

E: jetty: subprocess installed post-installation script returned error exit status 1 this program may not be installed 

what can i do to fix it

---

### Post by endurance001 on 2010-03-03
here is an terminal example of what its says when you try to install a program

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libsdl1.2debian-oss 1.2.13-4ubuntu4 [218kB]
Fetched 218kB in 1s (135kB/s)              
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you requested:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu4) | libsdl1.2debian-all (= 1.2.13-4ubuntu4) | libsdl1.2debian-esd (= 1.2.13-4ubuntu4) | libsdl1.2debian-oss (= 1.2.13-4ubuntu4) | libsdl1.2debian-nas (= 1.2.13-4ubuntu4) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu4); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 303323 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libsdl1.2debian-oss.
(Reading database ... 303316 files and directories currently installed.)
Unpacking libsdl1.2debian-oss (from .../libsdl1.2debian-oss_1.2.13-4ubuntu4_i386.deb) ...
Setting up jetty (6.1.20-2) ...
Adding system user `jetty' (UID 118) ...
Adding new user `jetty' (UID 118) with group `jetty' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /usr/share/jetty -g jetty -s /bin/false -u 118 jetty' returned error code 1. Exiting.
dpkg: error processing jetty (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libsdl1.2debian-oss (1.2.13-4ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 jetty
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

