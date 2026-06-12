---
title: "python2.5 support removed for twisted and other packages?"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by warnerpr on 2010-03-08
Hi, am I correct in noticing that Lucid removed python2.5 support for twisted-python and many other third party packages?

In 9.10 apt-get install python-twisted would install twisted for python2.5 and python2.6, but this does not seem to be the case for 10.04.

Can someone fill me in the on the plan for python2.5 support in Lucid?  

Thanks.

BTW this is on Alpha 3 with the latest updates.

-Paul

---

### Post by KaOS-bEat on 2010-03-15
yep, seems that packages that need 2.5 are now going to be uninstallable due to unsatisfied dependencies.
I'm having trouble getting python support for paraview, [other]("https://bugs.launchpad.net/ubuntu/+source/pylucene/+bug/538654") packages are affected as well but it seems the solution is pushing the developers to 2.6. 

wouldn't be bad to have a fallback 2.5 at least for a transition period...


K

---

