---
title: "python versions, numpy, scipy, pandas..."
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by oldnik on 2012-10-24
How to install python2.7.3 + numpy + scipy + matplotlib + scikits.statsmodels + pandas0.7.3 correctly ? The problem: 

```
~$ python --version
Python 2.7.3
```so i already have a system-default 2.7.3, which is good!

```
~$ dpkg -s python-numpy
Package: python-numpy
Status: install ok installed

```and i already have numpy installed! great! But...

```
~$ python
Python 2.7.3 (default, Oct 23 2012, 01:07:38) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy as nmp
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named numpy

```this module couldn't be find by python. The same with scipy, matplotlib. Why?

```
~$ sudo apt-get install python-numpy
[...] 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-numpy is already the newest version.
[...]

```why it does not see numpy and others ?

---

### Post by dino99 on 2012-10-24
python-numpy (1:1.7.0~b2-1ubuntu1) raring; urgency=low

  * Merge with Debian; remaining changes:
    - debian/patches/20_disable-plot-extension.patch
       Disable plot_directive extension, and catch ImportErrors when
       matplotlib cannot be imported, which allows us to remove
       python-matplotlib from dependencies.  This is required because
       python-numpy is in main, while python-matplotlib is in universe.
    - Build using dh_python2
      add bin/f2py* to .install files

 -- Matthias Klose <doko@ubuntu.com>  Mon, 22 Oct 2012 15:26:41 +0200

---

