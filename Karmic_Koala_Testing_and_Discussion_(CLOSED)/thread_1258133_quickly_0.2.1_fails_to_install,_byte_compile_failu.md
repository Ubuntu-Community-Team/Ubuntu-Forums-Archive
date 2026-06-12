---
title: "quickly 0.2.1 fails to install, byte compile failure"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-09-04
Setting up quickly (0.2.1) ...
Compiling /usr/lib/python2.6/dist-packages/quickly/quicklyconfig.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/quickly/quicklyconfig.py', 24, 19, '__version__ = 0.2.1\n'))
 pycentral: pycentral pkginstall: error byte-compiling files (11)
pycentral pkginstall: error byte-compiling files (11)
dpkg: error processing quickly (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 quickly


see [https://bugs.launchpad.net/quickly/+bug/424581](https://bugs.launchpad.net/quickly/+bug/424581) for quick fix

---

