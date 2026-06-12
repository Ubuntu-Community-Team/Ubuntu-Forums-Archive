---
title: "Trouble with an install"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Corporal_Clegg on 2008-03-06
I was installing a program using GDebi package installer, I thought it was taking to long so I
pressed cancel, then the initial window wouldn't close (I'd press the X button and nothing would happen) so I restarted my computer. Now when I try to install the program again it says I need to close the original, and whenever I open up Synaptic it gives a message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report." I try to run that and it just gives me a bunch of help options. I'm not sure what to do to get it working again, any help?

---

### Post by forestpixie on 2008-03-06
you need to run it as root

sudo dpkg --configure -a'

---

### Post by Corporal_Clegg on 2008-03-06
Thanks worked fine

---

