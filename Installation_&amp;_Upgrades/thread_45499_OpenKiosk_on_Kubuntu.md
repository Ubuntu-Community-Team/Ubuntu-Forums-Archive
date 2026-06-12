---
title: "OpenKiosk on Kubuntu"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by webray on 2005-06-30
OpenKiosk is an open-source multi-platform kiosk system.
I'm working on Kubuntu 5.04. The (server) nodeview is still running on my testsystem. Nodeview needs Qt version 3.x and a Berkeley DB, additional X11 for the Client.

The (client) kdex11client is not running.

./configure,
make and a
sudo make install worked ...

but not good enough i think. 

Here is a part out of the documentation of kdex11client: 
[COLOR=Sienna]"... After you have installed this plugin to the kde system directory of the client computer, re-login to the kde desktop. Right click somewhere on the panel (kicker). Select add -> applet menu and select kdeX11client ..."[/COLOR]

i cannot integrate the kdex11client in my kde-panel. There is always this standard-error-message "kdex11client cannot load. Please check your Installation"

Furthermore i read somewhere else about 2 files named libkdexclient11.la and 
libkdex11client.so. I cannot find them.

Perhaps anyone also installed OpenKiosk on a Kubuntu-System. :|

---

### Post by ltmon on 2005-06-30
I haven't tried this, but maybe you can recompile like this:

> sudo apt-get install checkinstall
> ./configure --prefix=/usr
> make
> sudo checkinstall -D make install

The only really different part that's important is the --prefix=/usr.  This is usually necessary for kde applications on Ubuntu and Debian.

The rest of it makes a debian package instead of simply installing it.  This will make it easier for you to uninstall it, reinstall it and install it on multiple PC's.

Cheers,

L.

---

### Post by webray on 2005-07-01
Thanks ltmon .. i'm sure, i can use this for my next compilation.
Yesterday i found another way.

This Guidance based on a fresh installed Kubuntu 5.04:

[COLOR=DarkOrange]-	sudo apt-get install gcc g++[/COLOR]

x includes
[COLOR=DarkOrange]-	sudo apt-get install xlibs-dev[/COLOR]

qt3
[COLOR=DarkOrange]-	sudo apt-get install libqt3-dev
-	sudo apt-get install libqt3-mt-dev[/COLOR]

kde-headers
[COLOR=DarkOrange]-	sudo apt-get install kdebase-dev[/COLOR]

Edit the file “~/kdex11client*/src/network“. There you have to fill in the IP and the Port of your Nodeview-Server. Now you can start.

[COLOR=DarkOrange]-	./configure
-	sudo make
-	sudo make install[/COLOR]

Change to directory “~/kdex11client*/src/”:
[COLOR=DarkOrange]-	sudo cp kdex11client.desktop /usr/share/apps/kicker/applets/ [/COLOR]

change now to the following directory “~/kdexclient*/src/.libs/”:
[COLOR=DarkOrange]-	sudo cp libkdexclient11.la /lib and /usr/lib 
-	sudo cp libkdex11client.so /lib and /usr/lib [/COLOR]

Then you have to restart your KDE-Desktop.
Now right-click on your KDE-Panel and integrate the kdex11client. Your station is locked ;-)

Another Question: I copied the .la and .so-files to /lib and /usr/lib.
But its enough to copy them to /usr/lib, or ...?

---

### Post by naktu on 2007-08-04
I have problem installing openkiosk in kubuntu. Now I manage to install and make it run. I am using opkdekiosk2.0.6. And I have some advise.

1) If you using windowxp as a server please setup IP for your client pc.
2) Follow above step. Install g++, xlibs-dev, libqt3-mt-dev, and kdebase-dev but before install you need to create new folder at /usr/share/

> sudo mkdir /usr/share/config

3) Start install

> ./configure --prefix=/usr
> sudo make
> sudo  make install

---

