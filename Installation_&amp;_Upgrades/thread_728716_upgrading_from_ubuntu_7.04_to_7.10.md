---
title: "upgrading from ubuntu 7.04 to 7.10"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by krsgypsy on 2008-03-19
trying to upgrade from ubuntu 7.04 to 7.10...

this is the error message i get when trying to upgrade using update manager:

Failed to fetch [http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz) 302 Found

then it suggests that it could be due to a network problem but, i have tried upgrading on different networks so i do not believe that is the problem.  in short, what am i doing wrong?

---

### Post by PmDematagoda on 2008-03-19
Open Software Sources in System>Administration>Software Sources, go to the Third Party Software tab and disable all the options there.

After that is done, try upgrading Ubuntu again.

---

### Post by krsgypsy on 2008-03-19
hey thanks a lot, everything ran smoothly and i have successfully upgraded to 7.10  thank you for your time and help.

---

### Post by kostkon on 2008-03-20
Now, in case you want to add the *Medibuntu* repository back again, you can find it at [http://medibuntu.org/]("http://medibuntu.org/"). You were using the old url for the repository which does not work anymore. That's why you got the error message.

---

