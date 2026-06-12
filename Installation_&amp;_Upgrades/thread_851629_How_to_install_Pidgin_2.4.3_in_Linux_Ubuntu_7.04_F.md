---
title: "How to install Pidgin 2.4.3 in Linux Ubuntu 7.04 Feisty Fawn by compiling its source"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by zidkenu on 2008-07-06
:lolflag:How to install Pidgin 2.4.3 in Linux Ubuntu 7.04 Feisty Fawn by compiling its source code(to compile Pidgin source code)

First, remove Gaim by MainMenu-> Add/Remove-> Gaim

Use synaptic to install the required packages...
search for libgtk2.0  -> to install libgtk2.0-0 and libgtk2.0-dev
search for gstreamer0.10 -> to install libgstreamer0.10-0 libgstreamer0.10-dev  libgstreamer0.10-plugins-good    libgstreamer0.10-plugins-ugly
libgstreamer0.10-plugins-bad      libgstreamer0.10-plugins-ffmpeg
search for gtkspell -> to install libgtkspell0 and libgtkspell-dev

Open a terminal by MainMenu > Accessories > Terminal
Download pidgin-2.4.3.tar.bz2 from Pidgin website
Unzip/extract pidgin-2.4.3.tar.bz2 into a foler called pidgin-2.4.3 by 
double clicking on tar.bz2 file-> click on Extract button-> Extract
Put that folder on your Desktop
Then type the commands (without "# ")
# cd Desktop/pidgin-2.4.3
# ./configure

Then if you encounter the following message...
quote "XScreenSaver extension development headers not found. 
Use --disable-screensaver if you do not need XScreenSaver extension support, this is required for detecting idle time by mouse and keyboard usage. 
" end of quote
Open Synaptic and search for "xscreensaver"
Then I found a package called "xscreensaver", but it had no its dev file, so I had to skip that support by enter the following in the terminal...
# ./configure --disable-screensaver

Then if you encounter the following message...
quote "Startup notification development headers not found.
Use --disable-startup-notification if you do not need it.
" end of quote
Open Synaptic and search for "startup notification"
Install libstartup-notification0 and its dev file libstartup-notification0-dev
Then run the same command again ...
# ./configure --disable-screensaver

Meanwhile development headers not found.
Use --disable-meanwhile if you do not need meanwhile (Sametime) support.
-> synaptic search: meanwhile -> install Meanwhile and its dev

avahi development headers not found.
Use --disable-avahi if you do not need avahi (Bonjour) support.
-> synaptic search: avahi bonjour
libavahi-compat-libdnssd-dev  for 
Development headers for the Avahi Apple Bonjour compatibility library
is not the one I need, 
so I give up by adding "--disable-avahi" after ./configure 
# ./configure --disable-screensaver --disable-avahi

D-Bus development headers not found.
Use --disable-dbus if you do not need D-Bus support.
-> libdbus-1-dev, simple interprocess messaging system (development headers) is not the one, so I put down "... no" here.

Perl development headers not found.
Use --disable-perl if you do not need Perl scripting support.
-> libperl-dev, Perl library: ... yes

Neither GnuTLS or NSS SSL development headers found.
Use --disable-nss --disable-gnutls if you do not need SSL support.
MSN, Novell Groupwise and Google Talk will not work without GnuTLS or NSS. OpenSSL is NOT usable!
-> libgnutls-dev, the GNU TLS library - development files...yes

Tcl development headers not found.
Use --disable-tcl if you do not need Tcl scripting support.
-> tcl8.4-dev, Tcl (the Tool Command Language) v8.4 - development files... yes

Tk development headers not found.
Use --disable-tk if you do not need Tk scripting support.
-> tk8.4-dev, Tk toolkit for Tcl and X11, v8.4 - development files...yes

So eventually, the command becomes ...
# ./configure --disable-screensaver --disable-avahi --disable-dbus
Then I followed the README and INSTALL files inside pidgin-2.4.3 folder..
# sudo make
# make check
# sudo make install
# make clean
# make distclean
# pidgin or # finch
or MainMenu > Internet > Pidgin

---

### Post by xiongnu on 2010-11-18
a precise and concise step-by-step instruction! works wonder!  it solved the sticky point that bothered me for so long on ubuntu:P

now i got all the IM working on my machine!

one question:  I downloaded the latest Pidgin version 2.7.5. at one point during compiling, it prompts whether i want to have voice and and video chat capability included.  i checked the dependency and had the necessary files installed.  but it still asked for files even though they're already there.  so i ended up with no voice and video.  

so is the voice and video chat really possible under ubuntu?  or i miss sth here.:KS

---

### Post by sikander3786 on 2010-11-19
> **xiongnu said:**
> a precise and concise step-by-step instruction! works wonder!  it solved the sticky point that bothered me for so long on ubuntu:P

now i got all the IM working on my machine!

one question:  I downloaded the latest Pidgin version 2.7.5. at one point during compiling, it prompts whether i want to have voice and and video chat capability included.  i checked the dependency and had the necessary files installed.  but it still asked for files even though they're already there.  so i ended up with no voice and video.  

so is the voice and video chat really possible under ubuntu?  or i miss sth here.:KS
Hi.

This is a really old thread as you see dated 2008.

And it was intended for Ubuntu 7.04 and support period for 7.04 desktop is over.

Which version are you running?

It would be better to start a new thread with all the hardware/software details.

Regards.

---

### Post by xiongnu on 2010-11-19
see my signature):P

---

### Post by sikander3786 on 2010-11-19
Are you still using 7.04?

You hardware doesn't let you run newer version of Ubuntu?

---

### Post by Dinjy on 2011-12-26
> **xiongnu said:**
> a precise and concise step-by-step instruction! works wonder!  it solved the sticky point that bothered me for so long on ubuntu:P

now i got all the IM working on my machine!

one question:  I downloaded the latest Pidgin version 2.7.5. at one point during compiling, it prompts whether i want to have voice and and video chat capability included.  i checked the dependency and had the necessary files installed.  but it still asked for files even though they're already there.  so i ended up with no voice and video.  

so is the voice and video chat really possible under ubuntu?  or i miss sth here.:KS

First of all [download pidgin]("http://www.downloadpidgin.org") from its website through the internet than double click on its .exe. after giving some easy instruction it will be installed successfully.

---

### Post by oldos2er on 2011-12-26
Closed, necromancy.

---

