---
title: "Python3.2 does not find Numpy1.5.1"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by mapuwenyi on 2011-08-04
I am using Ubuntu version 11.4.
I used the synaptic package manager to download Python3.2 and the Python module  Numpy1.5.1. However, **when I try to "import numpy" I get the message "No module named numpy"**.

I set "export PYTHONPATH=/usr/share/pyshared/numpy" and "export PYTHONPATH=/usr/share/pyshared/numpy/", but nothing new happened.

Now the numpy module is obviously  there, since it is found by other versions of Python like Python2.7, which is used by the system. I tested both Python2.7 *including numpy* or Python3.2 *without numpy*, both worked ok.
Does anybody know how to manage this problem?

---

### Post by Eltern on 2011-08-08
I have been having the same issue. The problem arises because, outside of anything Ubuntu does, different Python versions do not share the same modules. What would be desired behavior in Ubuntu is when you use the repositories to install a Python model (ex. Scipy) you designate which version(s) of Python you want it installed into. As of now I don't know of any such functionality, and bug reports on the subject haven't received a lot of love:
[https://bugs.launchpad.net/ubuntu/+source/python-numpy/+bug/795605](https://bugs.launchpad.net/ubuntu/+source/python-numpy/+bug/795605)

[This thread]("http://stackoverflow.com/questions/6084416/tkinter-module-not-found") proposes that you can use update-python-modules to update modules from one version of Python to another. This has not worked for me ("updated" modules stay in 2.x land, and don't convert to 3.x). I have heard tell of "easy" ways to manage dual versions of modules with easy_install or distribute, but they're not as dead simple as the Ubuntu repositories. I have not yet attempted to implement them.

You can download the source and build with python3 ([like so]("http://www.scipy.org/Installing_SciPy/Linux"), just use python3 instead of python). This definitely works, but is a pain.

---

### Post by mapuwenyi on 2011-08-09
:) PROBLEM SOLVED :); a painless manual installation in a few steps can be done as follows:

[LIST=1]
[*]**Install the 5 auxiliary packages (gcc, gfortran, python3.2, python3.2-dev, libatlas-base-dev)** either by using the synaptic package manager of Ubuntu11.4 or the following teriminal command:
[LIST]
[*] sudo apt-get install gcc gfortran python3.2 python3.2-dev libatlas-base-dev
[/LIST]
 
[*]**Download Numpy1.6.1 and unpack it**; using the following commands:
[LIST]
[*]wget [http://sourceforge.net/projects/numpy/files/NumPy/1.6.1/numpy-1.6.1.tar.gz](http://sourceforge.net/projects/numpy/files/NumPy/1.6.1/numpy-1.6.1.tar.gz)
[*]tar -zxvf numpy-1.6.1.tar.gz
[/LIST]
 
[*]**If the environment variable PYTHONPATH happens to be set, unset it** (you may set it again after installing Numpy):
[LIST]
[*]unset PYTHONPATH
[/LIST]
 
[*]The command that unpacks NumPy1.6.1 will have created a directory called "numpy1.6.1". **Enter that directory and build the Numpy package** with the help of the fortran compiler:
[LIST]
[*]cd numpy-1.6.1/
[*]python3.2 setup.py build --fcompiler=gnu95
[/LIST]
 
[*]**Install the numpy package** (your previous python2.7 installation will not be harmed):
[LIST]
[*]sudo python3.2 setup.py install
[/LIST]
 
[/LIST]
You now should be able to invoke Python3 as "python3.2" and use "import numpy as n" without error messages; it worked ok for me. (Credits for the above recipe go to Gerrit Kuhl in Hong Kong)

---

### Post by gniss on 2012-04-08
:p Nice...this solution worked!!!

---

