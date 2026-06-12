---
title: "Testing the git radeonhd driver on Jaunty"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yodermk on 2009-02-22
Is anyone running the code from
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)
?

I just tried it and am getting:
```

$ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
configure.ac:342: error: possibly undefined macro: XORG_MANPAGE_SECTIONS
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:344: error: possibly undefined macro: XORG_RELEASE_VERSION
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

First, anyone know what's wrong here?

But what I am wondering -- is there a way to install this without messing with the xorg packages from the repos? I'd really prefer not to mess with the package updates, keep this totally out of tree, and be able to switch to it and away from it at will.

I did install the xserver-xorg-video-radeonhd package, set the Driver to it in xorg.conf, and when X starts, the screen is totally white and blank, except for the mouse pointer. KDM does not show its login widgets.

My card is a HD 3200.

---

### Post by shm on 2009-02-22
you need installed xorg-dev package

but if you want to resolve 2D performance you need experimental branch [http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch](http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch)

but it seems that this branch for previous xorg version so it can't build in  jaunty.

catalist 9.2 also don't support xorg 1.6 

i'm also have radeon HD3200 and after update to  jaunty  i'm in trap.

sorry for English.

---

### Post by yodermk on 2009-02-22
xorg-dev is already installed.

I've never run Intrepid on this computer (it's a new build). I have another partition with OpenSUSE and it has much faster 2D speed, and it says direct rendering is enabled but no desktop effects.

If nothing else I can wait it out. I run Intrepid on my laptop, my important computer.

But if I can do so without making too much of a mess, I'll try the development branch of radeonhd.

---

### Post by rbmorse on 2009-02-22
In addition to xorg-dev there is one other package you need, but the name escapes me at the moment (xutils-dev?). 

See the notes in the "install" file in ~/xf86-video-radeonhd

---

### Post by yodermk on 2009-02-23
Sweet, it was xorg-build-macros -- thanks.

Now autogen finishes with:
```

NOTE: DRI support is disabled

```
Is this inherent to the code, or is something wrong here?

It did compile successfully. But before I install I also wonder what it will install and where, and can it easily be cleaned up should I want a pristine package-managed xorg again (for upgrades, etc)?

---

### Post by krazyd on 2009-02-23
You could try [checkinstall]("https://help.ubuntu.com/community/CheckInstall").

---

### Post by yodermk on 2009-02-23
Ok, used checkinstall -- thanks for the idea, but it did not seem to actually create a package.

I think I'm running the new code now, though, and performance seems to be a bit better. Says I have direct rendering but glxgears only gives like 60fps.

---

### Post by DeeZiD on 2009-02-23
> **yodermk said:**
> Says I have direct rendering but glxgears only gives like 60fps.
Nice!
Does that mean that SyncToVblank now works with the opensource driver? :D

---

### Post by Martje_001 on 2009-02-23
Next time if you want to compile something, try:
```
sudo apt-get build-dep <package>
```
It will install all dependencies automatically!

---

### Post by rbmorse on 2009-02-23
> **yodermk said:**
> Sweet, it was xorg-build-macros -- thanks.

Now autogen finishes with:
```

NOTE: DRI support is disabled

```Is this inherent to the code, or is something wrong here?

It did compile successfully. But before I install I also wonder what it will install and where, and can it easily be cleaned up should I want a pristine package-managed xorg again (for upgrades, etc)?

Where it installs:  You can specify this in the ./autogen a prefix statement. For example, 

./autogen.sh --prefix=/usr 

DRI is disabled: That's in the code. DRI support doesn't work for R6XX and R7XX cards, yet (there's an experimental branch active for R6 and R7 cards but it's useless at this time except for discovering problems and testing fixups. One at a time. Check the Wiki for details) so the default in the master branch is to disable DRI.

---

### Post by yodermk on 2009-02-24
Anyway, performance *is* still pretty bad. Not even really good 2D. *Possibly* a bit better than what I was running before, but not by a huge amount.

---

### Post by shm on 2009-02-26
today i build latest radeonhd drivers with latest drm and it works!

little how to:

mkdir /tmp/radeon
cd /tmp/radeon

wget [http://cgit.freedesktop.org/mesa/drm/snapshot/drm-r6xx-r7xx-support.tar.bz2](http://cgit.freedesktop.org/mesa/drm/snapshot/drm-r6xx-r7xx-support.tar.bz2)

tar jxvf ./drm-r6xx-r7xx-support.tar.bz2

cd ./drm-r6xx-r7xx-support

./autogen.sh --prefix=/usr

cd /tmp/radeon/drm-r6xx-r7xx-support/linux-core

make radeon.o drm.o

sudo cp ./radeon.ko  /lib/modules/`uname -r`/kernel/drivers/gpu/drm/radeon/

sudo cp ./drm.ko  /lib/modules/`uname -r`/kernel/drivers/gpu/drm/



next build radeonhd

cd /tmp/radeon

wget [http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/snapshot/xf86-video-radeonhd-r6xx-r7xx-support.tar.bz2](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/snapshot/xf86-video-radeonhd-r6xx-r7xx-support.tar.bz2)

tar jxvf ./xf86-video-radeonhd-r6xx-r7xx-support.tar.bz2

cd /tmp/radeon/xf86-video-radeonhd-r6xx-r7xx-support

./autogen.sh --prefix=/usr

make

sudo cp ./src/.libs/radeonhd_drv.so /usr/lib/xorg/modules/drivers

then edit device section in /etc/X11/xorg.conf 

Section "Device"
        Identifier      "Configured Video Device"
        Driver      "radeonhd"
        Option "AccelMethod" "EXA"
        Option "DRI" "on" #important!
EndSection

hope this helps
if you have build problems try
sudo apt-get build-dep xserver-xorg-video-radeonhd
sudo apt-get build-dep libgl1-mesa-dri

good luck!

---

### Post by krazyd on 2009-02-27
Cool! So you mean that 2D acceleration works? How is the Xv video playback?

3D doesn't work yet, does it?

---

### Post by theApokalypsis on 2009-03-12
nice! was going to create my own thread but found this one and thought I could add on. Made the jump to jaunty (with HD4870) and dropped fglrx (finally!), I was going off this link which follows the same process. 

[http://psung.blogspot.com/2009/02/configuring-radeon-r600r700-devices-on.html]("http://psung.blogspot.com/2009/02/configuring-radeon-r600r700-devices-on.html")

Instead of building the latest radeonhd you can also add Tormod Volden's PPA which has constantly updated git builds.


#Tormod Volden (OSS drivers)
deb [http://ppa.launchpad.net/tormodvolden/ppa/ubuntu](http://ppa.launchpad.net/tormodvolden/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tormodvolden/ppa/ubuntu](http://ppa.launchpad.net/tormodvolden/ppa/ubuntu) jaunty main

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXOSzAEEAJ+eXdGA6V9335cNpmS0ox+anlT98sz4X2wY2eFOOlP330o++KPdl3st/CJj
avGj6OtElIRV8v08YnPiU7GRVNshaIy2aedmgDsaMjKkjjDXeaBc/KHtVC9wzYPZYLj6MN6S
agDDmyekhesXuTxnIlmvFZ/Ly/AtTSaE8R6H7niDABEBAAG0H0xhdW5jaHBhZCBQUEEgZm9y
IFRvcm1vZCBWb2xkZW6ItgQTAQIAIAUCSXOSzAIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheA
AAoJEEseKHeW3VyaomoD/iC/e0FfclLSTtK2kkg659op8RDwjQsmlvRLQJMNhSfLz0wqZGiT
i/8rBsu8RNGBMSjE0ZT1GFyYT7Y3FRRmnmYiW+Q3/+1km/9k493XVq0T76LxnSXuwieIO26R
8qtQuApem6+xkxpzz767Te2boK/ErW1s+M0/4bK4lAQhQi/7
=dAGy
-----END PGP PUBLIC KEY BLOCK-----


I successfully have nice 2d playback with totem/gstreamer :D, no cpu spiking finally and nice and responsive gui.







Also, my current xorg.conf device section fyi...

Section "Device"
	Identifier	"Configured Video Device"
	Driver "radeonhd"
	Option "AccelMethod" "exa"
	Option "DRI" "on"
	Option "VideoOverlay" "off"
	Option "OpenGLOverlay" "on"
	Option "TexturedVideo" "off"
EndSection

Section "Module"
    Load  "dri"
EndSection

Section "DRI"
    Mode 0666
EndSection




p.s.s.

i found this feature chart interesting for current development and radeonhd vs radeon.

[http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature")

---

