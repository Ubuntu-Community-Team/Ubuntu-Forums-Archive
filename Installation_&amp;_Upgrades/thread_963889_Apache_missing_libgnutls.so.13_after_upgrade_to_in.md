---
title: "Apache missing libgnutls.so.13 after upgrade to intrepid"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by pnlarsson on 2008-10-30
Hi,

after upgrading to intrepid, apache won't start - it fails with:

 * Starting web server apache2                                                                                                                                                                                        /usr/sbin/apache2: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory

libgnutls13 don't exist in intrepid, libgnutls26 is available and installed.

I have tried to remove and purge apache2 and the install again - but no success.

Any more ideas?

/niklas

---

### Post by pnlarsson on 2008-10-31
I have now solved this by downloading libopencdk10_0.6.6-1ubuntu1_i386.deb and libgnutls13_2.0.4-1ubuntu2.1_i386.deb from the hardy reps. After a dpkg -i all is well and apache2, cupsd and flash in firefox is now working!

But this is a bandaid fix - what is the real problem?

/niklas

---

