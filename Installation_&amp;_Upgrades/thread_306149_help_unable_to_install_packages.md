---
title: "help: unable to install packages"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by dabd on 2006-11-24
I always get the following error message after upgrading from dapper to edgy.
The error occurs after trying to install packages either with synaptic or aptitude (I'm running Kubuntu).

E: gnome-app-install: subprocess post-installation script returned error exit status 1

Is there any fix for this?

Thanks

---

### Post by dabd on 2006-11-24
This is more detailed transcript of the error.  Any help would be appreciated.


Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-app-install (0.2.21) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 12, in <module>
    import xdg.DesktopEntry
ImportError: No module named xdg.DesktopEntry
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-app-install

---

### Post by Dr. Dweebis on 2007-01-14
I am having the same error - has anyone written back to you?

Dweebis

---

### Post by Anicka on 2007-01-17
I had exactly the same problem, but it turned out I had python installed both in /usr/bin and in /usr/local/bin (check with "whereis python"). After I removed the local one plus the python library in /usr/local/lib, it worked without any problem.

Anicka

---

