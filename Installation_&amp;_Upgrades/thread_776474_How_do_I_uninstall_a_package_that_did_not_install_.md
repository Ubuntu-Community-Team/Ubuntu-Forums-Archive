---
title: "How do I uninstall a package that did not install right"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by piromedic on 2008-04-30
I was installing a number of programs and lost my internet for some reason.  Some of the packages did not completely install.  Now I am tring to install some codecs and I get the message: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
  I have run the dpkg --configure -a and it tries to run the program Setting up acidlab (0.9.6b20-22) ... that did not install properly.  I dselect and aptitude.  I have even tried purge and noting seams to stop that acidlab.


Any help please,
Don

---

### Post by Pumalite on 2008-04-30
Post the complete output.

---

### Post by piromedic on 2008-04-30
Please explain what the complete output is and how do I do it?

> **Pumalite said:**
> Post the complete output.

---

### Post by Pumalite on 2008-04-30
sudo dpkg --configure -a
Copy and paste the entire result here.

---

### Post by piromedic on 2008-04-30
This is what happeneds
Setting up acidlab (0.9.6b20-22) ...

That is all that happeneds.  I have waited for 45 minutes and no change.

---

