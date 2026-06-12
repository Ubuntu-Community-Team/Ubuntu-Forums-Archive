---
title: "I Can Never Install Anything With Terminal!?!"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by MotoX-450 on 2008-08-09
I have never ever ever been able to install anything through the terminal.  I always have to use synaptic package manager and if it does not show up in the manager then I get really upset.  Here is my experience with TRYING to install Kiba Dock:

To check out kiba-dock from the Sourceforge server run:
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk) kiba
You will find all kiba related Software in the kiba Directory

So I did and navigated to the directory of kiba in Terminal and followed the directions of the "README"
Here is what the "README" say:
-------------------------
** Building **

./autogen.sh
make
make install (as root)
or
sudo make install
------------------------



so here is what I get when I try:
------------------------------
owner@usb-laptop:~/Desktop/kiba/kiba-dock$ ./autogen.sh

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:26: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running 'glib-gettextize'... Ignore non-fatal messages.
./autogen.sh: 50: glib-gettextize: not found
owner@usb-laptop:~/Desktop/kiba/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
owner@usb-laptop:~/Desktop/kiba/kiba-dock$ sudo make install
make: *** No rule to make target `install'.  Stop.
owner@usb-laptop:~/Desktop/kiba/kiba-dock$
--------------------------------------------------
I always get stuck at "Make" every single time I want to install something.  What am I doing wrong??

---

### Post by Parp on 2008-08-09
just a newbie observation, it's complaining about glib, do you have all the dependancies installed?

I found this, it might be a bit more useful.

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by mikjp on 2008-08-09
> **MotoX-450 said:**
> 
I always get stuck at "Make" every single time I want to install something.  What am I doing wrong??

You have to take care of dependencies. You have to install the libraries mentioned in the error message you copied here.

mikko

---

### Post by |Eric| on 2008-08-09
well i dont know what you whant to install but 
source needs to be compiled


usualy in the package unzipped folder:  (yes .tar.gz or .bz2 files are zipped files!)```


 ./configure       << this is for configuring compiling instruction (ususaly ./configure --help  gives available options)
make               << this is for compiling 
make install       << this is for installing

```

in order for this to work (as mentioned above) you need to have all the dependencies installed 

also not that this is valid only for source packages (.tar.gz or .tar.bz2  files )
& you need to install the proper Devlopment packages first!

to install in the comand line the proper replacement for Synaptics is "apt-get" application 

usualy goes like this

```

~$ apt-get install my_insane_program_i_whant_to_install

```

minimum requirement for compiling source is glibc, gcc & make (make as lots  of variants i usualy install automake as its a comon package)

also note that gcc is only for C programing language you may need other compilers /interpreter depending on the source 's language of programation



NOTE: its complaining a bit about the glib glib-gettextize fucntion but its not there that it stalls 
its actualy saying that there is "no Makefile found" meaning you cant use the make program to compile in that directory as its not finding the "Makefile" file

do a "ls" command to see if there is indeed a "Makefile" 
also check that your in the sources directory

ex:```
/media/sdc/my_insane_program0.0.1$ ls
Makefile
insane.c
./configure
```

also "pwd"gives you your curent dir so :
```
~$ pwd 
/media/sdc/my_insane_program0.0.1
```

---

### Post by mc4man on 2008-08-10
Start by installing gettext in synaptic.
Here are the rest (maybe, if not ck. your errors.

```
You need the following to build the Akamaru physics engine:

    * automake
    * autoconf
    * gcc
    * libtool
    * intltool >= 0.35.0
    * gettext 

You need the following to build kiba-dock itself:

    * glib2 >= 2.12
    * gtk2 >= 2.10
    * cairo >= 1.0.0
    * libxml-2.0
    * pango >= 1.10.0
    * Optional depends:
           librsvg > 2.14.4 (for SVG support)
           glitz >= 0.5.3
           akamaru (for physics) 


You will need the following to build various kiba-plugins:

    * Dbus plugin
           dbus
           pygtk2-devel (to build the actual Dbus plugins, located in the kiba-dbus-plugins directory) 

    * Gmenu plugin
           libgnome-menu 

    * Stack plugin
           libgnomeui-2.0 > 2.0.0
           libgnomevfs > 2.0.0 

    * Sysinfo plugin
           libgtop > 2.0.0 

    * Trash plugin 
          libgnomevfs > 2.0.0
```

You can search most in synaptic by shown name though some will be prefaced with lib. Ex. - libglib2.0, libgtk2.0 , ect.
You should have already installed  build-essential

---

### Post by MotoX-450 on 2008-08-10
Thank you all sooo much for the time you spent answering my question.  The whole purpose I wanted kiba-dock is because I NEED a "portable" pc (installed on an 8GB flash drive).  And if I plug it into a random pc, compiz does not work.  I have Avant-Window-Navigator but it does not work without compiz pc.  I was pretty sure kiba-dock did not need compiz.  But it looks like compiz is required from reading [***_[COLOR="Red"]THIS POST[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=554127").

What I really need is "SLIMDOCK" which is mentioned [***_[COLOR="Red"]HERE[/COLOR]_***]("http://www.internetling.com/2008/03/24/linux-docks-5-mac-os-x-docks-for-ubuntu-and-other-linux-distros/").

See this is why Linux cannot keep up with M$ and M@C.  Why cant programmers just program everything to be just a single executable file to install things?  I am trying so hard to switch from M$ to linux but it is hard.

Any ideas how I can install Slimdock or some other way to have a dock without compiz?

---

