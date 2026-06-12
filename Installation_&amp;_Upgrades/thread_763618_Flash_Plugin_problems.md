---
title: "Flash Plugin problems"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Hellishcross on 2008-04-23
Hi everyone... today is my first day using linux... I was trying to update my flash plugin by doing this:

[B]$ apt-get install flashplugin-nonfree
$ sudo update-flashplugin[/B]

The update has been taking forever and appearing to get stuck in places. Are these the right commands? :confused:

---

### Post by Ub1476 on 2008-04-23
You can update everything on your system from Synaptic (package/install/update manager). System>Administration>Update.

The commands to update your system are:

```
sudo apt-get update
sudo apt-get upgrade
```

If you only want to upgrade certain packaes, I only know of the GUI way (look above).. 

I think that update-*package* is not a valid command though.

---

### Post by paxmark1 on 2008-04-23
Hey

paxmark@raunes:/etc$ man update
No manual entry for update

The first command should have worked

I use aptitude more than apt-get, both quite similar

man apt-get
man aptitude

I did the following on my system and got the following output.  

paxmark@raunes:~$ aptitude show flashplugin-nonfree
Package: flashplugin-nonfree
State: installed
Automatically installed: yes
Version: 9.0.124.0ubuntu2
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 168k
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1,
         libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0,
         libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6,
         libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts,
          ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>=
          1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (< 6), xfs (< 1:1.0.1-5)
Replaces: flashplugin (< 6)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a Netscape/Mozilla type
 plugin.  Any browser based on Netscape or Mozilla can use the Flash plugin.  This package
 currently supports the following browsers: Mozilla, Mozilla-Firefox, Firefox, Iceweasel,
 and Iceape.  Also Galeon and Epiphany can use the Flash plugin.  Konqueror can also use
 the Flash plugin if konqueror-nsplugins is installed.

 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be downloaded
 from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash plugin is available at
 [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies that you have accepted the terms
 of that license.

 Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)


Side question

Is your multiverse enabled in /etc/apt/sources.list

p.s.  Flash locked up both Opera and Firefox browsers for my older system a lot.  I am seeing a lot lot less of this with my dist-upgrade to hardy.

peace mark

---

### Post by Hellishcross on 2008-04-23
Cool... thanks for the help!

---

### Post by mgmiller on 2008-04-24
Actually, the command should have been:
```
sudo apt-get install flashplayer-nonfree
```

That being said, you would do better to install the meta package for all the restricted stuff.  This will give you flash, java and a host of other things as well.

You need to have all the repositories enabled, so make sure they are all checked in System > Administration > Software Sources and putting checks in every thing except Source Code (unless you need that).

Then you can either search for and install the restricted extras package in Synaptic or from a terminal, enter:
```
sudo apt-get install ubuntu-restricted-extras 
```

If you are running kubuntu, change the command to kubuntu-restricted-extras.

If you are running xubuntu, use xubuntu-restricted-extras.

This way, flash, java and everything else will stay up to date automatically.

---

