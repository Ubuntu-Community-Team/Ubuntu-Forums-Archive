---
title: "upgrade problem/crashed opera"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by nodyl on 2007-04-20
I am unable to upgrade to "feisty".   I'm using the command:

gksu "upgrade-manager -c"

When I do this I get following error:

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

In addition to this, since I have tried to upgrade, my opera seg faults every time I try to use it since I tried to update.

What did I do?

---

### Post by zvacet on 2007-04-20
You didn´ comment cdcrom line in your source list.Put # in front of that line.Did you finish upgrade?Maybe that is reason why Opera crashes.Comment all repositories wich are not suported by Ubuntu(medibuntu and repos like that).

---

### Post by nodyl on 2007-04-20
What is the name of my source list file?  If you could, please include the full path; i have never been there before.

Also, do you know why that wasn't in the instructions?

---

### Post by nodyl on 2007-04-20
Please...I don't know what a source list is...

---

### Post by emerson999 on 2007-04-20
For opera, it's a problem on their side of things. Upgrading to the latest version of opera should solve the segfault.

---

### Post by emerson999 on 2007-04-20
> **nodyl said:**
> Please...I don't know what a source list is...

/etc/apt/sources.list

Though you'll have to be root, so something like

sudo vim /etc/apt/sources.list or sudo gedit /etc/apt/sources.list

---

### Post by nodyl on 2007-04-21
Zvacet and Emerson999 thanks for helping with the install.   The computer says it's upgraded now although I see no differences as of yet.


As far as upgrading Opera, I tried a few weeks ago and I just get the following error:

Conflicts with the installed package 'opera-static'


Do you know what that's about?

---

### Post by jdong on 2007-04-21
Remove the opera-static package using Synaptic or apt-get, then download the newest version of Opera from opera.com (The Edgy Eft packages do work under Feisty, at the time I did it no feisty debs were available)

---

### Post by nodyl on 2007-04-21
Thank you!

---

### Post by dermanus on 2007-04-27
Different problem with Opera:
```
opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed


```

I had it, it wouldn't open, so I decided to uninstall and try again. Now I get this.

I'm not too experienced. I'm guessing it's a version conflict, but I don't know how to change it.

---

### Post by jdong on 2007-04-27
Make sure that you download the right package to match your distribution version.

---

### Post by dermanus on 2007-04-27
I'm using Synaptic and it's the only package I can see.

---

### Post by zvacet on 2007-04-27
Remove all Opera files you have(delete with synaptic) and go here

[http://www.opera.com/download/]("http://www.opera.com/download/")

Double click on package and you will have new Opera.

---

### Post by dermanus on 2007-04-28
We're in business. Thanks!

---

