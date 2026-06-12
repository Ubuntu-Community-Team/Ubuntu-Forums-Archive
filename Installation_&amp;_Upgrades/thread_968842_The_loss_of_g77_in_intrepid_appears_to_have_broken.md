---
title: "The loss of g77 in intrepid appears to have broken f2py in numpy."
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by ryeterrell on 2008-11-03
I get this error when trying to run f2py:

numpy.distutils.fcompiler.CompilerNotFound: gnu: f90 nor f77

It appears g77 and g90 have been dropped in favor of the new and improved gfortran. That's nice and all, but old scripts don't appear to be recognizing it as a suitable fortran compiler - a significant problem, in my neck of the woods.

Any suggestions?

---

### Post by nhmc on 2008-11-10
I've also noticed the loss of g77.  gfortran doesn't appear to compile fortran 77 code I have that g77 did compile without errors. Is there any way to reinstall g77 in intrepid?

---

### Post by jdwood83 on 2008-11-10
I don't think there is any intent (as of yet) to reintroduce g77 to Ubuntu. I (and many others) are thoroughly disappointed in this. I use g77 on a daily basis before the upgrade and am getting by using my lappy (still at 8.04). If they don't add it soon, I'm gonna do a reinstall of 8.04

---

