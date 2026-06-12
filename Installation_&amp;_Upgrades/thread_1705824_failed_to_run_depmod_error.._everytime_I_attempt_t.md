---
title: "failed to run depmod: error.. everytime I attempt to install, update, or run synaptic"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by chadmkidner on 2011-03-12
Every time I run the package manager whether it be for updates, install, or anything else, I get an error during that states that is is attempting to recover from a package failure. At the end it states *Failed to run depmod dpkg: error processing linux-image-2.6.32-25-generic: subprocess installed post-installation script returned error exit status 1* And the same again for linux-image-2.6.35-27-generic..  I'm bewildered as to why it wouldn't just reconfigure when it goes through the update each time? It seems to try pretty hard my computer freezes everytime while it's attempting to because it maxes out the CPU.. Could having older kernels installed cause this problem by chance? Ideas? Thanks in advance for anyone that can help.

---

### Post by chadmkidner on 2011-03-22
Still haven't figured this out..

---

### Post by sikander3786 on 2011-03-22
Welcome to the forums and apologies for the late reply :-)

We need to see the complete output of these commands from Applications > Accessories > Terminal:

```
sudo apt-get update
sudo dpkg --configure -a
```

---

### Post by chadmkidner on 2011-04-03
Hmm.. Well I fixed the problem but its very interesting that it ever was one.. I deleted all of the old Kernels and reran synaptic updates and ran smoothly. no problems.

---

