---
title: "Compiling python 2.5/2.6 with zlib"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by Svennhg on 2011-05-16
Hi,

I'm trying to compile Python 2.5.5 (and 2.6) with zlib support on Natty. I have installed zlib1g-dev and several other dev packages. I'm able to compile python but zlib is not included:

ImportError: No module named zlib

Anyone else that have this problem, or have a solution for it?

Best wishes

Svenn.

---

### Post by rogerbinns on 2011-05-18
> **Svennhg said:**
> 
I'm trying to compile Python 2.5.5 (and 2.6) with zlib support on Natty. 

ImportError: No module named zlib


It is Ubuntu's "fault".  They changed where shared libraries are placed in order to support multiple architectures better (eg both x86 and x86_amd64 on the same machine) in a way that diverges from how it has always been done in the past.

As part of Python's build process it has many optional modules such as zlib.  To determine if a module can be built it looks for a header file and for the library in the normal locations.  Because of the changed layout it can't find the library and hence doesn't build the module.

Upstream Python is being patched, but that doesn't really help as they are only doing it with current versions of Python.  (I have to build every Python version from 2.3 through 3.3 so a few patched versions doesn't do me any good.)

This disgusting hack works for me on an AMD64 machine:

```
  cd /lib
  sudo ln -s x86_64-linux-gnu/libz.so.1 libz.so
```

---

### Post by Svennhg on 2011-05-18
Thanks, this worked for me as well.

---

### Post by tiggsy on 2012-04-20
Unfortunately, it didn't work for me (I have python2.5 in opt, as Ubuntu runs on 2.6)

---

### Post by hunterm4573r on 2012-04-30
The *disgusting hack* worked for me.  But this other way from Christian Heimes at LiPyrary also worked for me as well as allowing many other *necessary bits* to be installed as well... 

[http://lipyrary.blogspot.mx/2011/05/how-to-compile-python-on-ubuntu-1104.html](http://lipyrary.blogspot.mx/2011/05/how-to-compile-python-on-ubuntu-1104.html)

```
$ make distclean
$ export LDFLAGS="-L/usr/lib/$(dpkg-architecture -qDEB_HOST_MULTIARCH)"
$ ./configure
$ make
$ make install
$ unset LDFLAGS
```

---

