---
title: "How to install a linux software package"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by tripower on 2010-04-12
Please tell me that Ubuntu/Linux provide some sort of executable versions for installing software packages? Because I have been looking at some software downloads (TightVNC for example) which just supply a bunch of source code modules. What is the average user suppose to do with this stuff?

---

### Post by Chronon on 2010-04-12
Whenever possible, it's best to seek software from the repositories.  You can use the package manager (either Synaptic or Software Center) to find and install it.

The following should be available in the repositories:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tightvnc](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tightvnc)
```
Package tightvnc-java

    * dapper (web): TightVNC java applet and command line program [multiverse]
      1.2.7-3: all
    * hardy (web): TightVNC java applet and command line program [multiverse]
      1.2.7-4: all
    * intrepid (web): TightVNC java applet and command line program [multiverse]
      1.2.7-6: all
    * jaunty (web): TightVNC java applet and command line program [multiverse]
      1.2.7-6: all
    * karmic (web): TightVNC java applet and command line program [multiverse]
      1.2.7-8: all
    * lucid (web): TightVNC java applet and command line program [multiverse]
      1.2.7-8: all

Package tightvncserver

    * dapper (x11): virtual network computing server software [universe]
      1.2.9-8ubuntu2: amd64 i386 powerpc
    * hardy (x11): virtual network computing server software [universe]
      1.2.9-22: amd64 i386
    * intrepid (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * jaunty (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * karmic (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * lucid (x11): virtual network computing server software [universe]
      1.3.9-6: amd64 i386

Package xtightvncviewer

    * dapper (x11): virtual network computing client software for X [universe]
      1.2.9-8ubuntu2: amd64 i386 powerpc
    * hardy (x11): virtual network computing client software for X [universe]
      1.2.9-22: amd64 i386
    * intrepid (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * jaunty (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * karmic (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * lucid (x11): virtual network computing client software for X [universe]
      1.3.9-6: amd64 i386

```

---

### Post by drreed on 2010-04-12
I don't know anything about TightVNC, but the average user (hmmm wonder who that is) should probably stick with apt-get unless there is a reason not to.

For example, lets say I hear about something called "Wireshark" thats available for Linux, and wonder if I can get it on my Ubuntu distro, without compiling or anything, ok?

First, I want to see if it's available:

$sudo apt-cache search wireshark

This will return a list of every package available in your repositories with the occurence of the characters "wireshark" in it's description or name. If I wasn't sure how they spelled it in the article I read, I might just try "iresh" or "wire". Which may return a lot of things.

Scroll up through your listing (in your command window) studying each one until you find one that looks like what you want. Usually there is more than one file. The development (source) will be in a package, plus maybe some libraries that are designed especially for wireshark (they come up too because it matched the word)

You can look at it and tell which one you need usually.

Be aware that sometimes things conflict. I find this in audio stuff all the time. Some things are written for Gnome, some for KDE.  If you use KDE, then guess what will happen if you install a gnome app? (they frequently begine with a g - so if there was a special gnome version of wireshark, it might be called gwireshark, and KDE  gui apps usually begin with a K) It will download all the dependencies needed, which maybe a bunch of gnome stuff. ONce I was fooling around with audio stuff, rebooted, and logged into a entirely new desktop environment! Don't knwo what I did, it was late and I was tired I guess.

OK - so you found your wireshark and want to install:

#sudo apt-get install wireshark

it should return a message that it completed successfully when it's done. (This is where you'll get errors if there's a conflict with your libraries

If you screw up, or just decide you don't want it anymore, just:

#sudo apt-get remove wireshark

I often follow it up with:

$sudo apt-get autoremove

That gets any unneeded packages off your system. (ran into that scenario last night when I tried to install virtualbox-ose (you don't want that one - you want the one at teh Sun website, the ose installs the development files, which don't come off with remove, you have to use the autoremove command. If you don't and try to install the other one, it complains loudly and exits, because virtualbox-dev is already on your system.

Another strategy:

Go to your menus and find "add/remove software", run it
Find what you need in the list (it has a search/grep field up top to help you locate software that does certain things, like "torrent" will list everything related to torrents,) and you can choose the P2P you want to try.

Another strategy:

Search the forums for "installing software" and "updating software" I think there are guides or tutorials here, and many of them are application specific. (especially for things that require tweaking after the install finishes)

Trust me, once you get the hang of this you'll wonder why anyone would buy MS Windows, for anything.

Hope this helps

---

### Post by tripower on 2010-04-13
> **Chronon said:**
> Whenever possible, it's best to seek software from the repositories.  You can use the package manager (either Synaptic or Software Center) to find and install it.

The following should be available in the repositories:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tightvnc](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=tightvnc)
```
Package tightvnc-java

    * dapper (web): TightVNC java applet and command line program [multiverse]
      1.2.7-3: all
    * hardy (web): TightVNC java applet and command line program [multiverse]
      1.2.7-4: all
    * intrepid (web): TightVNC java applet and command line program [multiverse]
      1.2.7-6: all
    * jaunty (web): TightVNC java applet and command line program [multiverse]
      1.2.7-6: all
    * karmic (web): TightVNC java applet and command line program [multiverse]
      1.2.7-8: all
    * lucid (web): TightVNC java applet and command line program [multiverse]
      1.2.7-8: all

Package tightvncserver

    * dapper (x11): virtual network computing server software [universe]
      1.2.9-8ubuntu2: amd64 i386 powerpc
    * hardy (x11): virtual network computing server software [universe]
      1.2.9-22: amd64 i386
    * intrepid (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * jaunty (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * karmic (x11): virtual network computing server software [universe]
      1.3.9-4: amd64 i386
    * lucid (x11): virtual network computing server software [universe]
      1.3.9-6: amd64 i386

Package xtightvncviewer

    * dapper (x11): virtual network computing client software for X [universe]
      1.2.9-8ubuntu2: amd64 i386 powerpc
    * hardy (x11): virtual network computing client software for X [universe]
      1.2.9-22: amd64 i386
    * intrepid (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * jaunty (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * karmic (x11): virtual network computing client software for X [universe]
      1.3.9-4: amd64 i386
    * lucid (x11): virtual network computing client software for X [universe]
      1.3.9-6: amd64 i386

```


OK I tried to download and I get the following: "You are recommended to install the software from the channel instead."
So where do I download this package?

---

