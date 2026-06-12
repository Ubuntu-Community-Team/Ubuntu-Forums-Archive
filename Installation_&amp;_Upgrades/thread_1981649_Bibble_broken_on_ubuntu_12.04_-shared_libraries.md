---
title: "Bibble broken on ubuntu 12.04 -shared libraries?"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by kolibri on 2012-05-17
Ok, I know this is a Bibble problem, because they've abandoned Bibble and are making Bibble license owners pay $60 to get a Corel license because they haven't supported Bibble5 for Ubuntu 12.04, but  I thought I might get some help here.

After upgrading to Ubuntu 12.04, Bibble5  will no longer launch.  From the menus just nothing happens.

In the terminal, this is the error I get:

Install Path:           /opt/bibble5
LD_PATH:                /opt/bibble5/lib:
XLIB_SKIP_ARGB_VISUALS: 1
./bibble5: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory


I thought that I downloaded libGLU.so.1 and put in /opt/bibble5/lib but it didn't seem to make any difference.

TIA!

---

