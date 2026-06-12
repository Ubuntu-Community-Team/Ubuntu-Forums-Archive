---
title: "I can't compile, please help me"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by TSP on 2006-02-25
A couple od week ago i have to reinstall ubuntu and now i can't compile anything. i have installed build-essential, plus i install all the gnome dev files but i always have the same error c compiler cannot create executables...
What else can i do?

Thanks in advance! Cheers!

---

### Post by taurus on 2006-02-25
What's the output of this command,

gcc -v

---

### Post by TSP on 2006-02-25
> Objetivo: i486-linux-gnu
Configurado con: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada, treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-sh ared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-ge ttext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enabl e-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable- java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib /jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-chec king=release i486-linux-gnu
Modelo de hilos: posix
gcc versión 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)


Thank for try to help me

---

### Post by taurus on 2006-02-25
Could it be that the program you try to compile requires GCC version 3.4?  What is the name of the program you try to build for your machine and I assume you have to run "./configure" first, what is the output of that command?

---

### Post by TSP on 2006-02-25
I have the same problem with moreamp and ktorrent (i want the latest version, not the old version in the repositories)

ktorrent

> checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


---

### Post by taurus on 2006-02-25
Tell me where to download those programs and I will see if I can compile on my machine since I have the same version of GCC or post the whole content of the config.log...

---

### Post by TSP on 2006-02-25
Thank you so much!

ktorrent source code
[http://ktorrent.pwsp.net/index.php?page=downloads](http://ktorrent.pwsp.net/index.php?page=downloads)

Moreamp
[http://sourceforge.net/project/showfiles.php?group_id=121587&package_id=132681&release_id=388549](http://sourceforge.net/project/showfiles.php?group_id=121587&package_id=132681&release_id=388549)

Both are tar.gz files and i have the same problem. i dont know wht esle i need or if i have something wrong in my pc

---

### Post by taurus on 2006-02-25
First of, there is a .deb version (the latest one) for Kubuntu 5.10 so why don't you download that and install it as

```

sudo dpkg -i  ktorrent_1.2-1_i386.deb

```

Just so you know, I didn't have any trouble compiling ktorrent-1.2.tar.gz as

```

tar xvzf ktorrent-1.2.tar.gz
cd ktorrent-1.2
./configure
make
sudo make install

```

And for MoreAmp thing, if you read the INSTALLunix.txt, it tells you if you want to build and install it, then run ./mamkunixwxall.sh!!!  So, run this command at the prompt...

```

sudo ./mamkunixwxall.sh

```

---

### Post by TSP on 2006-02-26
I have problems with gcc when i try to compile something i get the same error is me configuration, maybe i have to setup my configuration to compile something?
thank for the help i am trying with something that i read in other forum
CC=/usr/bin/gcc-4.0
export CC

or

/usr/bin/gcc -> gcc-4.0
/usr/bin/g++ -> g++-4.0

Edited: i make a test i remove build essential and i have the same problems, seams to be that my system dont  see that i have the compiler tools, how can i fix this?

---

### Post by bayau on 2006-02-26
i have the same problem  as you..
still figure out how to solve it..

---

### Post by TSP on 2006-02-27
i have the problem fixed

sudo apt-get install --reinstall binutils

of course you have to install build-essential. hope that this help.


Cheers!

---

### Post by Swiss on 2006-03-03
I really need this app as it creates a virtual network between computers that have internet, I can't get my home networking to work, this app works, I just don't how to compile (or install) a tar.gz file. Help!

---

