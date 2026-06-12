---
title: "Newest updates want to install CVS and autotools"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aamukahvi on 2010-02-23
Any idea why this is happening? I tried to track various rdepends but couldn't figure it out. It was never installed before.
```
The following NEW packages will be installed:
  autoconf{a} automake1.9{a} autotools-dev{a} branding-ubuntu{a} cvs{a} gettext{a} intltool{a} irqbalance{a} libcap-ng0{a} 
  libkpathsea5{a} libubuntuone-1.0-1{a} m4{a} plymouth-x11{a} python-distutils-extra{a} python-ubuntuone{a} 
  rhythmbox-ubuntuone-music-store{a} 

```

---

### Post by VMC on 2010-02-23
Aptitude will show some explanation for you:

aptitude show cvs
Package: cvs
State: installed
...

Description: Concurrent Versions System
 CVS is a version control system, which allows you to keep old versions of files
 (usually source code), keep a log of who, when, and why changes occurred, etc.,
 like RCS or SCCS.  Unlike the simpler systems, CVS does not just operate on one
 file at a time or one directory at a time, but operates on hierarchical
 collections of directories consisting of version controlled files. 
 
 CVS helps to manage releases and to control the concurrent editing of source
 files among multiple authors.  CVS allows triggers to enable/log/control
 various operations and works well over a wide area network.

---

### Post by aamukahvi on 2010-02-23
> **VMC said:**
> Aptitude will show some explanation for you:

aptitude show cvs
Package: cvs
State: installed
...

Description: Concurrent Versions System
 CVS is a version control system, which allows you to keep old versions of files
 (usually source code), keep a log of who, when, and why changes occurred, etc.,
 like RCS or SCCS.  Unlike the simpler systems, CVS does not just operate on one
 file at a time or one directory at a time, but operates on hierarchical
 collections of directories consisting of version controlled files. 
 
 CVS helps to manage releases and to control the concurrent editing of source
 files among multiple authors.  CVS allows triggers to enable/log/control
 various operations and works well over a wide area network.

The thing is I know what it is but I don't want it and I cannot see any reason it should be installed.

---

### Post by philinux on 2010-02-23
> **aamukahvi said:**
> The thing is I know what it is but I don't want it and I cannot see any reason it should be installed.

Same here.

---

### Post by handaxe on 2010-02-23
Installed on my laptop as well, though synaptic indicates one can remove it without upsetting any depends. The OP probably has enabled the synaptic option to regard recommended packages as dependencies.

HA

---

### Post by aamukahvi on 2010-02-23
> **handaxe said:**
> Installed on my laptop as well, though synaptic indicates one can remove it without upsetting any depends. The OP probably has enabled the synaptic option to regard recommended packages as dependencies.

HA

Isn't that the default setting?

---

### Post by handaxe on 2010-02-23
> **aamukahvi said:**
> Isn't that the default setting?

Very possibly it is now - one tends to lose track of these things across multiple versions of Ubuntu :D  Whatever the case, it probably explains why CVS came in, given that it is not a dependency of any other package.

HA

---

### Post by aamukahvi on 2010-02-23
> **handaxe said:**
> Very possibly it is now - one tends to lose track of these things across multiple versions of Ubuntu :D  Whatever the case, it probably explains why CVS came in, given that it is not a dependency of any other package.

HA

Ok I found out that rhythmbox ubuntu one music store is causing this. I first deselected cvs and the rhytmbox plugin and then reselected the plugin. CVS was also selected. Hoping they get the dependencies sorted out. :)

---

