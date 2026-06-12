---
title: "Accessing Enthought: Python"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by winzer on 2010-02-27
I just installed the Enthought package that has loads of modules available for scientific computing with python. When I access python in my terminal and try to import a module it can't locate it. I tried setting an env variable to where my enthought package was located but that didn't fix it.

---

### Post by winzer on 2010-03-01
Do I need to set an environmental variable for python?

---

### Post by winzer on 2010-03-01
The instruction state:
This EPD-6.0.1 installer provides a Python build for Unix systems.
It includes Python 2.6.4.


Install Notes
-------------

  * A full installation installs everything (except menu items) under the
    target install directory.  All that is necessary to use EPD then is to
    place the directory

        <install>/bin

    in your path, or to explicitly call the binaries within that directory.
    Note that the installer will not modify your environment or .profile files
    for you.

So I went into my .bashrc and add:
PATH=$PATH:/home/chris/edp-6.0.1-rh5-x86/bin

I run python in the terminal, try to import a module and no success.

---

### Post by hiKen on 2011-06-03
same problem here!!

bump

---

### Post by calbaker on 2011-07-11
Bump

---

