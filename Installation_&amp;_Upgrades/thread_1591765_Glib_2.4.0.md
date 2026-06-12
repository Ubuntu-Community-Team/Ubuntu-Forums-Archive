---
title: "Glib 2.4.0"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by dbhatt on 2010-10-09
I am trying to build Pidgin on my Lucid install and on running configure, I get the following: 

> configure: error: 

You must have GLib 2.4.0 or newer development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
I tried installing pkg-config, but it's already in its newest version. I then tried going to the following website

[http://www.linuxcompatible.org/news/story/glib_240_released.html](http://www.linuxcompatible.org/news/story/glib_240_released.html)

and downloaded and extracted glib on my computer. That changed nothing.  I was hoping someone could tell me what's going on here.


I just tried the this: 

> sudo apt-get install libgtk2.0-0

and got 

> libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by lloyd_b on 2010-10-10
You're probably just missing the development headers.  Try installing package "libgtk2.0-dev" and see if it makes that error go away.

(many libraries are separated into two packages - the main library package, which is needed to run programs that use the library, and the corresponding "-dev" development package, which contains the extra stuff required to compile programs that use the library).

Lloyd B.

---

### Post by dbhatt on 2010-10-11
That did not work, again because of unmet dependencies. Here's what I got

> The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Broken packages


Following this, I tried building dependencies for libgtk2.0 and I got this


> picking 'gtk+2.0' as source package instead of 'libgtk2.0-dev'
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is to be installed
E: Build-dependencies for libgtk2.0-dev could not be satisfied.


---

### Post by lloyd_b on 2010-10-11
> **dbhatt said:**
> That did not work, again because of unmet dependencies. Here's what I got



Following this, I tried building dependencies for libgtk2.0 and I got this

Hmmm - some sort of inconsistency between the packages.  Have you updated/upgraded that machine recently?  Try running "sudo apt-get update && sudo apt-get upgrade" on it to ensure that it's fully upgraded.  Hopefully, this may clear the inconsistencies.

(the issue here is that libgtk2.0-dev is looking for an *older* version of libgtk (2.20.0-0ubuntu4, rather than 2.20.1-0ubuntu1)

Lloyd B.

---

### Post by dbhatt on 2010-10-11
Yes, I found that surprising too. I am running a Lucid build, and I update pretty regularly but I'll give the update commands a shot anyway.

---

### Post by dbhatt on 2010-10-12
Still no go. I get the same unmet dependencies. I'm doing all this to build and run Pidgin from the source code that I just downloaded. Is there a proper set of instructions on how to do that? This is my first foray into open source development, which is why I'm so lost.

---

### Post by Matt Harrison on 2010-10-12
Try this to fix the some of the dependencies above:

```
sudo apt-get install libglib2.0-dev libpango1.0-dev libatk1.0-dev
```

This will install GLib so you won't need to compile that, just try configuring pidgin again.

Any reason you are trying to compile Pidgin rather than installing the package?

---

### Post by dbhatt on 2010-10-12
Nope, same error.

---

### Post by dbhatt on 2010-10-12
I went in and enabled the "Recommended Updates" from Synaptic. Following this, I was able to install the lib2.4.0-dev packages that I was looking for.

Craig Harding suggested this solution.

---

