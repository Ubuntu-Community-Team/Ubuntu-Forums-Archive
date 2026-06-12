---
title: "Self installed dependencies"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by idlewild on 2005-05-27
I wanted a newer version of mono on my system so I just used their installer which worked very well but now I'm unable to install tomboy & f-spot which depend on mono.
Is there any way to tell my apt-get registry (not sure what it's called) that I've got mono installed so I can continue to use apt-get?

make an empty .deb with my version number on?

---

### Post by az on 2005-05-27
No.  You would need a backport for that.

---

### Post by idlewild on 2005-05-27
...which leads to another question, how easy/time consuming is it for a non-developer to make a backport for everyone.

---

### Post by az on 2005-05-27
It can be pretty easy.  It depends on the package.


[http://ubuntuforums.org/showthread.php?t=12040](http://ubuntuforums.org/showthread.php?t=12040)
[http://backports.ubuntuforums.org/faq.php](http://backports.ubuntuforums.org/faq.php)


There seems to be a mono backport already...

---

