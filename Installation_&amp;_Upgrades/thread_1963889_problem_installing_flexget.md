---
title: "problem installing flexget"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by pirush on 2012-04-23
hi!
my xbmcbuntu version is: 
Distributor ID: Ubuntu
Description: Ubuntu 11.10 - XBMCbuntu
Release: 11.10
Codename: oneiric

i am having trouble installing flexget.
must admit i am a linux nubie.
i ahve tried following these guides:
[http://flexget.com/wiki/InstallWizard/Linux/Environment](http://flexget.com/wiki/InstallWizard/Linux/Environment)
and 
[http://www.havetheknowhow.com/Install-th...exGet.html](http://www.havetheknowhow.com/Install-th...exGet.html)

and it looks like i have a python problem becuse whenever i type python -v i get the bellow messages, instead of the python version. (same for flexget b.t.w)

amir@amir-desktop:/etc/apt$ python -v
# installing zipimport hook
import zipimport # builtin
# installed zipimport hook
# /usr/lib/python2.7/site.pyc matches /usr/lib/python2.7/site.py
import site # precompiled from /usr/lib/python2.7/site.pyc
# /usr/lib/python2.7/os.pyc matches /usr/lib/python2.7/os.py
import os # precompiled from /usr/lib/python2.7/os.pyc
import errno # builtin
import posix # builtin
# /usr/lib/python2.7/posixpath.pyc matches /usr/lib/python2.7/posixpath.py
import posixpath # precompiled from /usr/lib/python2.7/posixpath.pyc
# /usr/lib/python2.7/stat.pyc matches /usr/lib/python2.7/stat.py
import stat # precompiled from /usr/lib/python2.7/stat.pyc
# /usr/lib/python2.7/genericpath.pyc matches /usr/lib/python2.7/genericpath.py
import genericpath # precompiled from /usr/lib/python2.7/genericpath.pyc
# /usr/lib/python2.7/warnings.pyc matches /usr/lib/python2.7/warnings.py
import warnings # precompiled from /usr/lib/python2.7/warnings.pyc
# /usr/lib/python2.7/linecache.pyc matches /usr/lib/python2.7/linecache.py
import linecache # precompiled from /usr/lib/python2.7/linecache.pyc
# /usr/lib/python2.7/types.pyc matches /usr/lib/python2.7/types.py
import types # precompiled from /usr/lib/python2.7/types.pyc
# /usr/lib/python2.7/UserDict.pyc matches /usr/lib/python2.7/UserDict.py
import UserDict # precompiled from /usr/lib/python2.7/UserDict.pyc
# /usr/lib/python2.7/_abcoll.pyc matches /usr/lib/python2.7/_abcoll.py
import _abcoll # precompiled from /usr/lib/python2.7/_abcoll.pyc
# /usr/lib/python2.7/abc.pyc matches /usr/lib/python2.7/abc.py
import abc # precompiled from /usr/lib/python2.7/abc.pyc
# /usr/lib/python2.7/_weakrefset.pyc matches /usr/lib/python2.7/_weakrefset.py
import _weakrefset # precompiled from /usr/lib/python2.7/_weakrefset.pyc
import _weakref # builtin
# /usr/lib/python2.7/copy_reg.pyc matches /usr/lib/python2.7/copy_reg.py
import copy_reg # precompiled from /usr/lib/python2.7/copy_reg.pyc
# /usr/lib/python2.7/traceback.pyc matches /usr/lib/python2.7/traceback.py
import traceback # precompiled from /usr/lib/python2.7/traceback.pyc
# /usr/lib/python2.7/sysconfig.pyc matches /usr/lib/python2.7/sysconfig.py
import sysconfig # precompiled from /usr/lib/python2.7/sysconfig.pyc
# /usr/lib/python2.7/re.pyc matches /usr/lib/python2.7/re.py
import re # precompiled from /usr/lib/python2.7/re.pyc
# /usr/lib/python2.7/sre_compile.pyc matches /usr/lib/python2.7/sre_compile.py
import sre_compile # precompiled from /usr/lib/python2.7/sre_compile.pyc
import _sre # builtin
# /usr/lib/python2.7/sre_parse.pyc matches /usr/lib/python2.7/sre_parse.py
import sre_parse # precompiled from /usr/lib/python2.7/sre_parse.pyc
# /usr/lib/python2.7/sre_constants.pyc matches /usr/lib/python2.7/sre_constants.py
import sre_constants # precompiled from /usr/lib/python2.7/sre_constants.pyc
# /usr/lib/python2.7/sitecustomize.pyc matches /usr/lib/python2.7/sitecustomize.py
import sitecustomize # precompiled from /usr/lib/python2.7/sitecustomize.pyc
import encodings # directory /usr/lib/python2.7/encodings
# /usr/lib/python2.7/encodings/__init__.pyc matches /usr/lib/python2.7/encodings/__init__.py
import encodings # precompiled from /usr/lib/python2.7/encodings/__init__.pyc
# /usr/lib/python2.7/codecs.pyc matches /usr/lib/python2.7/codecs.py
import codecs # precompiled from /usr/lib/python2.7/codecs.pyc
import _codecs # builtin
# /usr/lib/python2.7/encodings/aliases.pyc matches /usr/lib/python2.7/encodings/aliases.py
import encodings.aliases # precompiled from /usr/lib/python2.7/encodings/aliases.pyc
# /usr/lib/python2.7/encodings/utf_8.pyc matches /usr/lib/python2.7/encodings/utf_8.py
import encodings.utf_8 # precompiled from /usr/lib/python2.7/encodings/utf_8.pyc
Python 2.7.2+ (default, Oct 4 2011, 20:03:08) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
dlopen("/usr/lib/python2.7/lib-dynload/readline.so", 2);
import readline # dynamically loaded from /usr/lib/python2.7/lib-dynload/readline.so
>>> 


any idea?

thank!

---

