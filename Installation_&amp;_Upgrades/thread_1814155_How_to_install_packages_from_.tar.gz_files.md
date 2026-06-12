---
title: "How to install packages from .tar.gz files"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by love_linux1 on 2011-07-29
[FONT=Arial Black][SIZE=3][COLOR=DarkRed]Please tell me how to install packages from a .tar.gz file......[/COLOR][/SIZE][/FONT]

---

### Post by oldos2er on 2011-07-29
Depends on what's contained in the *.tar.gz file. Source code? Shell script? Precompiled binaries? What's the name of the program, and can you post a link to its website or where you downloaded it from?

---

### Post by lovinglinux on 2011-07-29
What exactly are you trying to install?

If you provide the name of the program and the reason why you are downloading a tar.gz package, then we can provide a better solution.

Usually, you don't need to go fishing applications on the Internet. Use Ubuntu Software Center to install the applications you need.

---

### Post by love_linux1 on 2011-07-31
I was installing TurboC-dev.tar.gz contains Source Code

---

### Post by raja.genupula on 2011-07-31
do you find any file like configure,  make  , can you list those file  contents .

---

### Post by oldos2er on 2011-07-31
> **love_linux1 said:**
> I was installing TurboC-dev.tar.gz contains Source Code

There are instructions here: [http://www.sandroid.org/TurboC/#Download](http://www.sandroid.org/TurboC/#Download)
Where it says "su" you should use "sudo -i" instead.

---

### Post by lkraemer on 2011-08-02
love_linux1,
The instructions on that site are very good.

A few things are assumed, and you may not know all of them.

To compile source code you need build-essential, and the headers for your
kernel installed, along with any libraries that are required (dependencies) to
compile without errors of missing code etc.

Most source is contained in a .tar.gz or zip or some compressed packaged file.
Contained in that file are some configure, makefile, and readme files.


**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your source code.


**TYPICAL COMPILE STEPS: (from within your source directory)**
```

cd~
cd path/to/source/code
./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.
**REF:**
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

[B]
COMPILE xxxx FROM SOURCE:[/B]

1. Use Synaptics to install the following Library Files needed for the Compile:
```

somerequiredlibxext-dev
somerequiredlibreadline-dev

```

2. Download source and extract to subdirectory.  The website uses:
```

tar -xzvf TurboC-dev.tar.gz
cd TurboC-source

```
Then read instructions in readme.txt and other files, then edit configure & makefile as needed.

3. Compile & Install (You may have to edit ./configure and/or makefile
to suit your needs according to documentation in the source readme files.
```

./configure
make clean
make
sudo make install

```
this assumes no errors.  If there errors Step #3 applies......  

4. Look for errors in compile after the "make" and fix the problems.  Then do:
```

make clean
make

```
until it all compiles.  Last step is to do:
```

sudo make install

```
Then locate the binary and execute the software with:
```

sudo updatedb
which binaryyouarelookingfor
/path/to/the/binary/thebinary [options] commands -switches etc..

```

Let us know how it goes............

TurboC looks interesting.  Brings back memories.....

lk

---

### Post by Trotel on 2011-11-24
Hi, I try to install lib32z1 and libc6-i386 packages
I try install with **sudo apt-get install <package>**, this don't work.
I search similar package with **apt-cache search <packages*>** and I don't have any similar packages.
So I download this in files
lib32z1: [http://packages.ubuntu.com/oneiric/libs/lib32z1](http://packages.ubuntu.com/oneiric/libs/lib32z1)
libc6-i386: [http://packages.ubuntu.com/oneiric/libs/libc6-i386](http://packages.ubuntu.com/oneiric/libs/libc6-i386)
So I do that you tell me, with build-essential and the headers, but when I wrote ./configure the last line have a error

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

Can you help me please?

---

### Post by raja.genupula on 2011-11-24
Man they seems deb files .
Installing .deb files is different from TAR

```
sudo dpkg -i filename.deb
```

use this command to install those .deb files .

actually you can get them by searching in synaptic man , I am sure .

---

