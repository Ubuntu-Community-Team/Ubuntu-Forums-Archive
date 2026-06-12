---
title: "Install Packages that are not in Synaptic"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by Trotel on 2011-11-22
Hi

I'm trying to install a .deb and I need some packages but they are not on the synaptic
How can I install this packages
lib32z1
libc6-i386

```
TGICL$ sudo dpkg -i perl-tgicl_2.1-1_all.deb 
Selecting previously deselected package perl-tgicl.
(Reading database ... 168515 files and directories currently installed.)
Unpacking perl-tgicl (from perl-tgicl_2.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of perl-tgicl:
 perl-tgicl depends on lib32z1 (>= 1:1.1.4); however:
  Package lib32z1 is not installed.
 perl-tgicl depends on libc6-i386 (>= 2.3); however:
  Package libc6-i386 is not installed.
 perl-tgicl depends on libfile-homedir-perl (>= 0.10); however:
  Package libfile-homedir-perl is not installed.
 perl-tgicl depends on libfile-spec-perl (>= 0.10); however:
  Package libfile-spec-perl is not installed.
dpkg: error processing perl-tgicl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 perl-tgicl

```$ uname -a
Linux 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by lkraemer on 2011-11-22
If you have the repositories selected in SYSTEM -> ADMINISTRATION -> Software Sources......................
You could always open a Terminal Window and do:
```

apt-get install lib32z1 libc6-i386

```
Since you may be compiling code you most likely will need to install the 
Headers and build-essential too!

Then just double left click on the .deb file.

[http://ubuntuforums.org/showthread.php?t=1814155&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1814155&highlight=build-essential)
Posting #7 as a reference

lk

---

### Post by Trotel on 2011-11-24
I try install with **sudo apt-get install <package>**, this don't work.
I search similar package with **apt-cache search <packages*>** and I don't have any similar packages.
So I download this in files
lib32z1: [http://packages.ubuntu.com/oneiric/libs/lib32z1](http://packages.ubuntu.com/oneiric/libs/lib32z1)
libc6-i386: [http://packages.ubuntu.com/oneiric/libs/libc6-i386](http://packages.ubuntu.com/oneiric/libs/libc6-i386)
So I do that you tell me, in the posting 7, but when I wrote ./configure the last line have a error

```
$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
configure: error: you must configure in a separate build directory

```

and make

```
$ make
Makeconfig:85: sysdeps/../config.make: No such file or directory
The GNU C library has not been configured.
Run `configure' to configure it before building.
Try `configure --help' for more details.
make: Failed to remake makefile `sysdeps/../config.make'.

```

---

### Post by lkraemer on 2011-11-26
Trotel,
You need to understand the difference in a library (lib) file, and the
necessary steps to compile and install code (typically source you write).

A libxxxx file is a module that does not need to be compiled.  It is a dependency for
other software that must be installed so the calling program can function properly.
So, there is no need to do a ./configure, make, make install, etc trying to install
a library.  

As per Posting #7, I state in BOLD text:
**TYPICAL COMPILE STEPS: (from within your source directory)**

and the steps below that are for compiling your source code so it can be executed.  I think
it would make good sense for you to re-read that posting SLOWLY, to grasp an understanding
of what is stated.

To be able to get all the dependencies you really need to select the proper Repo's in SYSTEM -> ADMINISTRATION -> Software Sources,
then search for lib32z1 and Apply the change.  That should load the required dependency's.  This all assumes you have
an Internet connection, and you have the proper Repo's selected..........OR you can use the Command Line to add the libs. 

lk

---

