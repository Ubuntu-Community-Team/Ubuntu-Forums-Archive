---
title: "Have installed 5.04. Then I tried installing Jahshaka and got dependency problems?"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by bongobongo on 2005-08-14
After basic installation of 5.04 and installation of NVIDIA drivers then I tried to install the Jahshaka
.deb packages.......

Below is the errors I got when I tried to install mlt_0.2.0-1_i386.deb

I also tried to install only jahshaka .deb file, See error report at bottom of this message.

Anyone out there with a smart way of fixing the errors below....

I see some packages should have been renewed....
Is there a quick way .... e.g. let ubuntu detect problem files and auto update those???
Or some other way

tore@ubuntu-xp:~$ sudo dpkg -i mlt_0.2.0-1_i386.deb
Password:
Selecting previously deselected package mlt.
(Reading database ... 71089 files and directories currently installed.)
Unpacking mlt (from mlt_0.2.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of mlt:
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
dpkg: error processing mlt (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
mlt
tore@ubuntu-xp:~$

Also tried to install only the Jahshaka 2.0RC1 .deb file and got following errors:

tore@ubuntu-xp:~$ sudo dpkg -i jahshaka_0.2.0rc1-1_i386.deb
Selecting previously deselected package jahshaka.
(Reading database ... 71089 files and directories currently installed.)
Unpacking jahshaka (from jahshaka_0.2.0rc1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of jahshaka:
jahshaka depends on libc6 (>= 2.3.5-1); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
jahshaka depends on libgcc1 (>= 1:4.0.1); however:
Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
jahshaka depends on libqt3c102-mt (>= 3:3.3.4); however:
Package libqt3c102-mt is not installed.
dpkg: error processing jahshaka (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
jahshaka
tore@ubuntu-xp:~$

---

### Post by bongobongo on 2005-08-15
Anyone with a suggestion!

---

### Post by secundar on 2005-08-18
You need to add Debian Sid to your repositories (apt-get/synaptic)

I'd love to have jashaka on ubuntu but i'm deathly afraid of adding Debian Sid. I seem to recall screwing my system not long ago...

---

### Post by bongobongo on 2005-08-19
Thanks for reply.

I have managed to do a ./configure.

But make fails.... are waiting for some feedback from the Jahshaka team to solve that.

But.... I have now tried to do this for 4 days now. And are still waiting for the solution.

I also have some mouse jagging problem in Ubuntu which really annoys me.

I might switch to OpenSuse today. I know the RPM packages on [www.jahshaka.org](www.jahshaka.org) installs nice with Suse. But then I would like not to... because I do not want to download 5 ISO files (CD') just to install a couple of applications.

---

### Post by mahiman on 2005-09-18
1) download the rpms
2)alien the 3 files in there
3) dpkg -i * on them
4) ln -s /usr/X11R6/lib/libXmu.so.6 libXmu.so

jahshaka

sudo as much as necessary...it works!

---

### Post by chaumurky on 2005-09-20
[QUOTE=mahiman]1) download the rpms
2)alien the 3 files in there
3) dpkg -i * on them
4) ln -s /usr/X11R6/lib/libXmu.so.6 libXmu.so

jahshaka

sudo as much as necessary...it works![/QUOTE]
 Wow! It was that easy! There goes my good night's sleep... ;-)

---

### Post by bongobongo on 2005-09-20
Thanks for reply.

I dig Ubuntu.

Did some tries and errors before I ended up with this distro.

It rocks.

Best regards

---

