---
title: "Pidgin 2.5.2 and OTR 3.2.0 not working on hardy"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by aquateen.carl on 2008-10-22
I've been trying since yesterday to get the new pidgin to work with the new OTR (off the record) plugin. I downloaded and installed the new pidgin from getdb. No problems everything works fine. However, if I install the new OTR 3.2.0 plugin deb that I downloaded from the interpid repo, pidgin starts up in the bottom panel and then closes. If run pidgin from the terminal I get the following:

```
pidgin: symbol lookup error: /usr/lib/pidgin/pidgin-otr.so: undefined symbol: g_dgettext

```

Once I remove the OTR plugin, pidgin works fine again. Just a little side note, I also installed the latest libotr, libotr-dev, and libotrbin (3.2.0-1 I believe) from the interpid repos. I then tried to download and complie the plugin from source, no luck here either. This what I get when I run ./configure

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXTRA... configure: error: Package requirements (glib-2.0 >= 2.6 gtk+-2.0 >= 2.6 pidgin >= 2.0 purple >= 2.0) were not met:

No package 'pidgin' found
No package 'purple' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXTRA_CFLAGS
and EXTRA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'm guessing I just need to point it in the right direction; however, I need to be pointed in the right direction in order to do that. :)

any help would be greatly appreciated.

---

### Post by aquateen.carl on 2008-10-23
Any ideas.... Is this maybe a bug with the plugin or did I miss something during the install?

---

### Post by silverdulcet on 2008-10-31
I found a PPA (Personal Package Archive) that has pidgin-otr 3.2.0 and all related libotr packages for hardy.

[https://launchpad.net/~misery/+archive]("https://launchpad.net/~misery/+archive")

Just add these sources:
deb [http://ppa.launchpad.net/misery/ubuntu](http://ppa.launchpad.net/misery/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/misery/ubuntu](http://ppa.launchpad.net/misery/ubuntu) hardy main

```
sudo aptitude update
sudo aptitude install pidgin-otr
```

I've tested the packages with the newest pidgin and it works perfectly for me.

---

### Post by aquateen.carl on 2008-11-06
Silver thanks for the info, I will have to give this a shot. My only concern is, do you know if this source is trustworthy? I hate to install it, if it may actually be counterintuitive to my goal of trying to secure ubuntu. 

Thanks again

---

### Post by G20-Budo on 2008-12-09
Has anyone tested this?  I tried it, but during the pidin-otr install, I got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "pigin-otr"
Couldn't find any package whose name or description matched "pigin-otr"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Inputs?

---

### Post by silverdulcet on 2008-12-09
> **G20-Budo said:**
> Has anyone tested this?  I tried it, but during the pidin-otr install, I got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "[COLOR="Red"]pigin-otr[/COLOR]"
Couldn't find any package whose name or description matched "[COLOR="Red"]pigin-otr[/COLOR]"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Most likely the typo highlighted above. If that doesn't work. You could always download the package and its dependencies and install it manually either by double-clicking on the .deb files and letting GDebi install them or using the command line with:

```
sudo dpkg -i packagename.deb
```

Just go to [https://launchpad.net/~misery/+archive]("https://launchpad.net/~misery/+archive")

I believe the packages you need are the following:
libotr2
libotr2-bin
libotr2-dev
pidgin-otr

You'll find the links to the debs when you expand the arrow link next to each of those package names. The 3 libotr2*.deb packages are listed under the one libotr heading.  Then just select the correct .deb file for your Ubuntu install/architecture (i.e. i386 for 32-bit or amd64 for 64 bit). I belive you need to install the libotr packages before you install the pidgin-otr plugin. Gdebi or dpkg will let you know if you need to install one before the other.

---

