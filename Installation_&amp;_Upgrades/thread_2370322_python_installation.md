---
title: "python installation"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by saiteja1995 on 2017-09-02
when I typed the command : **dpkg -s python**
OUTPUT:

Package: python
Status: install ok installed
Priority: standard
Section: python
Installed-Size: 635
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: allowed
Source: python-defaults
**Version: 2.7.11-1**
Replaces: python-dev (<< 2.6.5-2)
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Depends: python2.7 (>= 2.7.11-1~), libpython-stdlib (= 2.7.11-1)
Pre-Depends: python-minimal (= 2.7.11-1)
Suggests: python-doc (= 2.7.11-1), python-tk (>= 2.7.11-1~)
Breaks: update-manager-core (<< 0.200.5-2)
Conflicts: python-central (<< 0.5.5)
Description: interactive high-level object-oriented language (default version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v2.7).
Original-Maintainer: Matthias Klose <doko@debian.org>
Homepage: [http://www.python.org/](http://www.python.org/)


when I typed the command :[SIZE=4] **[SIZE=2]dpkg -s python-numpy[/SIZE]**[/SIZE]
OUTPUT:

**Python 2.7.13 (default, Sep  1 2017, 21:33:27)** 
[GCC 5.3.1 20160413] on linux2
Type "help", "copyright", "credits" or "license" for more information.
[B][I]>>> import numpy
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named numpy[/I][/B]
>>> 




So, I checked if **_python-numpy was installed_**




when I typed the command : **dpkg -s python-numpy**

OUTPUT:

Package: python-numpy
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 9373
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**Version: 1:1.11.0-1ubuntu1**
Provides: python-f2py, python-numpy-abi9, python-numpy-api10, python-numpy-dev, python2.7-numpy
Depends: python (<< 2.8), python (>= 2.7~), python2.7:any, python:any (>= 2.7.5-5~), libblas3 | libblas.so.3, libc6 (>= 2.14), liblapack3 | liblapack.so.3
Suggests: gcc (>= 4:4.6.1-5), gfortran, python-dev, python-nose (>= 1.0), python-numpy-dbg, python-numpy-doc
Description: Numerical Python adds a fast array facility to the Python language
 Numpy contains a powerful N-dimensional array object, sophisticated
 (broadcasting) functions, tools for integrating C/C++ and Fortran
 code, and useful linear algebra, Fourier transform, and random number
 capabilities.
 .
 Numpy replaces the python-numeric and python-numarray modules which are
 now deprecated and shouldn't be used except to support older
 software.
Homepage: [http://www.numpy.org/](http://www.numpy.org/)
Original-Maintainer: Debian Python Modules Team <python-modules-team@lists.alioth.debian.org>

[U][I][B]So I don't understand why 
1.there is inconsistency in version numbers  of python and
2.why numpy module could not be imported[/B][/I][/U]

---

### Post by ian-weisser on 2017-09-02
Please show us the result of the following commands:
```
which python
ls -l /usr/bin/python
ls -l /usr/bin/python2.7
```

---

