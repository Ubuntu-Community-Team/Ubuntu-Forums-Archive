---
title: "Broken package, any one else?"
date: 2009-04-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-04-30
I know it is way early, but for 2 days now this has been showing up as broken package:```
 apt-xapian-index: Depends: python-apt (>= 0.7.10.3) but 0.7.9~exp2ubuntu10 is installed.

```
Is any one else seeing this?

---

### Post by taavikko on 2009-04-30
Affected also, but like you said, it is very early in the process so
dependencies just haven't catched up.

---

### Post by ajackson on 2009-04-30
The dependencies are probably still in the build queue or haven't been sent to building yet. It's fairly common at this stage for stuff to get held back as they resync with Debian unstable (I think thats the right Debian version)

---

### Post by DougieFresh4U on 2009-04-30
> **taavikko said:**
> Affected also, but like you said, it is very early in the process so
dependencies just haven't catched up.

> **ajackson said:**
> The dependencies are probably still in the build queue or haven't been sent to building yet. It's fairly common at this stage for stuff to get held back as they resync with Debian unstable (I think thats the right Debian version)

Thanks, was just 'curious'

---

### Post by Jammy4041 on 2009-04-30
> **DougieFresh4U said:**
> I know it is way early, but for 2 days now this has been showing up as broken package:```
 apt-xapian-index: Depends: python-apt (>= 0.7.10.3) but 0.7.9~exp2ubuntu10 is installed.

```Is any one else seeing this?

I don't like to state the obvious but...

>=0.7.10.3 python-apt, = You must have a version of python-apt equal to or better than 0.7.10.13.
Unfortunatly, you only have 0.7.9

This means that your package that you want to install the 0.7.10.3 version from the debian sid repos, but these may depend on higher version, making you download more packages. (dependency hell is the technical term)

The debian package search website, using sid, has the python-apt version that you want.

[http://packages.debian.org/unstable/python/python-apt](http://packages.debian.org/unstable/python/python-apt)

Hope this helps.

---

### Post by autocrosser on 2009-04-30
I just deleted it until I see Python-apt hit the "right" version....:)

---

### Post by Amaranth on 2009-04-30
Do **not** get packages from Debian directly. Even most of the people who can handle the Ubuntu development releases probably won't be able to dig out of that hole.

---

### Post by DougieFresh4U on 2009-05-01
> **Amaranth said:**
> Do **not** get packages from Debian directly. Even most of the people who can handle the Ubuntu development releases probably won't be able to dig out of that hole.

I hear ya!!

---

### Post by plun on 2009-05-01
My broken packages for the moment....

```
The following packages have been kept back:
  apt-xapian-index libcompizconfig0 libcompizconfig0-dev python-feedparser

```

None of them gives any trouble for me.

---

### Post by rudenko_ruslan on 2009-05-01
> ruslan@ruslan-desktop:~$ sudo aptitude full-upgrade
[sudo] password for ruslan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  apt-xapian-index libcompizconfig0 libgnome2.24-cil 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 407kB of archives. After unpacking 115kB will be used.
The following packages have unmet dependencies:
  libcompizconfig0: Depends: compiz-core-abiversion-20090207 which is a virtual package.
  libgnome2.24-cil: Depends: libart2.0-cil (>= 2.24.0) which is a virtual package.
                    Depends: libgconf2.0-cil (>= 2.24.0) which is a virtual package.
                    Depends: libgnome-vfs2.0-cil (>= 2.24.0) which is a virtual package.
  apt-xapian-index: Depends: python-apt (>= 0.7.10.3) but 0.7.9~exp2ubuntu10 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
f-spot
libgnome2.24-cil
libgnomepanel2.24-cil
tomboy

Keep the following packages at their current version:
apt-xapian-index [0.16 (now)]
libcompizconfig0 [0.8.2-0ubuntu1 (now)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends f-spot
ubuntu-desktop recommends tomboy
Score is 66

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
ruslan@ruslan-desktop:~$
That's mine situation at the moment.

---

### Post by plun on 2009-05-01
> **rudenko_ruslan said:**
> That's mine situation at the moment.

"Right or wrong ??"...  I removed those packages..but this is a gamble :)
Something is changed in the mono-stack.

You can also wait....

edit

and sudo apt-get install ubuntu-desktop at last.

---

