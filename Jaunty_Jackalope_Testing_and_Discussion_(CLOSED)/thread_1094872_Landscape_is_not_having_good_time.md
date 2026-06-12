---
title: "Landscape is not having good time"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-03-13
Sounds like Python issues.  I am using Landscape from repos.

$ landscape-config 
Traceback (most recent call last):
  File "/usr/bin/landscape-config", line 6, in <module>
    from landscape.configuration import main
  File "/usr/lib/python2.6/dist-packages/landscape/configuration.py", line 15, in <module>
    from landscape.lib.dbus_util import (
  File "/usr/lib/python2.6/dist-packages/landscape/lib/dbus_util.py", line 15, in <module>
    from twisted.internet.defer import Deferred, execute
ImportError: No module named twisted.internet.defer


$ landscape-client 
Traceback (most recent call last):
  File "/usr/bin/landscape-client", line 7, in <module>
    from twisted.internet.glib2reactor import install
ImportError: No module named twisted.internet.glib2reactor

---

### Post by michael37 on 2009-03-14
Sounds like a intrepid-jaunty upgrade problem which resolved itself with latest upgrades.

---

