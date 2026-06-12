---
title: "Repo poisoning? Lots of new packages installed during recent update"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by bartong on 2010-02-19
Hi everyone,

During my most recent run of Update Manager I noticed something a little odd - it installed a whole bunch of new packages I had not previously had installed.

Below is part of the output of my History from Synaptic:

```
Installed the following packages:
alien (8.78)
bsd-mailx (8.1.2-0.20081101cvs-2ubuntu1)
debhelper (7.3.15ubuntu3)
html2text (1.3.2a-14)
intltool-debian (0.35.0+20060710.1)
libmail-sendmail-perl (0.79.16-1)
libqt3-mt (3:3.3.8-b-5ubuntu3)
libqt4-gui (4.5.3really4.5.2-0ubuntu1)
librpm0 (4.7.0-9)
librpmbuild0 (4.7.0-9)
librpmio0 (4.7.0-9)
libsys-hostname-long-perl (1.4-2)
lsb (4.0-0ubuntu5)
lsb-core (4.0-0ubuntu5)
lsb-cxx (4.0-0ubuntu5)
lsb-desktop (4.0-0ubuntu5)
lsb-graphics (4.0-0ubuntu5)
m4 (1.4.13-2)
mailx (1:20081101-2ubuntu1)
ncurses-term (5.7+20090803-2ubuntu2)
pax (1:20090728-1)
po-debconf (1.0.16)
postfix (2.6.5-3)
rpm (4.7.0-9)
```

What worries me in particular is the installation of alien, bsd-mailx and postfix.  Why should I suddenly need these packages? I haven't installed any new applications for months!

I know it sounds paranoid, but could it be possible the repo has somehow been poisoned, and the attacker is trying to turn our machines into spam spewers??

Keen to gauge any thoughts on the matter!

---

### Post by J V on 2010-02-19
probably just debian repo updated and ours automatically updated...

Alien is for installing rpms, as is rpm... so basicly, the rest are probly dependancies...

Chances of repo poisoning are slim-to-none: read up on public/private keys...

---

### Post by kansasnoob on 2010-02-19
I read something about that in lucid testing this AM:

[http://ubuntuforums.org/showthread.php?t=1410411](http://ubuntuforums.org/showthread.php?t=1410411)

It appears to have come from the Chrome repo, but I don't use it so can't be sure ;)

---

### Post by kostkon on 2010-02-19
The recent Chrome update pulled them for some reason. Nothing to worry about.

---

### Post by bartong on 2010-02-22
Interesting... I didn't stop to think that it might be Chrome pulling them down.

I am a little intrigued as to why Chrome would need Postfix et al though?  Are they trying to set it up so it can be recognised as an email client (for sending mail by redirecting into Gmail website) or something like that maybe?

PS: I know that repo poisoning is technically very difficult, but it has happened before to another linux distro, IIRC.  I think it was actually an insider that did it in that case.

---

