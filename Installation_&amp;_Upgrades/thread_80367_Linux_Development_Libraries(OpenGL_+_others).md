---
title: "Linux Development Libraries(OpenGL + others)"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by Zanza on 2005-10-22
I'm a 3rd year Comp. Sci. major, and as part of our program at the University I attend our programs are graded on Linux machines. I have some experience using Linux, but very little experience in configuring Linux. So far I have been incredibly impressed with how Ubuntu detected and configured itself perfectly to my hardware.

However, Ubuntu seems to have nearly no development tools, I had to install g++ and make utility with synaptic. I cannot however seem to find OpenGL's libraries(gl, glu and glut). I'm also not sure if it is missing any other of the libraries like the Standard Template Libraries like vector and list. Can I simply copy and paste over the Lib files from my school's Fedora Core 2 machines? and if not where can I find the libraries I need? How do I install the libraries I need?

---

### Post by CrunchyDoodle on 2005-10-22
I suggest using the Synaptic Package Manager and setting the Packages you want to see for Development (Restricted copyright, multiverse and universe). I think everything you want will be there.

Bye.    :cool:

MSCS Loyola 1985

---

### Post by Kyral on 2005-10-22
I present to you the search results from apt-cache search glu

```
kyral@GNUGeneration:~$ aptS glu
foomatic-db - linuxprinting.org printer support - database
foomatic-db-engine - linuxprinting.org printer support - programs
foomatic-db-gimp-print - linuxprinting.org printer support - database for Gimp-Print printer drivers
foomatic-db-hpijs - linuxprinting.org printer support - database for HPIJS driver
foomatic-filters - linuxprinting.org printer support - filters
foomatic-filters-ppds - linuxprinting.org printer support - prebuilt PPD files
freeglut3 - OpenGL Utility Toolkit
freeglut3-dbg - OpenGL Utility Toolkit debugging information
freeglut3-dev - OpenGL Utility Toolkit development files
glut-doc - documentation and examples for the OpenGL Utility Toolkit
glutg3-dev - the OpenGL Utility Toolkit development files
libgcj-dev - Java development headers and static library for use with gcj
libgcj6 - Java runtime library for use with gcj
libgcj6-dev - Java development headers and static library for use with gcj
libglu1-mesa - The OpenGL utility library (GLU)
libglu1-mesa-dev - The OpenGL utility library -- development support files
libglut3 - the OpenGL Utility Toolkit
libglut3-dev - development libraries and headers for GLUT
python-opengl - Python binding to OpenGL
python2.4-nevow - Web application templating system for Python and Twisted
python2.4-opengl - Python binding to OpenGL
celestia-glut - A real-time visual space simulation (GLUT frontend)
foomatic-gui - GNOME interface for configuring the Foomatic printer filter system
freesci - a portable interpreter for SCI games like Space Quest 3
gauche-gl - Gauche bindings for OpenGL
ghc-cvs-hopengl - HOpenGL libraries for the Glasgow Haskell Compilation system
ghc6-hopengl - HOpenGL libraries for the Glasgow Haskell Compilation system
glunarclock - GNOME Lunar Clock Applet
glurp - gtk2.4+ frontend to the Music Player Daemon (MPD)
glutg3 - the OpenGL Utility Toolkit
hunspell - spell checker and morphological analyzer (program)
jedstate - Extended mind for John E. Davis' text editor jed
libclass-container-perl - Glues object frameworks together transparently
libclass-dbi-abstractsearch-perl - Abstract Class::DBI's SQL with SQL::Abstract
libclass-dbi-pager-perl - Pager utility for Class::DBI
libcrypt-ssleay-perl - Support for https protocol in LWP
libextutils-parsexs-perl - convert Perl XS code into C code
libextutils-xsbuilder-perl - Automatic XS glue code generation
libglui-dev - A GLUT-based C++ user interface library
libglui2c102 - GLUI, a C++ GLUT based GUI library - runtime support
libhunspell-dev - spell checker and morphological analyzer (static library)
libinline-perl - Write Perl subroutines in other programming languages
libopengl-perl - Perl module to display 3D data using OpenGL, GLU, GLUT, and GLXmesademos - Example programs for Mesa (and OpenGL in general)
ml-nlffigen - ML generator for C glue code
mpd - Music Player Daemon, the name says it all
mtx - controls tape autochangers
passepartout - XML-based Desktop Publishing Application
pike7.2-pexts-admintools - Pike AdminTools module
pike7.2-pexts-bzip2 - Pike bzip2 module
pike7.2-pexts-curses - Pike (N)Curses module
pike7.2-pexts-geoip - Pike GeoIP module
pike7.2-pexts-mcrypt - Pike mcrypt module
pike7.2-pexts-mhash - Pike Mhash module
pike7.2-pexts-newt - Pike Newt module
pike7.2-pexts-pcre - Pike PCRE module
pike7.4-pexts-admintools - Pike AdminTools module
pike7.4-pexts-bzip2 - Pike bzip2 module
pike7.4-pexts-curses - Pike (N)Curses module
pike7.4-pexts-geoip - Pike GeoIP module
pike7.4-pexts-mcrypt - Pike mcrypt module
pike7.4-pexts-mhash - Pike Mhash module
pike7.4-pexts-newt - Pike Newt module
pike7.4-pexts-pcre - Pike PCRE module
pike7.6-odbc - Odbc module for Pike
printconf - Automatically configures USB and parallel printers with CUPS
python-foomatic - Python interface to the Foomatic printer database
python-gnuplot - A Python interface to the gnuplot plotting program
python-gtkmvc - Model-View-Controller (MVC) implementation for pygtk
python-plplot - Python support for PLplot, a plotting library
python2.3-nevow - Web application templating system for Python and Twisted
python2.3-opengl - Python binding to OpenGL
tcpslice - extract pieces of and/or glue together tcpdump files
tidev-modules-source - Sources for drivers for Texas Instruments calculators link cables
tilp - TI calculator <-> PC communication program for X
userv - `user services' - program call across trust boundaries
wims - WWW Interactive Mathematics Server (WIMS)
kyral@GNUGeneration:~$ aptS opengl
blender - Very fast and versatile 3D modeller/renderer
freeglut3 - OpenGL Utility Toolkit
freeglut3-dbg - OpenGL Utility Toolkit debugging information
freeglut3-dev - OpenGL Utility Toolkit development files
ftgl-dev - Library to render text in OpenGL using FreeType
gle-doc - OpenGL tubing and extrusion library documentation
glut-doc - documentation and examples for the OpenGL Utility Toolkit
glutg3-dev - the OpenGL Utility Toolkit development files
gtkglarea5 - Gimp Toolkit OpenGL area widget shared library
gtkglarea5-dev - Gimp Toolkit OpenGL area widget include files and static library
libgl1-mesa - A free implementation of the OpenGL API -- runtime
libgl1-mesa-dbg - A free implementation of the OpenGL API -- debugging package
libgl1-mesa-dev - A free implementation of the OpenGL API -- development support files
libgl1-mesa-dri - A free implementation of the OpenGL API -- DRI runtime
libgle-dev - OpenGL tubing and extrusion library development files
libgle-doc - OpenGL tubing and extrusion library documentation
libgle3 - OpenGL tubing and extrusion library
libgle3-dev - OpenGL tubing and extrusion library development files
libglitz1 - Glitz OpenGL image compositing library
libglitz1-dev - OpenGL image compositing library development libraries and headers
libglu1-mesa - The OpenGL utility library (GLU)
libglu1-mesa-dev - The OpenGL utility library -- development support files
libglut3 - the OpenGL Utility Toolkit
libglut3-dev - development libraries and headers for GLUT
libopenal-dev - OpenAL is a portable library for 3D spatialized audio
libopenal0 - OpenAL is a portable library for 3D spatialized audio
libosmesa6 - Mesa Off-screen rendering extension
libtiff-tools - TIFF manipulation and conversion tools
mesa-doc - Developer documentation for Mesa
openoffice.org2 - OpenOffice.org Office suite version 2.0
python-opengl - Python binding to OpenGL
python2.4-opengl - Python binding to OpenGL
rss-glx - Really Slick Screensavers GLX Port
x11proto-gl-dev - X11 OpenGL extension wire protocol
xscreensaver-gl - GL(Mesa) screen hacks for xscreensaver
nvidia-glx - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-glx-legacy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
nvidia-settings - Tool of configuring the NVIDIA graphics driver
xorg-driver-fglrx - Video driver for ATI graphics accelerators
3ddesktop - "Three-dimensional" desktop switcher
achilles - An artificial life and evolution simulator
boson - an OpenGL wargame for KDE
boson-data - Datas for Boson
cl-sdl-demos - CL-SDL and OpenGL example programs
cl-sdl-opengl - Support for OpenGL in Common Lisp, via CL-SDL
clanlib-doc - Reference documentation and tutorials for ClanLib
clanlib-examples - Examples for ClanLib
conquest-gl - a real-time, multi-player space warfare game (OpenGL client)
crack-attack - multiplayer OpenGL puzzle game like "Tetris Attack"
criticalmass - Shoot-em-up a la galaxian
csmash - CannonSmash, a table tennis simulation game
egoboo - 3D dungeon crawling adventure in the spirit of NetHack
egoboo-data - Egoboo data files.
entity-gl - XML-based GUI builder for GTK+ (OpenGL bindings)
foobillard - a 3D billiards game using OpenGL
gauche-gl - Gauche bindings for OpenGL
gem - Graphics Environment for Multimedia - OpenGL animation tools
ghc-cvs-hopengl - HOpenGL libraries for the Glasgow Haskell Compilation system
ghc5-hopengl - HOpenGL libraries for the Glasgow Haskell Compilation system
ghc6-hopengl - HOpenGL libraries for the Glasgow Haskell Compilation system
ghemical - A GNOME molecular modelling environment
gliv - image viewer using gdk-pixbuf and OpenGL
glutg3 - the OpenGL Utility Toolkit
gngb - GameBoy Emulator
gnubik - 3D Rubik's cube game
junior-games-gl - Debian Jr. 3D Games (hardware acceleration required)
k3d - 3D modeling and animation system
k3d-doc - 3D modeling and animation system - Documentation
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
libcegui-mk2-0 - Crazy Eddie's GUI (libraries)
libcegui-mk2-0-dbg - Crazy Eddie's GUI (debugging libraries)
libcegui-mk2-dev - Crazy Eddie's GUI (development files)
libclan2-gl - OpenGL module for ClanLib game SDK
libclan2-gui - GUI module for ClanLib game SDK
libclan2-jpeg - JPEG module for ClanLib game SDK
libclan2-lua - Lua module for ClanLib game SDK
libclan2-mikmod - MikMod module for ClanLib game SDK
libclan2-network - Network module for ClanLib game SDK
libclan2-png - PNG module for ClanLib game SDK
libclan2-sound - Sound module for ClanLib game SDK
libclan2-ttf - TTF module for ClanLib game SDK
libclan2-vorbis - Vorbis module for ClanLib game SDK
libclanlib-dev - ClanLib game SDK development files
libclanlib2c2 - ClanLib game SDK core runtime
libcoin40-dev - high-level 3D graphics devkit with Open Inventor and VRML97 support
libcoin40c2 - high-level 3D graphics kit with Open Inventor and VRML97 support - runtime
libdevil-dev - Cross-platform image loading and manipulation toolkit
libformsgl-dev - Header files and static libraries for the OpenGL XForms librarylibformsgl1 - The OpenGL XForms graphical interface widget library
libfox1.0c2 - The FOX C++ GUI Toolkit
libfox1.2c2 - The FOX C++ GUI Toolkit
libglew-dev - The OpenGL Extension Wrangler - development environment
libglew1 - The OpenGL Extension Wrangler - runtime environment
libglitz-glx1 - Glitz OpenGL library GLX backend
libglitz-glx1-dev - Glitz OpenGL library GLX backend development libraries and headers
libglpng - PNG loader for OpenGL
libglpng-dev - PNG loader for OpenGL - development files
libglui-dev - A GLUT-based C++ user interface library
libgtkada-gl-2.4 - Ada binding for OpenGL
libgtkgl2.0-1 - Gimp Toolkit OpenGL area widget shared library
libgtkgl2.0-dev - Gimp Toolkit OpenGL area widget include files and static library
libgtkglext1 - OpenGL Extension to GTK (shared libraries)
libgtkglext1-dev - OpenGL Extension to GTK (development files)
libgtkglext1-doc - OpenGL Extension to GTK (documentation)
libgtkglext1-ruby - GTK+ GL extension bindings for the Ruby language
libgtkglextmm1-dev - C++ wrapper for the OpenGL Extension to GTK (development files)
libgtkglextmm1c2 - C++ wrapper for the OpenGL Extension to GTK (shared libraries)
libinti-gl-dev - GtkGLExt bindings for Inti - development files
libinti-gl-doc - GtkGLExt bindings for Inti - shared libraries
libinti-gl1c2 - GtkGLExt bindings for Inti - shared libraries
liblablgl-ocaml - Runtime libraries for lablgl
liblablgl-ocaml-dev - an OpenGL interface for Objective Caml
liblablgtk-ocaml - Runtime libraries for lablgtk.
liblablgtk-ocaml-dev - Ocaml bindings to Gtk+
libopenalpp-cvs-dev - Object Oriented version of OpenAL
libopenalpp-cvsc2 - Object Oriented version of OpenAL
libopengl-dylan - Support for OpenGL in Gwydion Dylan (Native)
libopengl-perl - Perl module to display 3D data using OpenGL, GLU, GLUT, and GLXlibopengl-ruby - OpenGL binding for Ruby
libopenscenegraph-dev - 3D scenegraph development files
libopenscenegraphc2 - 3D scenegraph
libosgcal-dev - cal3d to OpenSceneGraph adapter
libosgcalc2 - cal3d to OpenSceneGraph adapter development files
libproducer-dev - Cross-platform C++ library for managing OpenGL rendering contexts
libproducerc2 - Cross-platform C++ library for managing OpenGL rendering contexts
libqglviewer-dev - A qt/OpenGL-based viewing widget
libqglviewer1 - A qt/opengl-based viewing widget
libqt4-gui - Qt 4 core GUI functionality runtime library
libsage-0.1 - Supports OpenGL in SDL applications
libsage-dev - Supports OpenGL in SDL applications
libtiff-opengl - TIFF manipulation and conversion tools
libtulip-2.0-dev - Tulib graph library - core development files
libtulip-2.0c2 - Tulib graph library - core runtime
libtulip-ogl-2.0-dev - Tulib graph library - OpenGL development files
libtulip-ogl-2.0c2 - Tulib graph library - OpenGL runtime
libtulip-qt-2.0-dev - Tulib graph library - Qt/OpenGL gui development files
libtulip-qt-2.0c2 - Tulib graph library - Qt/OpenGL gui runtime
libvtk4c2 - Visualization Toolkit - A high level 3D visualization library
libwxgtk2.4-1 - wxWindows Cross-platform C++ GUI toolkit (GTK+ runtime)
libwxgtk2.4-dev - wxWindows Cross-platform C++ GUI toolkit (GTK+ development)
libwxgtk2.6-0 - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
libwxgtk2.6-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)
lightlab - experiment with the OpenGL lighting model
lightspeed - Shows how objects moving at relativistic speeds look like
mesademos - Example programs for Mesa (and OpenGL in general)
openalpp-cvs-doc - Object Oriented version of OpenAL
openoffice.org - high-quality office productivity suite
openscenegraph - 3D scenegraph binary files
openscenegraph-doc - 3D scenegraph documentation
openuniverse - 3D Universe Simulator
openuniverse-common - 3D Universe Simulator data files
osgcal-doc - documentation for the cal3d to OpenSceneGraph adapter
pike7.2-gl - Mesa module for Pike
pike7.4-gl - Mesa module for Pike
planetpenguin-racer - another 3D racing game featuring Tux, the Linux penguin
planetpenguin-racer-data - data files for the game PlanetPenguin Racer
plib-doc - Portability Libraries: documentation and examples
plib1.8.4 - Portability Libraries: Run-time package, stable release
plib1.8.4-dev - Portability Libraries: Development package, stable release
plib1.8.4-pic - Portability Libraries: Dev. package (with PIC code), stable rel.pointless - A presentation tool based on OpenGL
pong2 - Remake of old arcade classic in OpenGL
prboom - clone of the legendary first person shooter Doom
producer-doc - Documentation for C++ library for managing OpenGL rendering contexts
pymol - An OpenGL Molecular Graphics System written in Python
python-openal - port for Python of the OpenAL library
python-qt3-gl - Qt3 OpenGL bindings for Python (default version)
python-soya - high level 3D engine for Python
python-soya-doc - high level 3D engine for Python
python2.3-opengl - Python binding to OpenGL
python2.3-qt3-gl - Qt3 OpenGL bindings for Python 2.3
python2.4-qt3-gl - Qt3 OpenGL bindings for Python 2.4
r-cran-rgl - GNU R package for three-dimensional visualisation using OpenGL
sear - 3D client for the Worldforge game servers
sppc - Simple Panel Plot Composer
ssystem - 3D solar system simulator
stalin - An extremely aggressive Scheme compiler
stratagus - realtime strategy game for Unix and X
stratagus-gl - realtime strategy game for Unix and X - OpenGL version
torcs - 3D racing cars simulator game using OpenGL
trackballs - An OpenGL-based game of marbles through a labyrinth
vertex - a GTK+OpenGL 3D modeller
xlockmore - Lock X11 display until password is entered.
xlockmore-gl - Lock X11 display until password is entered -- GL version
xmakemol-gl - A program for visualizing atomic and molecular systems
xmms-iris - advanced OpenGL visualization plugin for XMMS
xracer - A free Wipeout clone for Unix and X.
xracer-tools - A free Wipeout clone for Unix and X.
xwnc - Mix of Xvnc and XDarwin with improved protocol
amoeba - fast-paced, polished OpenGL demonstration by Excess
amoeba-data - Fast-paced, polished OpenGL demonstration by Excess (data)
cthugha - an oscilloscope on acid
doomlegacy-sdl - A port of the Doom engine that supports OpenGL
doomlegacy-x11 - A port of the Doom engine that supports OpenGL
mplayer-386 - The Ultimate Movie Player For Linux
mplayer-586 - The Ultimate Movie Player For Linux
mplayer-custom - The Ultimate Movie Player For Linux
mplayer-k6 - The Ultimate Movie Player For Linux
mplayer-nogui - The Ultimate Movie Player For Linux
quake2 - improved version of id Software's Quake II engine
snes9x-common - Common files for snes9x
snes9x-opengl - OpenGL binaries for snes9x - Super NES Emulator

``` 
BTW, aptS is my alias to "apt-cache search"

---

### Post by spearfish on 2006-03-19
Hi, I am also a computer science student in college.  I was really amazed that Ubuntu didn't come with either emacs or G++.  Considering that a really big percent of people installing linux on their machines are programmers, this seems really lame on the part of Ubuntu.

Admittedly, the Synaptic Package Manager is pretty cool, but Ubuntu documentation doesn't do much to say:  If you are a programmer, you want "package A," "package B", etc.  Much of the documentation comes from exasperated posts on the message forum, and realizing that 100 other people had the same problem.

---

### Post by lakcaj on 2006-04-10
apt-get install build-essential x-window-system-dev

That's usually what I do to grab just about everything I might need.  The reason it is not included by default is that alot of people will never compile anything themselves on a linux box.  So, if you are a programmer, you should be knowledgeable enough to install the required packages yourself.

---

### Post by Obidan on 2006-07-28
> **lakcaj said:**
> apt-get install build-essential x-window-system-dev

That's usually what I do to grab just about everything I might need.

----------------------------------------

***Ahem.... Here we go.....***

sudo apt-get install build-essential x-window-system-dev

The following packages have unmet dependencies:
  x-window-system-dev: 
     Depends: libgl1-mesa-dev but it is not going to be installed
     Depends: libglu1-mesa-dev but it is not going to be installed

***Shazbot! Well then....***

sudo apt-get install libgl1-mesa-dev

The following packages have unmet dependencies:
  libgl1-mesa-dev: 
     Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-0ubuntu16 is to be installed
E: Broken packages

***Huh.... Broken packages? Well then, let's just get rid of libgl1-mesa, and put the right one in....***

sudo apt-get remove libgl1-mesa

The following packages will be REMOVED:
  compiz compiz-gnome compiz-kde fglrx-control freeglut3 gdebi gdm gksu
  gnome-app-install gnome-netstatus-applet gnome-system-monitor
  gnome-volume-manager gstreamer0.8-x hal-device-manager hwdb-client
  libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libgl1-mesa-dri libgle3 libglew1
  libglitz-glx1 libglu1-mesa libglut3 libopengl-perl libqt4-gui
  libqt4-qt3support mesa-utils mozilla-mplayer mplayer mplayer-586
  mplayer-fonts python-gnome2-extras python2.4-gnome2-extras qt4-qtconfig
  rss-glx serpentine update-notifier x-window-system-core xbase-clients
  xdriinfo xorg-driver-fglrx xscreensaver-gl xscreensaver-gl-extra xserver-xgl

***_HELLS NO!!! WTF Can't I just install the dev headers?!?!?_***

---

### Post by clash on 2006-08-18
Didn't get this probelm fixed no ?

---

### Post by rnodal on 2006-08-28
Did you add extra repositories?

---

### Post by aqwabawks on 2006-08-29
Looks like I'm not the only one having problems installing Glut libraries.

I'm required to be create programs using C and Open GL in Linux.  I have install all the mesa and glut libraries I've read around the forums that I require but when I try to compile a Open GL program it can't find any Open GL libraries....  What could I be doing wrong?

---

### Post by rnodal on 2006-08-29
Are you using an IDE or you are compiling from command line?

---

### Post by aqwabawks on 2006-08-29
I'm compiling from command line.

---

### Post by az on 2006-08-29
> **aqwabawks said:**
> Looks like I'm not the only one having problems installing Glut libraries.

I'm required to be create programs using C and Open GL in Linux.  I have install all the mesa and glut libraries I've read around the forums that I require but when I try to compile a Open GL program it can't find any Open GL libraries....  What could I be doing wrong?

Make sure you have the universe repository enabled, update and the install the required -dev packages.

There is no problem here - all of the dev tools and libraries are available.

Ubuntu is streamlined in that not everything is in the main repo.  The Universe repo is community-suported.  That's why you get cutting-edge packages with support, there are in the main repository.  If everything was in main, this would be Debian.

---

### Post by Seq on 2006-08-29
> **Obidan said:**
> ----------------------------------------

***Ahem.... Here we go.....***

sudo apt-get install build-essential x-window-system-dev

The following packages have unmet dependencies:
  x-window-system-dev: 
     Depends: libgl1-mesa-dev but it is not going to be installed
     Depends: libglu1-mesa-dev but it is not going to be installed

***Shazbot! Well then....***

sudo apt-get install libgl1-mesa-dev

The following packages have unmet dependencies:
  libgl1-mesa-dev: 
     Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-0ubuntu16 is to be installed
E: Broken packages

***Huh.... Broken packages? Well then, let's just get rid of libgl1-mesa, and put the right one in....***

sudo apt-get remove libgl1-mesa

The following packages will be REMOVED:
  compiz compiz-gnome compiz-kde fglrx-control freeglut3 gdebi gdm gksu
  gnome-app-install gnome-netstatus-applet gnome-system-monitor
  gnome-volume-manager gstreamer0.8-x hal-device-manager hwdb-client
  libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libgl1-mesa-dri libgle3 libglew1
  libglitz-glx1 libglu1-mesa libglut3 libopengl-perl libqt4-gui
  libqt4-qt3support mesa-utils mozilla-mplayer mplayer mplayer-586
  mplayer-fonts python-gnome2-extras python2.4-gnome2-extras qt4-qtconfig
  rss-glx serpentine update-notifier x-window-system-core xbase-clients
  xdriinfo xorg-driver-fglrx xscreensaver-gl xscreensaver-gl-extra xserver-xgl

***_HELLS NO!!! WTF Can't I just install the dev headers?!?!?_***

It looks like you have added additional repositories for XGL, and that has installed a newer version of mesa. You are shifting the responsibility of providing development headers from the ubuntu repositories to a mix of ubuntu + some other repositories.

Headers required for building GL applications should be available within main. Unfortunately I am at work (on a windows machine), and cannot find what they are called. Usually grabbing the build-deps for something similar will get you what you need. For example, planet penguin racer (I cannot remember the exact name of the package for planet penguin racer, so please substitute):

```
apt-get build-dep planet-penguin-racer
```

---

### Post by rnodal on 2006-08-29
If all the libraries are installed correct then the problem is the command that you are using to compile your programs. Could you provide the command the you are using?

-r

---

### Post by lunarmelody on 2006-09-07
I'm having a similar problem.  I installed what I think are the necessary packages, but when I compile from the command line, it seems that none of my libraries are found.  My code won't compile, nor will the samples in the Mesa demo package.  Here's what I installed, using the Synaptic Package Manager:
freeglut3
freeglut3-dbg
freeglut3-dev
libglu1-mesa
libglu1-mesa-dev
libglui2c2
libglui-dev
libglut3
libglut3-dev
Am I missing anything?

---

### Post by rnodal on 2006-09-08
> **lunarmelody said:**
> I'm having a similar problem.  I installed what I think are the necessary packages, but when I compile from the command line, it seems that none of my libraries are found.  My code won't compile, nor will the samples in the Mesa demo package.  Here's what I installed, using the Synaptic Package Manager:
freeglut3
freeglut3-dbg
freeglut3-dev
libglu1-mesa
libglu1-mesa-dev
libglui2c2
libglui-dev
libglut3
libglut3-dev
Am I missing anything?

That looks find to me. One more time, if the libraries are installed(I think they are) it must be the command then.

-r

---

### Post by lunarmelody on 2006-09-08
What should I be using as a command?  I've just been trying to use either gcc or g++, but do I need an extra argument for linking?

---

### Post by rnodal on 2006-09-08
Well if you use gcc or g++ from the command line then you need to specify where the libraries and include files are. I don't remember the actual command from the top of my head as I use an IDE for programming. I'm at work right now but later I will post how. Mean while you can use google. Try something like "compiling OpenGL appliocations under linux" as your search term. Take care:
-r

---

### Post by kerzane on 2006-12-04
> **lakcaj said:**
> apt-get install build-essential x-window-system-dev

That's usually what I do to grab just about everything I might need.  The reason it is not included by default is that alot of people will never compile anything themselves on a linux box.  So, if you are a programmer, you should be knowledgeable enough to install the required packages yourself.

I have installed build-essential, but can't find x-window-system-dev under apt-get or synaptic. Any idea where it might be? Or an available foolproof alternative. I say this cause I am quite foolish. Edgy 6.10. I'm trying to learn some opengl programming.

Thanks, please help.

---

### Post by az on 2006-12-04
> **kerzane said:**
> I have installed build-essential, but can't find x-window-system-dev under apt-get or synaptic. Any idea where it might be? Or an available foolproof alternative. I say this cause I am quite foolish. Edgy 6.10. I'm trying to learn some opengl programming.

Thanks, please help.

[http://packages.ubuntu.com/edgy/libdevel/libgl1-mesa-dev](http://packages.ubuntu.com/edgy/libdevel/libgl1-mesa-dev)

They are in the universe repo and are not named x-window-system-dev, but xlibs-dev and libgl1-mesa-dev and so forth...

---

### Post by kerzane on 2006-12-05
Thanks azz. Got both of those but still no luck. Incidentally I'm getting minor errors in "graphviz-cairo" everytime I install a new package. Don't know what this means, or what the problem is. When I try to compile my OpenGL program, I'm told I'm missing gltk.h. Do you know where this file should be? Maybe my installs just didn't work. Thanks.

---

### Post by kerzane on 2006-12-05
This is exactly what I get:

Setting up x11proto-xf86misc-dev (0.9.2-3ubuntu1) ...
Setting up libxxf86misc-dev (1.0.1-0ubuntu1) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-3ubuntu1) ...
Setting up libxxf86vm-dev (1.0.1-0ubuntu1) ...
Setting up x11proto-bigreqs-dev (1.0.2-0ubuntu3) ...
Setting up x11proto-fontcache-dev (0.1.2-3ubuntu1) ...
Setting up x11proto-xcmisc-dev (1.1.2-3ubuntu1) ...
Setting up x11proto-xf86bigfont-dev (1.1.2-3ubuntu1) ...
Setting up x11proto-xf86dri-dev (2.0.3-3ubuntu1) ...
Setting up libxaw7-dev (1.0.2-0ubuntu1) ...
Setting up x11proto-gl-dev (1.4.7-1) ...
Setting up xserver-xorg-dev (1.1.1-0ubuntu12) ...
Setting up xorg-dev (7.1.1ubuntu6.1) ...
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo

---

### Post by maniacmook on 2006-12-08
I have read this thread front to back many times and I get this error message that when i run this:

sudo apt-get install build-essential x-window-system-dev

zburdick@iLinux:~/Desktop/wine-0.9.26$ sudo apt-get install build-essential x-window-system-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package x-window-system-dev


so now what shoudl I do.

---

### Post by locutus42 on 2007-01-21
Remember, "stand on the shoulders of giants" and use the "build-dep" feature of apt-get to create your 3D/OpenGL dev env based on what another 3D application used. 

The build-dep directive will go out and get all the packages required for compiling the source package you specify. And if I can, I always like to start with something working and go from there. In this case, you'd want to be able to compile the particular package you picked for the build-dep directive.

one thing I did was search for any opengl games using this:
```
sudo apt-cache search opengl | grep -i game
```

then, I looked at that list to see what might be a very small/simple game so that I'm not building a ton of stuff but using OpenGL just the same. Next, I took a look at what was going to get installed using this( I'm trying trackballs ):
```
sudo apt-get -s build-dep trackballs
```

if that looks good, then remove the "-s" and you should be good.
Oh, and you'll need to enable the "source" trees with synaptic or manually in /etc/apt/sources.list and run the "update" facility to get all the dependencies.
```
sudo apt-get build-dep trackballs
```

It would be nice if there was a HOW-TO for using Ubuntu for development or if one of the 3D developers could pop in. BUT, without that, I believe leveraging "build-dep" is going to be a good way to get started. 

"stand on the shoulders of giants", or just other, mortal, 3D developers. ;-)

One more thing I forgot to mention, You need to get the source for the 3D app and what the heck, have it automatically built too.
```
mkdir ~/openGL-devTest
cd ~/openGL-devTest
sudo apt-get -b source trackballs
```
You should see the source downloaded, built and end up with a bunch of package files in the ~/openGL-devTest directory.
I did and then I installed the two packages required for the trackballs game and then ran the game to see if it worked:
```
sudo dpkg -i ./trackballs_1.1.1-2ubuntu2_i386.deb ./trackballs-data_1.1.1-2ubuntu2_all.deb
sudo apt-get -b source trackballs
trackballs
```

This all worked here on Dapper LTS running the latest ATI driver for the Express 200M graphics card w/OpenGL

---

### Post by DigitEyez on 2007-02-07
> **kerzane said:**
> 
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo

I had the same problem. The solution is posted in this thread: [http://ubuntuforums.org/showpost.php?p=1699820&postcount=2](http://ubuntuforums.org/showpost.php?p=1699820&postcount=2)

---

### Post by arnthorla on 2008-05-28
> **lunarmelody said:**
> I'm having a similar problem.  I installed what I think are the necessary packages, but when I compile from the command line, it seems that none of my libraries are found.  My code won't compile, nor will the samples in the Mesa demo package.  Here's what I installed, using the Synaptic Package Manager:
freeglut3
freeglut3-dbg
freeglut3-dev
libglu1-mesa
libglu1-mesa-dev
libglui2c2
libglui-dev
libglut3
libglut3-dev
Am I missing anything?

I had a similar problem. The solution was really simple, for my problem at least. 

```
cc simple.c -o simple -lGL -lGLU -lglut -lm -lX11
```

Notice: -lGL not [COLOR="Red"]-lgl[/COLOR] and -lGLU not [COLOR="Red"]-glu[/COLOR].

Regards
arnthorla

---

### Post by kospanak on 2008-07-19
Hello. i have a small problem with GLUI. When i compile i have these mistakes:

/usr/include/GL/glui.h:59:19: error: cstdlib: No such file or directory
/usr/include/GL/glui.h:60:18: error: cstdio: No such file or directory
/usr/include/GL/glui.h:61:19: error: cstring: No such file or directory
/usr/include/GL/glui.h:62:18: error: string: No such file or directory
/usr/include/GL/glui.h:63:18: error: vector: No such file or directory
In file included from cubemap.c:10:
/usr/include/GL/glui.h:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘RGBc’
/usr/include/GL/glui.h:240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
/usr/include/GL/glui.h:241: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘&’ token
/usr/include/GL/glui.h:245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI’
/usr/include/GL/glui.h:246: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Control’
/usr/include/GL/glui.h:247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Listbox’
/usr/include/GL/glui.h:248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_StaticText’
/usr/include/GL/glui.h:249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_EditText’
/usr/include/GL/glui.h:250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Panel’
/usr/include/GL/glui.h:251: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Spinner’
/usr/include/GL/glui.h:252: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_RadioButton’
/usr/include/GL/glui.h:253: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_RadioGroup’
/usr/include/GL/glui.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Glut_Window’
/usr/include/GL/glui.h:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_TreePanel’
/usr/include/GL/glui.h:256: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Scrollbar’
/usr/include/GL/glui.h:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_List’
/usr/include/GL/glui.h:259: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Arcball’
/usr/include/GL/glui.h:281: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glui.h:294: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_CB’
/usr/include/GL/glui.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Control’
/usr/include/GL/glui.h:327: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Node’
/usr/include/GL/glui.h:410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Bitmap’
/usr/include/GL/glui.h:441: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_StdBitmaps’
/usr/include/GL/glui.h:471: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Master_Object’
/usr/include/GL/glui.h:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Master’
/usr/include/GL/glui.h:569: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Glut_Window’
/usr/include/GL/glui.h:607: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Main’
/usr/include/GL/glui.h:759: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Control’
/usr/include/GL/glui.h:956: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Button’
/usr/include/GL/glui.h:1005: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Checkbox’
/usr/include/GL/glui.h:1061: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Column’
/usr/include/GL/glui.h:1095: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Panel’
/usr/include/GL/glui.h:1139: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_FileBrowser’
/usr/include/GL/glui.h:1203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Rollout’
/usr/include/GL/glui.h:1261: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Tree’
/usr/include/GL/glui.h:1361: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_TreePanel’
/usr/include/GL/glui.h:1428: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Rotation’
/usr/include/GL/glui.h:1429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Translation’
/usr/include/GL/glui.h:1435: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI’
/usr/include/GL/glui.h:1579: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_EditText’
/usr/include/GL/glui.h:1697: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_CommandLine’
/usr/include/GL/glui.h:1747: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_RadioGroup’
/usr/include/GL/glui.h:1784: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_RadioButton’
/usr/include/GL/glui.h:1825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Separator’
/usr/include/GL/glui.h:1858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Spinner’
/usr/include/GL/glui.h:1951: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_StaticText’
/usr/include/GL/glui.h:1977: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_TextBox’
/usr/include/GL/glui.h:2080: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_List_Item’
/usr/include/GL/glui.h:2093: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_List’
/usr/include/GL/glui.h:2200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Scrollbar’
/usr/include/GL/glui.h:2313: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Listbox_Item’
/usr/include/GL/glui.h:2320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Listbox’
/usr/include/GL/glui.h:2390: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Mouse_Interaction’
/usr/include/GL/glui.h:2436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Rotation’
/usr/include/GL/glui.h:2491: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLUI_Translation’
cubemap.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cubemap.c: In function ‘gl’:
cubemap.c:375: error: ‘glui_subwin’ undeclared (first use in this function)
cubemap.c:375: error: (Each undeclared identifier is reported only once
cubemap.c:375: error: for each function it appears in.)
cubemap.c:375: error: ‘GLUI_Master’ undeclared (first use in this function)
make: *** [cubemap.o] Error 1

What could be the problem?

---

