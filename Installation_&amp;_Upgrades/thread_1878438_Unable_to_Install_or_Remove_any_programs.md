---
title: "Unable to Install or Remove any programs"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by Tallguitarguy on 2011-11-09
It's been working fine for a while, but all of a sudden I can't install or remove anything in ubuntu software center. Here's all that the error messages say:
Message 1
"An unhandlable error occured - There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
Details - Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."
Message 2
"A program problem was detected..."
Message 3
"Sorry, the program aptdaemon closed unexpectedly..."

The parts with '...' are nothing useful for you. Please help, because I would hate to have to install ubuntu from scratch again.

---

### Post by darkod on 2011-11-09
Not sure if it helps with this kind of error, but you might try:

sudo dpkg --configure -a

or

sudo dpkg --reconfigure -a

(not sure of the exact spelling right now).

That helps with broken down installations of some package, if that's what is blocking further installs.

---

### Post by Tallguitarguy on 2011-11-10
That didn't do anything unfortunately. I can still remove and get programs using terminal, but that's no fun.

---

### Post by Tallguitarguy on 2011-11-10
I just had this stupid idea, "I wonder what would happen if I uninstalled Ubuntu Software Center, and then reinstalled it." What do you know? It worked. lol

---

