---
title: "Help Installing tar.gz file (Alien Arena 2011)"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by TurtleKing on 2011-02-06
I have extracted the tar.gz file into my home folder. And according to the instruction it says I need to run "./configure", "make", and "sudo make install" within the alienarena-7.50 directory. However, when I tried the "./configure" command I get the follow result:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gawk... (cached) mawk
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to build the client... yes
checking for traditional single directory, in place installation... no
checking for library containing acos... -lm
checking for library containing dlopen... -ldl
checking for library containing clock_gettime... -lrt
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for library containing jpeg_read_header... -ljpeg
checking for X11... yes
checking for XXF86VM... yes
checking for XXF86DGA... yes
checking for X11/extensions/Xxf86dga.h... yes
checking for DEPS... no
configure: error: Package requirements (ode libcurl ogg vorbis vorbisfile freetype2) were not met:

No package 'ode' found
No package 'freetype2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
Am not sure what is it asking to do here.:confused: Afterwards, I tried the "make" command and it doesn't seem to respond well.
```
make: *** No targets specified and no makefile found.  Stop.
```
Same goes for the "sudo make install" command.

Any help please?

---

### Post by dino99 on 2011-02-06
install with synaptic: alien, gdebi

sudo alien -k packagename.tar.gz will give you a deb package: no need to extract

then right click on the generated deb to install it with gdebi, that it :)

---

### Post by lykeion on 2011-02-06
You need the build-essential package + all the dev packages needed for alien arena to compile it manually.

If you feel compiling software yourself is over your head you can install precompiled games like Alien Arena and others from PlayDeb.[LIST=1]
[*]Browse to PlayDeb: [http://www.playdeb.net/updates/Ubuntu/10.10](http://www.playdeb.net/updates/Ubuntu/10.10)
[*]Select "Click here to learn how to install games from PlayDeb" and follow instructions
[*]Find Alien Arena on PlayDeb Here: [http://www.playdeb.net/software/Alien%20Arena](http://www.playdeb.net/software/Alien%20Arena)
[*]Click "Install this now"
[/LIST]

---

### Post by TurtleKing on 2011-02-06
I want to compile as the download was big, and I am limited to such big downloads since I share internet connection. Do any of you happen to know what I need in order to compile it? Also, would be pretty cool to learn how to compile programs now for the future.

---

### Post by lykeion on 2011-02-06
Yes it is cool to compile :)
Usually the building reqs are listed in the README file.
Found an old thread in this forum on how to compile from svn: [http://ubuntuforums.org/showthread.php?t=476505](http://ubuntuforums.org/showthread.php?t=476505)
Just install the packages in the first code box of the first post of the thread. Can't guarantee it still works the building reqs may have changed, so look at the README.

---

### Post by TurtleKing on 2011-02-06
> **lykeion said:**
> Yes it is cool to compile :)
Usually the building reqs are listed in the README file.
Found an old thread in this forum on how to compile from svn: [http://ubuntuforums.org/showthread.php?t=476505](http://ubuntuforums.org/showthread.php?t=476505)
Just install the packages in the first code box of the first post of the thread. Can't guarantee it still works the building reqs may have changed, so look at the README.
I think I am going to have to skip compiling on this one since the terminal seems to be the one at fault. Basically, I check what the README said I would need, and compared it to Synaptic Package Manager and its matches. However, the terminal says the programs are still missing or not installed (same result as the 1st post). I guess I will just have to do the deb install method for this program.:(

---

### Post by lykeion on 2011-02-07
Never blame the poor terminal :) And I don't think you should give up on compiling so soon. But maybe try with a smaller program so you'd get a hang of it.

People who write programs and the readmes don't use the package names of specific distributions (like Ubuntu), so when they say it requires for example GTK+ 2.0 you need to install the package *libgtk2.0-dev*. This of course you wouldn't know when you're new at compiling but after a while you'll learn from experience.

Another thing to find what package is missing is to use the *apt-file* command (sudo apt-get install apt-file). And when ./configure shows an error message that a specific header file is missing, example: .... can't find alisp.h
You can use apt-file to tell what package will provide that file:
```
apt-file search alisp.h
```
(in this case you should install the package libasound2-dev)

To help you further can you output the part of the README that specifies the package requirements

EDIT 
Saw from output in 1st put it says "No package 'freetype2' found"
This means you need the package *libfreetype6-dev*
How I knew that? I used the *apt-cache* command to search for a dev package with name libfreetype in it ```
apt-cache search libfreetype | grep dev
```
and libfreetype6-dev would be the obvious one to install

No package 'ode' found
I'd use the same method here (you'd get two results, I'd test with installing the first one and if that doesn't do it uninstall it and try with the second one)

---

### Post by TurtleKing on 2011-02-07
Well, I even tried the play deb method, and I get an error once I click on install in ubuntu software center:
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

```
detail: alien-arena alien-arena-common alien-arena-data
```

---

### Post by TurtleKing on 2011-02-07
> **lykeion said:**
> Never blame the poor terminal :) And I don't think you should give up on compiling so soon. But maybe try with a smaller program so you'd get a hang of it.

People who write programs and the readmes don't use the package names of specific distributions (like Ubuntu), so when they say it requires for example GTK+ 2.0 you need to install the package *libgtk2.0-dev*. This of course you wouldn't know when you're new at compiling but after a while you'll learn from experience.

Another thing to find what package is missing is to use the *apt-file* command (sudo apt-get install apt-file). And when ./configure shows an error message that a specific header file is missing, example: .... can't find alisp.h
You can use apt-file to tell what package will provide that file:
```
apt-file search alisp.h
```
(in this case you should install the package libasound2-dev)

To help you further can you output the part of the README that specifies the package requirements

EDIT 
Saw from output in 1st put it says "No package 'freetype2' found"
This means you need the package *libfreetype6-dev*
How I knew that? I used the *apt-cache* command to search for a dev package with name libfreetype in it ```
apt-cache search libfreetype | grep dev
```
and libfreetype6-dev would be the obvious one to install

No package 'ode' found
I'd use the same method here (you'd get two results, I'd test with installing the first one and if that doesn't do it uninstall it and try with the second one)
Yay my first ubuntu software compile! Thanks Man!:biggrin:

---

### Post by lykeion on 2011-02-07
Good that it worked out for you.

Another tip I can give is if you have a duo- or quad-core cpu, you can speed up the compiling by specifying nr of simultaneous jobs for make. The usual recommendation is that nr of jobs should be equal to nr of cores + 1. So for a quad-core cpu use this instead of the ordinary make:
```
make -j5
```

---

### Post by TurtleKing on 2011-02-07
I can't really remember what were the exact errors (away from computer now), but after the "make" command was complete I tried the make install and got about 2-3 errors. I will try and see if it is just another program that needs to be installed if not, then I will post the errors.

As for the playdeb problem, any idea why Ubuntu Sotware Center responded with that error? I figured it would have some type of "continue or cancel" button menu, but not cancel completely.:confused:

---

### Post by TurtleKing on 2011-02-07
Solved, I just had to "sudo make install" command in terminal.

---

