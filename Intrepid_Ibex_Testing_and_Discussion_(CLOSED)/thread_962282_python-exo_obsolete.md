---
title: "python-exo obsolete?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-29
Hi all, 
 This is a ubuntu and xubuntu (meaning both environments) enabled box. This was running on Hardy and then updated/upgraded to Intrepid. I have been able to resolve almost all the updates and upgrades but python-exo is one which I haven't been able to resolve. This is what system-cruft-remover sees. Perhaps its a bug or something, I have no idea 

```

$ sudo cruft-remover --verbose find
[sudo] password for shirish: 
ignored    deb:python-exo 
           Package is no longer supported: it is no longer in the package archive. (It may also have been installed from an
           unofficial archive that is no longer available. In that case you may want to keep it.)

```

Tried to know what python-exo is 

```

~$ aptitude show python-exo
Package: python-exo
New: yes
State: installed
Automatically installed: no
Version: 0.3.4-3ubuntu4
Priority: optional
Section: python
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 348k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.8), libexo-0.3-0 (>= 0.3.4), libglib2.0-0 (>= 2.15.6),
         libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.19.4), libxfce4util4 (>= 4.4.2), python (>= 2.4), python (< 2.6),
         python-central (>= 0.5.62)
Suggests: python-exo-dbg
Provides: python2.4-exo, python2.5-exo
Description: Library with extensions for Xfce (Python bindings)
 libexo is a library for Xfce that contains a bunch of additional widgets and a framework for editable toolbars (an improved
 version of the framework present in GNOME), light-weight session management support, functions to automatically synchronize
 object properties (based on GObject Binding Properties) and several miscellaneous utility and helper functions for
 application developers. 
 
 This package provides Python bindings for libexo.
Homepage: http://libexo.os-cillation.com/

```

Can somebody help me?

---

