---
title: "Biopython installation"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by dovah on 2014-07-22
Hi guys! 

I'm trying to install the biopython module on my Ubuntu 12.04 LTS machine (64x). I first upgraded to Python3.3 by installing from source (biopython does not support other versions), that seems ok. 

However, I installed some modules using the ```
sudo apt-get install python-module
``` command but I can't call them from a python shell:

```
dovah@AsusX501A:~$ python3.3
Python 3.3.5 (default, Mar 12 2014, 02:09:17) 
[GCC 4.6.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from biopython import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'biopython'
>>> from Bio import * ##as suggested in http://biopython.org/DIST/docs/api/module-tree.html
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'Bio'
```

As you can see, the modules are installed: 

```
dovah@AsusX501A:~$ sudo apt-get install python-biopython
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-biopython is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And so is biopython (quite strange though: line 14 says biopython-1.64-py**2.7**-linux-x86_64.egg):

```
dovah@AsusX501A:~$ sudo easy_install -f http://biopython.org/DIST/ biopython
Searching for biopython
Reading http://biopython.org/DIST/
Best match: biopython 1.64
Downloading http://biopython.org/DIST/biopython-1.64.zip
Processing biopython-1.64.zip
Writing /tmp/easy_install-v5LJZz/biopython-1.64/setup.cfg
Running biopython-1.64/setup.py -q bdist_egg --dist-dir /tmp/easy_install-v5LJZz/biopython-1.64/egg-dist-tmp-TruGJH
warning: no previously-included files matching '.cvsignore' found under directory '*'
warning: no previously-included files matching '*.pyc' found under directory '*'
zip_safe flag not set; analyzing archive contents...
Bio.Entrez.Parser: module references __path__
Adding biopython 1.64 to easy-install.pth file
Installed /usr/local/lib/python2.7/dist-packages/biopython-1.64-py2.7-linux-x86_64.egg
Processing dependencies for biopython
Finished processing dependencies for biopython
```

Are modules specific for a given python version? Why is the system still stuck on Python 2.7? 

Thank you in advance for your help.

EDIT: Numpy successfully installed by using: ```
sudo apt-get install numpy3
```

---

### Post by slooksterpsv on 2014-07-22
Biopython installed on your system with python 2.7 as the default. You can update your alternatives to set python3 to the default or just install it yourself (easiest solution less breakage).

Some programs have been ported to python3 but not all of them for Ubuntu. Hence the still, and most widely used, python 2.7 version.

---

### Post by slooksterpsv on 2014-07-22
Sorry for duplicate post, my network glitched.

---

