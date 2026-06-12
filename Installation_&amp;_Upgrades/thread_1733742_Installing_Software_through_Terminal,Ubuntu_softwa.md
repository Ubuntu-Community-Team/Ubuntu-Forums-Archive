---
title: "Installing Software through Terminal,Ubuntu software center or Synaptic Pkg mgr Error"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by TULIOESTRADA on 2011-04-19
Ubuntu 10.10

This is what I get when I run terminal:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
richard@richard-B2-Series:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I run Ubuntu software center:

An unhandlable error occured:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

When I run Synaptic Pkg Mgr:

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

Already restarted pc and still the same thing. I have nothing else runnning.

Thank you in advance for your help.

---

### Post by plucky on 2011-04-19
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Something is keeping hold of the lock file which only allows one package manager to run at a time.

Close all package managers (Synaptic,Update-manager,apt-get,aptitude,etc) and from a terminal try ```
sudo rm /var/lib/dpkg/lock
``` then run ```
sudo apt-get update && sudo apt-get upgrade
``` and post back the output if you are still getting any errors.

Good Luck

---

