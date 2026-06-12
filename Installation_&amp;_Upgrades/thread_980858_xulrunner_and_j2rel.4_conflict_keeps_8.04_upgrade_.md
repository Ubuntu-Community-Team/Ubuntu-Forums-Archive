---
title: "xulrunner and j2rel.4 conflict keeps 8.04 upgrade from completing"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by deangl on 2008-11-13
Hello,

I have been running 7.10 for a while and things were humming along...

I upgraded to 8.04 using update manager.  During upgrade, I started seeing errors related package conflicts with xulrunner-1.9 and j2rel.4.  This resulted in multiple packages not being installed/updated correctly.  Now things are really bad on the system.

When trying to "remove" j2rel.4, there is no such package.  But dpkg command output in the terminal window keeps complaining that there are package conflicts.

This is frustrating as it seems I am stuck in an unusual state:
... can't remove the package because it isn't there...
... and can't install further packages because of the package conflict with j2rel.4.

Any help would be greatly appreciated.

Thanks,
Dale

---

### Post by deangl on 2008-11-13
Found out one of my problems.  I was misspelling the package name.  It was really "j2re" with a 1.4 appended to it (not "j2rel" .4 - el vs one).

I dpkg -r j2re1.4 and am now updating the rest.

Dale

---

