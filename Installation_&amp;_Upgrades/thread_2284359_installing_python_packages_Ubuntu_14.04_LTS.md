---
title: "installing python packages Ubuntu 14.04 LTS"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by helio3 on 2015-06-29
I'm having troubles installing python (2.7.6) modules in my Ubuntu 14.04  LTS. I have just tried to install module numpy (and others)and when I import it, I  have the following output:

```

~$ python
Python 2.7.6 (default, Jun 22 2015, 17:58:13) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/numpy/__init__.py", line 153, in <module>
    from . import add_newdocs
  File "/usr/lib/python2.7/dist-packages/numpy/add_newdocs.py", line 13, in <module>
    from numpy.lib import add_newdoc
  File "/usr/lib/python2.7/dist-packages/numpy/lib/__init__.py", line 18, in <module>
    from .polynomial import *
  File "/usr/lib/python2.7/dist-packages/numpy/lib/polynomial.py", line 19, in <module>
    from numpy.linalg import eigvals, lstsq, inv
  File "/usr/lib/python2.7/dist-packages/numpy/linalg/__init__.py", line 50, in <module>
    from .linalg import *
  File "/usr/lib/python2.7/dist-packages/numpy/linalg/linalg.py", line 29, in <module>
    from numpy.linalg import lapack_lite, _umath_linalg
ImportError: /usr/local/bin/gex/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by /usr/lib/liblapack.so.3)

```

I already tried to update, upgrade, install with pip and so many other  things and just became without extra options to try around here...  

Could anyone give any light on what the problem might be?


  Thanks in advance!


  Cheers

---

### Post by dino99 on 2015-06-29
Trusty already has the latest numpy package  [https://launchpad.net/ubuntu/+source/python-numpy](https://launchpad.net/ubuntu/+source/python-numpy)
as well the python2.7.6  [https://launchpad.net/ubuntu/+source/python2.7](https://launchpad.net/ubuntu/+source/python2.7)

and i suppose you already have python2.7 installed by default on your Trusty system. So what are you doing and how ?

---

### Post by helio3 on 2015-06-29
Using the original version, I tried to "import numpy" and I was getting the error I mentioned in the 1st post. That´s the reason I tried to update/upgrade. After doing this, I´m still getting the same error. Is there any diagnostic sugestion? I have no idea why this is happening...:-|

---

### Post by steeldriver on 2015-06-29
There is something screwy in your library search path - it is finding a non-standard libgfortran.so.3 in /usr/local

```

ImportError: **/usr/local/bin/gex/libgfortran.so.3**: version `GFORTRAN_1.4' not found (required by /usr/lib/liblapack.so.3)

```

---

### Post by helio3 on 2015-06-29
Thanks for the input steeldriver.

I managed to reinstall gfortran manually by downloading the package (deb file). Everything is working fine...so far......

Cheers

---

