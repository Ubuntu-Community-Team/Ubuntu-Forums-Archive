---
title: "Install Azureus"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by wlankatt on 2005-11-17
I need some help, again. -.-
I'm trying to install Azureus. I tried this: [http://www.ubuntuguide.org/#azureus]("http://www.ubuntuguide.org/#azureus") but it didn't work. What else can I do?

---

### Post by bored2k on 2005-11-17
[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus+java+install](http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus+java+install)

---

### Post by taurus on 2005-11-17
What didn't work?  Can you at least be a little more specific???

---

### Post by mmcmonster on 2005-11-19
[QUOTE=taurus]What didn't work?  Can you at least be a little more specific???[/QUOTE]

Well, I'm not the original poster, but azureus doesn't appear to be in universe or multiverse.  Here is my sources.list
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

#backports
#deb http://us.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
#deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse restricted

#backports-extras
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse restricted

# Penguin Liberation Front 
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

#wine
deb http://wine.sourceforge.net/apt/ binary/
#deb-src http://wine.sourceforge.net/apt/ source/

#w32codecs and dvd software
#####*****Only uncomment this line to install w32codecs*****#####
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

#opera web browser
deb http://deb.opera.com/opera/ etch non-free

#OpenOffice.org2.0 final
deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

