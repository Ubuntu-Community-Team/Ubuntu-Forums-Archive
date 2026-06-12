---
title: "Gambas3"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by eaglemob on 2010-04-26
Hi there,
I am using desktop ubuntu 10.04 Lucid. On a 64 bits !!

I would like to install Gambas3 or the last svn version.

The problem is, i am NOOB and i don't like install trough the terminal.
Could anyone plz link me a version of gambas3 or the last svn for 64bits .deb ?

Any help apreciated,

Thx.

---

### Post by oldfred on 2010-04-26
I do not see Gambas3 on their web site?

If you are just starting out it is much better just to download the version that is in synaptic as that will work in your version of Ubuntu.

---

### Post by kbielefe on 2010-04-26
Gambas3 is a development version.  There isn't a .deb yet because developers don't use them.  Learning to compile large Linux projects is a useful skill, especially since you are looking into a programming language.  No time like the present to learn that skill.

---

### Post by eaglemob on 2010-04-26
Compiling i think will be np, but what comes after is were i get stuck.

In terminal i did this:
eaglemob@eaglemob-desktop:~$

$ mkdir trunk
$ svn checkout [https://gambas.svn.sourceforge.net/svnroot/gambas/gambas/trunk/](https://gambas.svn.sourceforge.net/svnroot/gambas/gambas/trunk/)
$ cd trunk
$ ./reconf-all

After this i am stuck, but i will try to figure out.
Were does it compile to ? what directory ?
Compiling doesn't mean is installed with gui and everything, or does it ?=Noob questions :confused:

Sorry for those questions. I am just use to desktop, and i managed so far to install everything. But wen comes to compiling i don't dare to mess up in terminal :).

Thx all for the replays.

Ps. i think svn version is 2.9x but i am not sure.

---

### Post by kalaharix on 2010-04-27
Hi

In theory you just now do the standard:
sudo ./configure -C
sudo make
sudo make install

I have just tested this and had a problem. Bear in mind that both UB10.04 and Gambas2.99 are development version and something may have changed in the week since I last did an install. Or maybe I am just being a numpty somewhere. I will test on a fresh install and come back to the forum.

---

### Post by eaglemob on 2010-04-27
Re,

I am gonna try to compile and install again. Because last night the install didn't went as
suppose to be :(

This time as root.

And yea Kalaharix you are right, both UbT10.04 and gambas2.99 are still to fresh.

Well one day this will work :)
I will be back if i find some use full info. 

Cya, thx

---

### Post by eaglemob on 2010-04-27
This site, may help someone as me.
[http://gambasdoc.org/help/readme](http://gambasdoc.org/help/readme)

./configure -C

So far so good, but still one error..
.
.
.
checking for Desktop-neutral routines headers... (cached) 
checking for Desktop-neutral routines libraries... (cached) 
checking for Gnome desktop routines component with pkg-config... no
configure: WARNING: *** Gnome desktop routines is disabled
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/gnome/Makefile
.
.
.
ALL COMPONENTS WILL BE COMPILED.

Just that WARNING, i don't know if is important or not.

Now is just to try to install and make it work on Gnome Desktop ..auch :).

To be continued !!

Gtx

---

### Post by eaglemob on 2010-04-27
Good news !!!
Gambas2.99 works on Ubt10.04.   64 bits.
Just some small things that need to be tested.

Soon or later i will post what i did.

c ya

Ps i will mark this thread as *SOLVED*!!

---

### Post by kalaharix on 2010-04-28
Hi

well done. I am still struggling. Used sudo apt-get install intltool and that got me almost there but also had the same warning message. Gambas3 now loads but won't let me start a new project. Loading an existing project loads the form as text not graphically.

Looking forward to how you did it!

---

### Post by eaglemob on 2010-04-28
> **kalaharix said:**
> Hi

well done. I am still struggling. Used sudo apt-get install intltool and that got me almost there but also had the same warning message. Gambas3 now loads but won't let me start a new project. Loading an existing project loads the form as text not graphically.

Looking forward to how you did it!

Then you are missing something. I will post exactly how i did. Some small tutorial.

I will warn you gambas 2.99 is not Project compatible with previous versions like 2.19.
You can not load project from other versions..well at least not yet..maybe in the future will.

Cya l8terz.

---

### Post by eaglemob on 2010-04-28
Here is how i installed gambas 2.99 on Ubuntu 10.04 x64

Installing gambas SVn on UBT10.04

1:From karmic 9.10, we gonna use this libs listed down and the necessary files for the installation in ubt10.04. This can be found on this page:

[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

In terminal:
sudo apt-get install build-essential autoconf libbz2-dev libfbclient2
libmysqlclient15-dev unixodbc-dev libpq-dev libsqlite0-dev
libsqlite3-dev libgtk2.0-dev libldap2-dev libcurl4-gnutls-dev
libgtkglext1-dev libpcre3-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev
libsdl-image1.2-dev libsage-dev libxml2-dev libxslt1-dev libbonobo2-dev
libcos4-dev libomniorb4-dev librsvg2-dev libpoppler-dev
libpoppler-glib-dev libasound2-dev libesd0-dev libesd-alsa0
libdirectfb-dev libaa1-dev libxtst-dev libffi-dev kdelibs4-dev
firebird2.1-dev libqt4-dev libglew1.5-dev libimlib2-dev libv4l-dev
libsdl-ttf2.0-dev
----------------------------------------------------------------------------------------
2:making the directory,downloading and configuring everything.

$ mkdir trunk
$ svn checkout [https://gambas.svn.sourceforge.net/svnroot/gambas/gambas/trunk/](https://gambas.svn.sourceforge.net/svnroot/gambas/gambas/trunk/)
$ cd trunk
$ ./reconf-all
----------------------------------------------------------------------------------------
3: Analyzing the configuration.

$ ./configure -C

If comes a *Warning* on the terminal output, then something is missing !!!
I advise to scroll the terminal log to see if exist any *WARNING*
---------------------------------------------------------------------------------------
4:If there is no error then we go to next step . compiling.

$ make
----------------------------------------------------------------------------------------
Now if everything went good with no error we are going to install !!!
----------------------------------------------------------------------------------------
5:Installing !! (ROOT ONLY or Gambas will NOT install !!)

$ su -c "make install"

This above will ask for the root password, depending if are already root or not!!
----------------------------------------------------------------------------------------
Additional:!!!
For exemple, if the configuration gived many erros you can reconfigure again.

$ ./reconf
----------------------------------------------------------------------------------------
To start gambas

In terminal type in gambas2 or gambas3 depending what package you installed
----------------------------------------------------------------------------------------
Extra information on the site below
[http://gambasdoc.org/help/readme?view](http://gambasdoc.org/help/readme?view)

have fun,
grtx

---

### Post by holocronweaver on 2012-03-23
For those who find this old post as a top search result for Ubuntu & Gambas3, note that there is (as of this writing) still no official package for Gambas3 but there is a PPA:

ppa:nemh/gambas3

BTW, Gambas 3 is now officially released so hope it makes it into the Precise repos soon...

---

