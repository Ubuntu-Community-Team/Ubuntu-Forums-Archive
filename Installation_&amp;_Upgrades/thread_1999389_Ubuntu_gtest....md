---
title: "Ubuntu gtest..."
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2012-06-08
Hi, all:

Environment:
OS: Ubuntu 12.04


1) By grabbing libgtest-dev from the repository, it clearly says

> This package contains the header files needed to link programs against gtest.
It seems that libgtest-dev only installs the header files, but no library files installed.


2) Due to 1), it seems I've got to install gtest by myself.
After successfully
> a) download
b) mkdir build
c) cd build
d) ccmake ../
e) make
I failed at the final step 
> f) sudo checkinstall
with the following error messages
 
> Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.



Did anybody meet the same issue? And if so, how did u solve this problem?


Best Regards
Pei

---

### Post by geralds on 2012-07-17
Hi,
have you seen Erik Smistad's excellent tutorial on how to get started w/ gtest in Ubuntu? It's available at [http://www.thebigblob.com/getting-started-with-google-test-on-ubuntu/]("http://www.thebigblob.com/getting-started-with-google-test-on-ubuntu/") and will likely solve your problem.
Regards, g

---

