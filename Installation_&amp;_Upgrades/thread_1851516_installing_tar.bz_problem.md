---
title: "installing tar.bz problem"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by Reen4 on 2011-09-28
[SIZE=2]I extract tar.bz package and trying to install the software from source(I am beginner at this:)) 
but it didn't work with me 
there is a README file tells {cmake -DCMAKE_INSTALL_PREFIX=/usr/ ../ -DCMAKE_MODULE_PATH=[path to FindQJSON.cmake]}

can anyone help me
I don't know what to do[/SIZE]

---

### Post by plant pot on 2011-09-28
I am not a ubuntu guy. I do not know how to install stuff on ubuntu. 

But normally... one types:
./configure
(to run an 'automake' 'configure' script if one is present; this step is needed to generate a 'Makefile' if one was not provided)

make
(to run the makefile; this will build / compile most normal software (hopefully!))

on most systems you would then type:
sudo make install
But ubuntu doesn't like 'make install', so instead type:[FONT=monospace]
[/FONT]sudo checkinstall
(to install the software onto your system for everyone to use).


The software you are using seems to use the uncommon 'cmake' rather than tried and tested (GNU) 'make' so it is a bit odd/unusual. It maybe that you need to install 'cmake first. Check to see if ubuntu has a package for 'cmake'?

I would suggest you start by trying to build a simpler, more normal program instead.

And tell the nice people on this list what it is that you are trying to build?


Also, it maybe that someone has already made a pre-compiled '.deb' package of the thing you want. This would save you from the need to do anything clever today. Ubuntu seems to discourage users from growing and using external '.tar.bz' / '.tar.gz' files. Search for a 'PPA' that carries the thing you want on [https://launchpad.net]("https://launchpad.net%27/") ?

---

### Post by oldos2er on 2011-09-28
> **Reen4 said:**
> I extract tar.bz package and trying to install the software from source(I am beginner at this:) 

Which version of Ubuntu are you using? Have you installed build-essential? Did you check the repositories first for the program you need? What program are you trying to compile, can you post a link to it?

---

### Post by Reen4 on 2011-09-28
> **plant pot said:**
> I am not a ubuntu guy. I do not know how to install stuff on ubuntu. 

But normally... one types:
./configure
(to run an 'automake' 'configure' script if one is present; this step is needed to generate a 'Makefile' if one was not provided)

make
(to run the makefile; this will build / compile most normal software (hopefully!))

sudo make install
(to install the software onto your system for everyone to use).


The software you are using seems to use the uncommon 'cmake' rather than tried and tested (GNU) 'make' so it is a bit odd/unusual. It maybe that you need to install 'cmake first. Check to see if ubuntu has a package for 'cmake'?

I would suggest you start by trying to build a simpler, more normal program instead.

And tell the nice people on this list what it is that you are trying to build?
I tried to do
./configure
make
sudo make install
but it didn't work. the package I'm trying to install is [SIZE=1]Google translate runner 0.0.3[/SIZE] and I found it in [softpedia]("http://linux.softpedia.com/get/Desktop-Environment/KDE/Google-translate-runner-47896.shtml") site 
> **oldos2er said:**
> Which version of Ubuntu are you using? Have you installed build-essential? Did you check the repositories first for the program you need? What program are you trying to compile, can you post a link to it?
I use ubuntu 11.4. I didn't know what is build-essential:).

---

### Post by plant pot on 2011-09-28
You would be smart to follow any of [[COLOR=#d40000]**oldos2er**[/COLOR]]("http://ubuntuforums.org/member.php?u=338320")'s advice over mine. He is clearly a very smart cookie.

Hopefully someone will tell you how to search for and install a ready-made 'Google translate runner' package. It looks like an older v0.0.2 one exists on [https://launchpad.net](https://launchpad.net)  But I am not experienced at that.


If that doesn't pan-out, and you still want to compile your own v0.0.3 then...

> **Reen4 said:**
> I use ubuntu 11.4. I didn't know what is build-essential:).

Ubuntu normally distributes software as 'packages'. To compile non-ubuntu software on ubuntu you need a 'package' that allows you to do this. That package is called 'build-essentials'. It contains compilers such as 'gcc' and the 'make' program I referred to. You need it.

Use the package downloading tool on your ubuntu desktop to download and install the package called 'build-essentials'.

The thing you read in the readme file means that you also need to use the package downloading tool to download and install the package called 'cmake'.

Google translate looks like it needs 'KDE'. Someone else can suggest how to install a 'KDE' development package on ubuntu. I don't have a clue and would probably give up. 'KDE' is big and would take a while to download and install.

After that, try to follow the 'readme' again.
Sorry.

---

### Post by azmyth on 2011-09-28
You need to install cmake libqjson0 libqjson-dev kdelibs5-dev

Unpack the package and go to the directory the google translate directory and use the command

cmake -DCMAKE_INSTALL_PREFIX=/usr/  -DCMAKE_MODULE_PATH=/usr/share/cmake-2.8/Modules/FindQJSON.cmake

You must be running KDE as well

---

### Post by Reen4 on 2011-09-29
> **plant pot said:**
> 
Hopefully someone will tell you how to search for and install a ready-made 'Google translate runner' package. It looks like an older v0.0.2 one exists on [https://launchpad.net](https://launchpad.net)  But I am not experienced at that.

I tried installing **[SIZE=1]google-translate-runner 0.0.2[/SIZE] **but it didn't work
thanks for helping me :)

> **azmyth said:**
> You need to install cmake libqjson0 libqjson-dev kdelibs5-dev

Unpack the package and go to the directory the google translate directory and use the command

cmake -DCMAKE_INSTALL_PREFIX=/usr/  -DCMAKE_MODULE_PATH=/usr/share/cmake-2.8/Modules/FindQJSON.cmake

You must be running KDE as well
I did all you told me to but running KDE. I don't know how
and it didn't work :(
[HTML]-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.7.2 (using /usr/bin/qmake)
-- Looking for XOpenDisplay in  /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so;/usr/lib/i386-linux-gnu/libXau.so;/usr/lib/i386-linux-gnu/libXdmcp.so
-- Looking for XOpenDisplay in  /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so;/usr/lib/i386-linux-gnu/libXau.so;/usr/lib/i386-linux-gnu/libXdmcp.so  - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/i386-linux-gnu/libX11.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE 
-- Looking for _POSIX_TIMERS
-- Looking for _POSIX_TIMERS - found
-- Found Automoc4: /usr/bin/automoc4 
-- Found Perl: /usr/bin/perl 
-- Found Phonon: /usr/include 
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Failed
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.6 include dir: /usr/include
-- Found KDE 4.6 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
CMake Error at /usr/share/kde4/apps/cmake/modules/FindPackageHandleStandardArgs.cmake:198 (MESSAGE):
  Could NOT find KDE4Workspace (missing: KDE4Workspace_CONFIG)
Call Stack (most recent call first):
  /usr/share/kde4/apps/cmake/modules/FindKDE4Workspace.cmake:70 (find_package_handle_standard_args)
  CMakeLists.txt:10 (find_package)


-- Configuring incomplete, errors occurred![/HTML]

---

### Post by azmyth on 2011-09-29
You didn't install this.

kdelibs5-dev

KDE is the desktop environment. You're trying to install a plasma plugin for KDE thus you need to be running KDE.

---

### Post by Reen4 on 2011-09-29
> **azmyth said:**
> You didn't install this.

kdelibs5-dev

KDE is the desktop environment. You're trying to install a plasma plugin for KDE thus you need to be running KDE.
Thanks a lot

---

