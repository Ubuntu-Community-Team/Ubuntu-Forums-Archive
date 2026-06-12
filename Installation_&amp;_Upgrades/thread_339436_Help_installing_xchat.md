---
title: "Help installing xchat"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by compfreak219 on 2007-01-15
When I try to install xchat on Ubuntu 6.10 I get this:

```

sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) but it is not installable
E: Broken packages

```

It's a deb package so I also just tried using the package manager and it says:
```

Error: Dependency is not satisfiable: libdbus-1-2

```

:(

---

### Post by NeoLithium on 2007-01-15
Post what shows from this command in terminal:
```

cat /etc/apt/sources.list

```

I think you might just not have the repository enabled that will allow apt-get to install the dependencies for Xchat...

---

### Post by compfreak219 on 2007-01-15
it shows:
```


deb http://www.davidpashley.com/debian/irssi-sarge/ ./
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

```

I have edited it some with other programs, so I hope I didn't screw it up

---

### Post by NeoLithium on 2007-01-15
Ok, type this:
```

gksudo gedit /etc/apt/sources.list

```

Then copy and paste this list, into yours, & save.
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

```

Then just type:
```

sudo aptitude update

then 

sudo aptitude install xchat

```

And all should be well :)

---

### Post by compfreak219 on 2007-01-15
thanks, I'll try it and see what happens. 

No reply is a good reply.

---

### Post by compfreak219 on 2007-01-15
there was progress....but this shows up now when I try installing it

```
The following packages are BROKEN:
  xchat 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  xchat-common 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libdbus-1-3 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common 
  libkrb53 libmagick9 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic mono-common mono-gac mono-jit 
  mono-runtime openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer python-uno screen tar ttf-opensymbol tzdata vino 
  w3m x11-common xbase-clients xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  xchat-common 
0 packages upgraded, 2 newly installed, 0 to remove and 95 not upgraded.
Need to get 965kB of archives. After unpacking 2773kB will be used.
The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
xchat [Not Installed]

Leave the following dependencies unresolved:
xchat-common recommends xchat
Score is -201

Accept this solution? [Y/n/q/?]

```

I hit y and it said all those packages have been kept back and 0 packages upgraded 0 installed

---

### Post by NeoLithium on 2007-01-15
ok, try this quick:
```

sudo apt-get update
 
then 

sudo apt-get dist-upgrade

```

Basically, you need that update of hte packages held back.  The dist-upgrade should install them; then you can install xchat.

---

### Post by compfreak219 on 2007-01-15
its upgrading.. it looks like it will take some time though

---

### Post by NeoLithium on 2007-01-15
WIth some of the repositories you had commented out still in the sources.list; it missed a fair bit from before; but don't worry; this larger size update only happens once, the rest of the time they'll trickle in with smaller amounts to be downloaded and installed.

---

### Post by compfreak219 on 2007-01-15
ok xchat STILL wont install..here's what I get:

```

 sudo aptitude install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  xchat 
The following NEW packages will be automatically installed:
  xchat-common 
The following NEW packages will be installed:
  xchat-common 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 965kB of archives. After unpacking 2773kB will be used.
The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
xchat [Not Installed]

Leave the following dependencies unresolved:
xchat-common recommends xchat
Score is -201

Accept this solution? [Y/n/q/?] 

```

---

### Post by NeoLithium on 2007-01-15
Hmmm, it says it's broken, maybe open up synaptic and try to repair the installed Xchat first?

---

### Post by compfreak219 on 2007-01-15
it wont do anything ... should i just try irssi? lol

---

### Post by compfreak219 on 2007-01-15
wow... I got irssi installed now, so nevermind about xchat. Thanks for everything.

---

