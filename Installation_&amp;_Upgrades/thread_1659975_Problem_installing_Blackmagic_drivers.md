---
title: "Problem installing Blackmagic drivers"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Harrycrossxx on 2011-01-04
trying to install the drivers for my blackmagic intensity pro capture device and i cannot get the driver to install i get an error in the ubuntu software center saying: 


There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 851, in _simulate_helper
    size = int(deb["Installed-Size"]) * 1024
ValueError: invalid literal for int() with base 10: ''


i have the latest ubuntu fully up-to-date.

---

### Post by Rexbron! on 2011-01-12
First, make sure you are using [7.9.4 ]("http://www.blackmagic-design.com/downloads/software/DeckLink_Linux_7.9.4.tar.gz") as the problem with the driver package is fixed there. 

However, an issue with Media Express still exists and I posted instructions on how to fix it on my [blog]("http://www.aehunter.net/ubuntu/blackmagic-design-media-express-2-3-and-ubuntu-10-10-a-solution/").

---

