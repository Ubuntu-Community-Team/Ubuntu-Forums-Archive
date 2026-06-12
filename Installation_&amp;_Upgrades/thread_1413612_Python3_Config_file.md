---
title: "Python3 Config file?"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by vaguy02 on 2010-02-22
Everyone,

I've installed python3 on Ubuntu 9.10, but the application I'm trying to install requires the python3-config file. This is not loaded in the /usr/bin/ dir with the python3 command. Is there a way to generate or load this file?

Thanks,
Rob

---

### Post by oldfred on 2010-02-22
The config file should be part of the application. python uses configparser to process it.
 python3 ./cfgexample.py 
There was a bug.
[http://mail.python.org/pipermail/new-bugs-announce/2009-September/005854.html](http://mail.python.org/pipermail/new-bugs-announce/2009-September/005854.html)

---

### Post by vaguy02 on 2010-02-22
Actually what I needed was python3-dev, this installed the program "python3-config" in /usr/bin/

Thanks,
Rob

---

