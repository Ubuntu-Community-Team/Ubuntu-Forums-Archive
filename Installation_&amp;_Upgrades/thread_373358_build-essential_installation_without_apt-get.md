---
title: "build-essential installation without apt-get"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by bracc0 on 2007-03-01
Hi everyone form a newbie,
this is a great place to put questions. I love this forum.

Now I'm facing a curious problem. 
I am trying to install the build-essential package for Edgy. I have no way to connect to any repository because my company firewall block them. I downloaded the build-essential package, I un-tared it, I ran ./configure and I got this:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for dpkg-architecture... no
configure: error: The dpkg development files (dpkg-dev) must be installed to build this package.

I downloaded and un-tared the dpkg-dev package too, I ran the ./configure and:

claudio@claudiubuntu:~/dpkg-1.13.22ubuntu6$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking dpkg cpu type... i386
checking dpkg operating system type... linux
checking dpkg architecture name... i386
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Opened the config.log and found an error stating that the file crt1.o is missing, same error showed in the link provided two rows down (/usr/bin/ld: crt1.o: No such file: No such file or directory).

Had a look in the forums searching "crt1.o" and... someone suggested to install build-essentials!
[http://www.ubuntuforums.org/showthread.php?t=371029&highlight=crt1.o](http://www.ubuntuforums.org/showthread.php?t=371029&highlight=crt1.o) 
:) 

Looks like a loop.  Anyone has an idea?

Thanks in advance
Claudio

---

### Post by Stemp on 2007-03-01
Hi Bracc0,

Do you mean you just installed the build-essential package, or all the packages related to it ? 
[http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)
Because there is a lot of dependencies

---

### Post by bracc0 on 2007-03-01
I mean that I am trying to install build essential with no luck because there are plenty of dependance.

Infact I got stuck when I try to install one of them, "dpkg-dev". 
The procedure says to look into the installation log file. The log file say that a file named "crt1.o" necessary for the configuration is missing, and the forum say that I have to install build-essentials. That's exactly what I'm trying to do! :-)

Claudio

---

### Post by taurus on 2007-03-01
The build-essential (and everything related to it) is on the install CD so if you have the CD, put it into a drive, open a terminal, and do

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by bracc0 on 2007-03-02
Lovely!
It worked fine. 
No need to enter any CLI command: the CD has been recognized immediately. 
I've been asked if I would open the cd with Synaptics. Then I have choosen the "build-essential", and the package with all dependancies has been installed in a few seconds.

Thanks a lot!
Claudio
:) :) :)

---

