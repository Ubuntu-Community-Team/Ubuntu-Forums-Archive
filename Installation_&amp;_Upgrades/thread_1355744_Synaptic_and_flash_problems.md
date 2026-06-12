---
title: "Synaptic and flash problems"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Mr Williams on 2009-12-15
I was trying to install wine for xubuntu and I have somehow messed up not only flash, but synaptic.


I am caught in a loop, in which one thing is telling me to do one thing and the other is saying something different.


I cannot install any programs because synaptic is being clogged with 'broken' files, it says "**Could not upgrade the system!  Fix broken packages first."  **I have tried using the broken filter but it will not do anything, after waiting for ages it tells me  **"E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal."**   Therefore completing the loop and driving me mad.

Please help

---

### Post by Mr Williams on 2009-12-15
This is what happens when I try to install flash manually on terminal

```
  anthony@anthony2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
anthony@anthony2:~$ 
  
```

This is what happens when I try to remove them

```
anthony@anthony2:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
E: Unmet dependencies. Try using -f.
```

loop much?????????

---

