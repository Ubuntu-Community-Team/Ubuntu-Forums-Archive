---
title: "[SOLVED] ./configure error"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Arcnsparc on 2008-04-09
I am installing "Music Applet 2.3.0" and get this error during ./configure :

error: could not find pygtk-codegen-2.0 script

I am running Gutsy on an thinkpad R60.  I had an error about python dev stuff being missing but i installed all of the with apt-get.  Any advice on how to get this script and get it in the right place would be appreciated.  The tarball i am using is 
[http://www.kuliniewicz.org/music-applet/downloads/music-applet-2.3.0.tar.gz](http://www.kuliniewicz.org/music-applet/downloads/music-applet-2.3.0.tar.gz)
which I got from the Music Applet site.  THANKS

---

### Post by ibutho on 2008-04-09
Install python-gtk2-dev and see if that helps resolve the problem.

---

### Post by Arcnsparc on 2008-04-09
Holy moly!

So i was installing:
pygtk-2.12.1.tar.gz  
from here:
[http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/](http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/)

and i got THIS!:

checking for PYGOBJECT... configure: error: Package requirements (pygobject-2.0 >= 2.14.0) were not met:

No package 'pygobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGOBJECT_CFLAGS
and PYGOBJECT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Now I am super confused!  I am betting that it is an easy fix though, it doenst look too scary.

(and I am very impressed at the 3 minute response time to the first post... strong work)

---

### Post by ibutho on 2008-04-09
How about just using the packages in the Ubuntu repositories? pygtk is the same package as python-gtk2 which I mentioned above. pygobject is the same as python-gobject which is also in the Ubuntu repositories. If you want to install all the files required to build/compile apps that rely on python, then install python-all-dev.

---

### Post by mikewhatever on 2008-04-09
Have you tried <sudo apt-get install python-gtk2-dev>? That package is in the repositories.

---

### Post by Arcnsparc on 2008-04-09
I got my hopes up! I did this as instructed:

sudo apt-get install python-all-dev

and that went well, so I tried to ./configure in the tar install folder and it went through most of the checks and then i got this guy again!

checking for headers required to compile python extensions... found
checking for pygtk-codegen-2.0... no
configure: error: could not find pygtk-codegen-2.0 script

Do you think I have it but its in the wrong path or that the ./configure file doesnt know where to look?  Im kinda new to linux still but it makes WAY more sense than windows, so I can kinda guess at it...

---

### Post by Arcnsparc on 2008-04-09
> **mikewhatever said:**
> Have you tried <sudo apt-get install python-gtk2-dev>? That package is in the repositories.

I tried that and then ./configure again and got this bad boy:

      gtk+-2.0
        libpanelapplet-2.0
        pango >= 1.6
        pygtk-2.0
        gnome-python-2.0
) were not met:

No package 'libpanelapplet-2.0' found
No package 'gnome-python-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUSICAPPLET_DEPS_CFLAGS
and MUSICAPPLET_DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I dont know a lot but that looks bad in my book hahaha

---

### Post by Arcnsparc on 2008-04-09
SOOOOooo.....

I am still working on it and its fun but giving me trouble yet!

I tried to set the PKG_CONFIG_PATH like this:

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

then

export PKG_CONFIG_PATH

I did this according to this guy: [http://www.linuxquestions.org/questions/linux-software-2/pkgconfigpath-230545/](http://www.linuxquestions.org/questions/linux-software-2/pkgconfigpath-230545/)
and i verified that my pkg_config file was at usr/bin and was an executable.

I still got the same error from the ./configure script:

checking for MUSICAPPLET_DEPS... configure: error: Package requirements (
        gtk+-2.0
        libpanelapplet-2.0
        pango >= 1.6
        pygtk-2.0
        gnome-python-2.0
) were not met:

No package 'libpanelapplet-2.0' found
No package 'gnome-python-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUSICAPPLET_DEPS_CFLAGS
and MUSICAPPLET_DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I guess now I have to alter the configure scirpt right?  This is getting heavy fast but its good for my linux muscles for sure.

---

### Post by mikewhatever on 2008-04-10
Well, both packages are also in the repositories, install them with <sudo apt-get install libpanel-applet2-dev python-gnome2-dev>. You have to install all dependencies to successfully compile something. If you get errors of more packages missing, open Synaptic and search for them, the names might be slightly different though.
You probably know it, but I'll mention any way, Music Applet 2.2.0 is also in the repositories and can be installed <sudo apt-get install music-applet>. It's an older version and might not have all the features of the current one.

---

### Post by Arcnsparc on 2008-04-11
> **mikewhatever said:**
> Well, both packages are also in the repositories, install them with <sudo apt-get install libpanel-applet2-dev python-gnome2-dev>. You have to install all dependencies to successfully compile something. If you get errors of more packages missing, open Synaptic and search for them, the names might be slightly different though.
You probably know it, but I'll mention any way, Music Applet 2.2.0 is also in the repositories and can be installed <sudo apt-get install music-applet>. It's an older version and might not have all the features of the current one.



Thank you so much, that all worked just fine and now i have the app!  Only one problem left and that is this:

configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop
configure: WARNING: MPD support is disabled because the following Python modules could not be found:
configure: WARNING:     * mpdclient2
configure: WARNING: XMMS1 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmms
configure: WARNING: XMMS2 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmmsclient

which happened during install.  I use amarok so this is a bummer.  Im trying to find a solution, im going to try and install the modules..... I have no idea what that is, but im sure I will after a few rounds Me VS Google.  Thanks!

---

### Post by Arcnsparc on 2008-04-11
So I tried to do this:

sudo apt-get install kdecore

which did what it should, then I tried to install the music applet again via aptget (didnt work for amarok) then i tried by using the tarball ./configure and i still got this error:

configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop

Im lost on what to do!  I you be so grateful for any advice, I LOVE Amarok, its made me like my music again and I really want to get Music-applet working with it so I can persuade them into linux :)

---

### Post by Arcnsparc on 2008-04-11
I found a similar thread over here:
[http://ubuntuforums.org/showthread.php?p=4699190#post4699190](http://ubuntuforums.org/showthread.php?p=4699190#post4699190)
but i dont understand what they are saying...
If anyone could break this down for a newbie that would be super cool....

---

### Post by y-lee on 2008-04-11
It looks like you are missing some python modules

Install python-kde3 and python-kde3-dev and python-dcop

As far as i can tell that should take care of 

> onfigure: WARNING: * kdecore
configure: WARNING: * pcop
configure: WARNING: * pydcop

Let me know I'm not running gusty so i going by google and oddly i can't connect to ubuntu packages web site now :confused: it is down or lost in some cyber black hole :lolflag:

---

### Post by Arcnsparc on 2008-04-11
Thanks y-lee,  those suggestions worked like a charm, I got it installed and everything went smoothly.  It does however, crash upon opening when configured to amarok so I am giving up on getting this thing working.  Ill try again in a few months when there are more bugs worked out.  Thanks for the help!

---

### Post by y-lee on 2008-04-11
So it compiled but its crashing??

Anyway if ya try again and have problems let us know. We all try to help here :)

---

### Post by Arcnsparc on 2008-04-12
I think it might be because it is a KDE app and Im using gnome.....  Im sure it will work after more bugs are hammered out.

---

### Post by Arcnsparc on 2008-06-14
I got it to work with all of the players by doing this:

Sudo apt-get build-dep music-applet

which added 100MB of files to my build, and for good measure i did that with amarok too.  After that it works fine!

---

