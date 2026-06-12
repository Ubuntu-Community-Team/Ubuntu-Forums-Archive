---
title: "Hardy and Desktop effects"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by driebel on 2008-05-19
I upgraded to Hardy this afternoon, and for the most part, the upgrade went smoothly.  My desktop effects manager doesn't work anymore, however.  Trying to open it from the main menu brings up an error window telling me the program has crashed and asking me to report the problem.  I tried re-installing the compiz package from Synaptic, to no avail.  My window open/close animations are still working, but my desktop cube is gone.
I'm gaining command line experience, but still rather new.  Basic instructions preferred :)

Any ideas?

---

### Post by ajgreeny on 2008-05-19
Firstly try renaming the ~/.gconf/apps/compiz folder to compiz.backup then reboot or at least log out and in again.  If that doesn't work when you try to get the cube working in compizconfig-settings-manager try completely removing compiz and then reinstalling it after a reboot.

---

### Post by driebel on 2008-05-19
Some more info, though I'm not sure if it's relevant.  I attempted to run the config manager from the command line, and the following resulted:

dave@Ishmael:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList
dave@Ishmael:~$ 

Along with the same error window as before.  I mentioned I was gaining command line experience, but this exceeds my knowledge base.  Does this mean there's a problem with the python libraries?  I'll look at Synaptic for similar packages, but I'm kind of just flopping and twitching at this point.

---

### Post by driebel on 2008-05-19
Thanks ajgreeny.  I've renamed the folder and am about to restart.  One note though, the problem isn't that I can't get the cube working through the configuration settings manager, it's that I can't start the configuration settings manager in the first place.

---

### Post by driebel on 2008-05-19
Tried the re-name, reboot, re-install method with no luck.  After the rename, compiz is completely deactivated (of course), and even after using synaptic to re-install compiz and its various add-ons, I am still unable to start the configuration settings manager.

---

