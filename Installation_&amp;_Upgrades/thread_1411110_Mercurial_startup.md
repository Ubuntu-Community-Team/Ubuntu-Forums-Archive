---
title: "Mercurial startup"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by humebug on 2010-02-19
I am trying to use mercurial.

I get through the installation fine, and the debuginstall reports no errors.

When I attempt to clone a repo (the tutorial on the mercurial website) I get the error message:

abort: could not import module _ssl!
Exception AttributeError: "'httprepository' object has no attribute 'urlopener'" in <bound method httprepository.__del__ of <mercurial.httprepo.httprepository object at 0xb756b78c>> ignored

I have had a look at my python and there is an _ssl file in the Module folder.

Can anyone suggest what's wrong?
Thanks.

---

