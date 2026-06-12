---
title: "feisty update crashes HELP!!!"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by akilarules on 2007-05-30
when i try to update ubuntu it the update manager finds all the new updates and when i try to install them an error message pops up saying the following:

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

The same thing happened to synaptic and the add-remove application. when i went into terminal and ran 'dpkg --configure -a' it said i needed superuser privileges, even tho i am the computer administrator. what do i do?

---

### Post by moonliter on 2007-05-30
to get root privilegies you have to type sudo before dpkg --configure -a 
copy and paste this into terminal:

**sudo dpkg --configure -a** hope it help?

---

### Post by akilarules on 2007-05-30
thanks a lot. is that all i have to do tho?

---

### Post by phidia on 2007-05-30
Well you might want to hold off on the recently released updates until this [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)
is sorted out.

---

