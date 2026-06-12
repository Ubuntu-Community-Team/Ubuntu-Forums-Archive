---
title: "Evolution removed from last update"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QQi on 2010-01-25
> The following packages will be REMOVED:
[COLOR="Red"]  evolution evolution-couchdb evolution-exchange evolution-indicator
  evolution-plugins libsdl1.2debian-alsa[/COLOR]
The following NEW packages will be installed:
[COLOR="DarkGreen"]  busybox-static libsdl1.2debian-pulseaudio netcat-openbsd ttf-wqy-microhei[/COLOR]
The following packages will be upgraded:
  [COLOR="DarkOrange"]devicekit-power flex libcryptui0 libdevkit-power-gobject1
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libpng12-0
  libpng12-dev libtelepathy-farsight0 python-launchpadlib rsync seahorse[/COLOR]
  synaptic ubuntu-desktop ubuntu-minimal ubuntu-standard
17 upgraded, 4 newly installed, 6 to remove and 0 not upgraded.

what's happen?:(

---

### Post by LKjell on 2010-01-25
Try to install evolution-common. A lot of packages have been merged.

libsdl1.2debian-alsa is going to be removed. I sort of have waited for that since Hardy.

---

### Post by phenest on 2010-01-25
Looks like a dependency problem (maybe) to do with the libgtkhtml* packages.

---

### Post by QQi on 2010-01-25
^

yes dependency problem with libgtkhtml

> $[COLOR="Green"]sudo apt-get install evolution[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[COLOR="Sienna"]The following packages have unmet dependencies:
  evolution: Depends: libgtkhtml-editor0 (< 1:3.29) but 1:3.29.6-0ubuntu1 is to be installed
             Depends: libgtkhtml3.14-19 (< 1:3.29) but 1:3.29.6-0ubuntu1 is to be installed
             Recommends: evolution-plugins but it is not going to be installed
E: Broken packages[/COLOR]

---

### Post by tad1073 on 2010-01-25
That is a good thing, I use Thunderbird exclusively can can do without all of evolutions junk.

---

### Post by zika on 2010-01-25
> **tad1073 said:**
> That is a good thing, I use Thunderbird exclusively can can do without all of evolutions junk.Evolution is not beeing removed. a new version is announced... This is a partial upgrade... I have texlive packages kept back for several days... ubuntu-desktop is, also, being kept back...

---

### Post by LKjell on 2010-01-25
libsdl1.2debian-pulseaudio is part of the ubuntu meta package. But to install that one it needs to remove the alsa one.

---

### Post by zika on 2010-01-25
> **LKjell said:**
> libsdl1.2debian-pulseaudio is part of the ubuntu meta package. But to install that one it needs to remove the alsa one.Done that already... (manually)

---

### Post by jppr on 2010-01-25
[https://launchpad.net/ubuntu/lucid/+source/evolution/2.28.2-1ubuntu5](https://launchpad.net/ubuntu/lucid/+source/evolution/2.28.2-1ubuntu5)

Rebuild to get the new gtkhtml shlib

---

### Post by emarkay on 2010-01-25
> **tad1073 said:**
> That is a good thing, I use Thunderbird exclusively can can do without all of evolutions junk.

I feel **exactly** the same here, but others do use it, and it's got some "hooks" into the user ID stuff as I recall.  I am sure it's just a transient Alpha thing - it'll be back soon...

---

### Post by philinux on 2010-01-25
OT but.

I switched to evolution in the last two months and prefer it.

Main reasons are. Forward and back buttons work as expected. The built in calender, synced with google, and clock applet integration. Ubuntu-one contacts sync.

---

