---
title: "Installing OpenOffice.org 3.0 RPMS"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by andsmi on 2008-10-20
Hi! I'm wondering on how to install openoffice.org 3.0 on my ubuntu hardy. I have no Idea... I just downloaded it from openoffice.org and received an .tar.gz. I unfolded it and ended up with an install and one uninstall file, and a folder called RPMS, how do I install this?

Thnx

---

### Post by eldragon on 2008-10-20
you downloaded the wrong package..

get it from [here]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0") instead

to install:


unpack.

remove openoffice.org-core from synaptic

install all .debs in DEBS.

and for incons and such, install the .deb in DEBS/desktop-integration.

---

### Post by andsmi on 2008-10-20
> **eldragon said:**
> you downloaded the wrong package..

get it from [here]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0") instead

to install:


unpack.

remove openoffice.org-core from synaptic

install all .debs in DEBS.

and for incons and such, install the .deb in DEBS/desktop-integration.

But thats not the nb version. the file I downloaded was Norwegian-Bokmål

---

### Post by eldragon on 2008-10-20
> **andsmi said:**
> But thats not the nb version. the file I downloaded was Norwegian-Bokmål

oh, well, here you can [get]("http://download.openoffice.org/other.html") all versions, but there isnt a deb pack for your language.

you could try alien to convert the rpms to debs, but i dont know if it will work.

alien is in the repos

---

### Post by andsmi on 2008-10-20
So there isn't a way to install the rpms?

---

### Post by andsmi on 2008-10-20
I tried to install all of those DEBS but I get these following errors while installing some: Error: Dependency is not satisfiable: ooobasis3.0-en-US

---

### Post by eldragon on 2008-10-20
> **andsmi said:**
> So there isn't a way to install the rpms?

yes, with alien, which is a package interpreter for rpms (turns them into debs), it doesnt work 100% of the time. there must but a reason why the debs are not available in your language.


about the unsatisfiable dependence, beats me, i just hit the following to get oo3.0 installed:
```

$ sudo apt-get remove openoffice.org-core
$ sudo dpkg -i *.deb
$ cd desktop-integration
$ sudo dpkg -i *.deb

```

the dpkg commands should be executed in the directory with the debs.

all dependencies are in the same folder. if there was an unresolved dependency, it will get fixed once the missing package is installed.

---

### Post by andsmi on 2008-10-20
Thanks! got it working now. But in the terminal it said: javaldx: Could not find a Java Runtime Environment!

---

### Post by eldragon on 2008-10-20
> **andsmi said:**
> Thanks! got it working now. But in the terminal it said: javaldx: Could not find a Java Runtime Environment!

well, you need just that :D

```

$ sudo apt-get install sun-java6-jre

```

i *think* thats all you will need :D

---

### Post by andsmi on 2008-10-20
thnx;)

---

