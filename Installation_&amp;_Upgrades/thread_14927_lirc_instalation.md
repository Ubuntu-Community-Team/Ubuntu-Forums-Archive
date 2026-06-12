---
title: "lirc instalation"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by Bdfy on 2005-02-10
apt-get install  lirc-modules-source
cd /usr/src/
tar -zxvf lirc-modules.tar.gz
cd modules/lirc
See README
debian/rules KDREV=Custom.1 binary-modules
dpkg -i blablabla.deb
ls lib/modules/2.6.10-2-386/misc/
lirc_sir.o ...
Why lirc_sir.o but not lirc_sir.ko ???? 
Kernel dasn't no support format ..o 
if I compile module from [www.lirc.org](www.lirc.org) - all OK 
Why ?

---

### Post by knathraak on 2005-03-30
This is a problem.  lirc-modules-source seems possibly an old package from debian (anybody know?).  *.o modules are for 2.4 kernels, right?  I wonder if this package has been imported into ubuntu [universe?|multiverse?] without being updated.  I know it's not supported, that's fine but *please*, it needs to be updated or replaced.  lirc is a giant PITA to get going with ubuntu.   I would do it myself, but this is over my head.  There's a large MythTV comunity out there using lirc and a large Ubuntu community.  The intersection of the two is bound to be considerable.   If anyone is working on this or has a good howto for getting lirc going, please help.

Incidentally, on a fresh install of Ubuntu, I could not get the lirc ./setup.sh; make; make install to work until *after* I had gone through the motions of trying to set up the lirc-modules-source first.  Somehow that process, though failing sets something up that allows lirc to go ahead and compile.

This is so frustrating!

---

