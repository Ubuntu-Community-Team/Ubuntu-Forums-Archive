---
title: "Which PPA's do you use?"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-06-24
As the title says, which PPA's are you using.
Currently I've got:
[Empathy Daily]("https://launchpad.net/%7Eamoog/+archive/empathy-daily")
[Banshee Daily]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-daily")
[Gwibber Daily]("https://launchpad.net/%7Egwibber-daily/+archive/ppa")
[Webkit]("https://launchpad.net/%7Ewebkit-team/+archive/ppa")

---

### Post by graaant on 2009-06-24
Can you include links to the keys for these?

---

### Post by descendent87 on 2009-06-24
> **graaant said:**
> Can you include links to the keys for these?
added links to the launchpad pages

---

### Post by jmmL on 2009-06-24
These are my extras:> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main #Mozilla-daily
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main #Gnome Do
# deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main #nVidia and mplayer - thefirstm
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #Chromium
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main #Banshee
deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main #Kow - VLC pre1.0
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) jaunty main #Gnome-colors
deb [http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu) jaunty main #Banshee-unstable

mozilla-daily for firefox-3.5, firefox-3.6 and thunderbird-3.0 (aka shredder)
do-core is for gnome-do.
thefirstm packages the latest nVidia drivers and also mplayer with vdpau support.
chromium-daily is for chromium-browser
kow packages VLC as and when new milestones are released
Gnome-colors for the cool theme and icon sets
And the two banshee PPAs for banshee testing.

---

### Post by Rainstride on 2009-06-24
I use these.

[X Updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/")
[Pidgin]("https://launchpad.net/~pidgin-developers/+archive/ppa")
[OpenOffice.org]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")
[GNOME-Colors (shiki/arc colors)]("https://launchpad.net/~gnome-colors-packagers/+archive/ppa")
[Wine]("http://www.winehq.org/download/deb")
[Virtualbox]("http://www.virtualbox.org/wiki/Linux_Downloads")
[Banshee (stable)-I don't even use banshee but i have the ppa:D]("https://edge.launchpad.net/~banshee-team/+archive/ppa")
[Banshee (unstable)]("https://launchpad.net/~banshee-unstable-team/+archive/ppa")
[bojo42's ppa, i don't ever add this one to my update lists. I only use one program out of the whole thing (Mupen64plus 1.5) so I just download that one deb file.]("https://launchpad.net/~bojo42/+archive/ppa")
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

**Transmission**
```
deb http://ppa.launchpad.net/transmissionbt/ubuntu <ubuntu_release_name> main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu <ubuntu_release_name> main
```change for your distro.

```
gpg --keyserver keyserver.ubuntu.com --recv 976b5901365c5ca1
gpg --export --armor 976b5901365c5ca1 | sudo apt-key add -
```

---

