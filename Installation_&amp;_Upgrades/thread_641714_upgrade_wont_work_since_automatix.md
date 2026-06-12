---
title: "upgrade wont work since automatix"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by gorilly on 2007-12-15
hi all 

i installed automatix2

since then i cant upgrade even though i have the upgrade icon appearing

when i click on upgrade i get the error 'not all upgrades can be installed' so i select partial upgrade.

then i get the error 'could not calculate the upgrade'

help please!

7.10 btw

---

### Post by taurus on 2007-12-15
Oughtta remove automatix2 from your system and from your /etc/apt/sources.list!

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by ericartman on 2007-12-15
Tried AM once, things got better when I did a fresh install without AM.

Cart

---

### Post by gorilly on 2007-12-16
Hi

thanks for the help guys,

seemed to be the ftp.debian.us (or similar) and the AM one casuing havock in my sources

all sorted out now, cheers

---

### Post by SunnyRabbiera on 2007-12-16
yeh sometimes automatix does this... but it has never done this to me though

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

