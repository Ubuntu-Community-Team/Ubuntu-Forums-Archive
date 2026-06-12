---
title: "Error when I try to install drivers/programs"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by blackbinary on 2008-02-18
I get this error, even if I just try to open the synaptic packet manager. I've already got problems with the install which I hope will be fixed by driver downloads, but I can't get to them because of this error. Also during my last session it was downloading software updates when the screen went black and I had to hard reboot, this may be the cause.

Anyways. the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks for any help


--PS: 

So i ran dpkg --configure -a
I'm assuming the python-bittorent file wasn't complete when I hard reboot'd and is now corrupt because I get this error:

E: The package python-bittorrent needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So what do I do next? Now the package manager won't open at all.

---

### Post by luisromangz on 2008-02-18
Do what the error says. Open a terminal and write:

sudo dpkg --configure -a

---

