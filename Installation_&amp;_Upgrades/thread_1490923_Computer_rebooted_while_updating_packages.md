---
title: "Computer rebooted while updating packages"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by MikeinVA on 2010-05-22
I recently had to rebuild my computer with a new HDD and decided to load the new Ubuntu 10.04 which seems to work great. I was in the middle of downloading packages from the Ubuntu Software Center when the computer decided to reboot in the middle of downloading 6 packages. I went to the Synaptic Package Manager and it said to run "sudo dpkg --configure -a Here is what I got when I did that. What do I do next to fix and continue downloading the corrupted packages?

michael@michael-desktop:~$ sudo dpkg --configure -a
[sudo] password for michael: 
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up libelemental0 (1.2.0-3ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libelemental0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
dpkg: dependency problems prevent configuration of gelemental:
 gelemental depends on libelemental0 (>= 1.2.0); however:
  Package libelemental0 is not configured yet.
dpkg: error processing gelemental (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-support ...
Errors were encountered while processing:
 libelemental0
 gelemental
michael@michael-desktop:~$

---

### Post by mac9416 on 2010-05-23
Hi, MikeinVA,

To remove all downloaded packages run...

```
$ sudo apt-get clean
```

Then attempt to install the packages again. My guess is there will be errors, but we'll worry about that when it happens.

---

