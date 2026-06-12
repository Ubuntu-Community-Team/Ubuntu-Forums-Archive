---
title: "Compile code (PyGTK) for a compiled version of Python"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by wcyang on 2011-04-07
How can I compile PyGTK for a compiled version of Python?

In the past, I may have compiled the following version of Python:[INDENT] /usr/local/bin/python2.6
[/INDENT]I tried compiling PyGTK using "configure, make, sudo make install.'

When I ran the above version of Python and typed "import pygtk", the following message appeared:[INDENT] ImportError: No module named pygtk
[/INDENT]When I typed "python2.6 setup.py build", the following message appeared:[INDENT] ********************************************************************
* Building PyGTK using distutils is only supported on windows. *
* To build PyGTK in a supported way, read the INSTALL file.    *
********************************************************************
[/INDENT]The INSTALL file talks about "./configure; make; make install."

Do I need to change some options for "configure?"

---

### Post by EpicSceptic on 2011-05-31
I have a similar issue.  When I try installing pygtk on my virtualenv with

pip install pygtk

It downloads and when it is installing I get the same error message stating:

Building PyGTK using distutils is NOT SUPPORTED

I thought there might be something wrong with pip but you used a different installation method(I assume) and yet get the same problem?

I updated setuptools and pip and build-essentials etc.  Nothing seems to work.

Any help/advice on this?

---

