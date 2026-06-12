---
title: "How could I install boost 1.37.0 under Ubuntu ?"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by WILL_CHAN on 2008-11-11
First, I download boost_1_37_0.tar.gz from boost.org. But I don't know how to install it from the command line. Anyone done this before could show me how to do it correctly ! I'd really appreciate it.

---

### Post by Partyboi2 on 2008-11-12
Boost is available in the ubuntu repos, easier to install then to compile, unless there is a reason you need to compile it.

---

### Post by WILL_CHAN on 2008-11-13
First of all, thanks ! I understand it, I and already installed boost 3.5.0 in repos. But some of the example that I downloaded from boost didn't work with my current version that's why I think I need to install the latest version. Further, I don't know how many times I did google searching already but I never find a complete tutorial of how to install boost :( ! That's strange since I think boost will be the next standard for C++ but very few people learn how to use them :( !

---

### Post by emit22 on 2008-12-11
And to think they want to standardize this into the STL.
All jokes put aside for a moment.  This is C++...

Has anyone so far been able to
compile Boost Libraries v1.3.7
onto debian? Ubuntu???

I don't want v.1.3.4 features because
debian doesn't keep libs current.

It doesn't compile
and I'm about to format to centos.

Help?

---

### Post by Amablue on 2009-01-28
I'm going to bump this because I'm interested in finding out right now too. I've been writing a program on my Windows PC, but I'd like to get it working under Ubuntu as well, although I'm still somewhat of a newbie when it comes to programming (or rather compiling) under linux.

---

### Post by kayvortex on 2009-02-01
This is what I did:

1) Download the library (obviously!). Note that I downloaded the .7z compressed one and found that I'd have to remove all the ^M dos newlines in the files, which is a hassle; so, just download the .bz2 or .gz compressed libraries instead.

2) Go to where that file was downloaded to (probably ~/Desktop) and untar it:
```
tar xjf boost_1_37_0.tar.bz2
```
or
```
tar xzf boost_1_37_0.tar.gz
```
depending on what file you downloaded.

This will create the directory "boost_1_37_0" where all the source code is located. Change into that directory:
```
cd boost_1_37_0
```


Now, the interesting bits:

3) Compile the libraries: If you're not doing anything fancy, like cross-compiling, then there's no need to explicitly use bjam yourself. Simply use configure:
```
./configure
```
Or you can also select what libraries you want since building all of them takes a bit of time. For example, if you only want the filesystem and program options libraries, instead use:
```
./configure --with-libraries=filesystem --with-libraries=program_options
```
I personally used the latter command since that's all I really wanted and I didn't want to waste half an hour compiling something that didn't work, so I can confirm that this does work ok. By default, the libraries and headers are installed to subdirectories of /usr/local, but you can change this if you want:
```
./configure --libdir=/my/library/dir --includedir=/my/header/dir
```
This will install the libraries to /my/library/dir and the headers to /my/header/dir. It's not advisable to change these to /usr/lib and /usr/include respectively since it's best to keep system files separate from manually installed stuff.
Now, you'll obviously need the necessary compiling tools (gcc, ld, etc.), and also python (which you probably already will have, I think). These can be installed by issuing:
```
sudo aptitude install build-essential python-dev
```
if you don't already have them. (Now, I'm not actually sure if you need python-dev as opposed to just python, so I'll play it safe and just say install the -dev package).
After configuring, you need to make the libraries:
```
make
```
This normally takes some time, so you'll need to be patient.

4) Installing:
```
sudo make install
```
This puts all the header files in /usr/local/include/boost-1_37 and all the libraries in /usr/local/lib by default (i.e. if you didn't tell configure at step 3 that you wanted them installed somewhere else).

5) Using the library:
This is where it got a little frustrating for me at first. The main problem lies in linking the libraries to your program.

5.1) You need to let ld know where your libs are (apparently). To do this, first check that "/usr/local/lib" is in /etc/ld.so.conf. On my system, /etc/ld.so.conf contained:
> include /etc/ld.so.conf.d/*.conf
So, I checked the files in /etc/ld.so.conf.d. Sure enough, /etc/ld.so.conf.d/libc.conf contained:
> # libc default configuration
/usr/local/lib
so I didn't have to do anything. If you don't find "/usr/local/lib" anywhere, make a file in /etc/ld.so.conf.d called "my_libs.conf" that contains:
> # My libraries
/usr/local/lib
Note that "/usr/local/bin" should be adjusted to whatever library directory you chose to install to at step 3 *if* you used the --libdir flag.

Having made sure that /usr/local/lib is known to ld, just issue the command:
```
sudo ldconfig
```

5.2) Invoking g++ properly:
Your code should simply use generic #include commands:
> #include <boost/filesystem.hpp>
etc. for two reasons: the first is portability, and the second is that using explicit file locations caused me to have either linker problems, or, worse, caused a segfault at runtime.
Having not told the compiler where, exactly, your files are in the source code, you must tell the compiler explicitly when invoking it: run gcc/g++ as:
> g++ -L/usr/local/lib -I/usr/local/include/boost-1_37 -lboost_filesytem-gcc42-mt ...
(Obviously replacing "..." with your source files/output files/other compiler flags like -g etc.)
The -L flag tells gcc where to look for the lib files (adjust as appropriate if modified at step 3 with --libdir).
The -I flag tells gcc where to look for the include flags (adjust as appropriate if modified at step 3 with --includedir).
The -l flag tells gcc to link the file libboost_filesystem-gcc42-mt.so.

For compiling multiple source files separately, make sure the -I flag is given, and then make sure the -L and -l flags are present at the linking stage.
Note that doing things like this means that you can have more than one installations of boost libs/headers installed on your system and everything will work fine and there's no need to do any uninstalling (I also have boost version 1.34.1 installed through the repos and there's no problems using the 1.37.0 version libs installed as above).

Note that I'm (still) using Hardy, but there shouldn't really be any differences in Intrepid that can't be resolved as above. Good luck!

---

### Post by deviouskoopa on 2010-02-23
> **kayvortex said:**
> 
3) Compile the libraries: If you're not doing anything fancy, like cross-compiling, then there's no need to explicitly use bjam yourself. Simply use configure:
```
./configure
```
Or you can also select what libraries you want since building all of them takes a bit of time. For example, if you only want the filesystem and program options libraries, instead use:
```
./configure --with-libraries=filesystem --with-libraries=program_options
```

When I unpacked the tar, there was no "configure" file and therefore the above commands did not work... what am I doing wrong?

---

