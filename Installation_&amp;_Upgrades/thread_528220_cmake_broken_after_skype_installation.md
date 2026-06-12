---
title: "cmake broken after skype installation"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Belveder on 2007-08-17
Hi everybody!

Today I installed Skype from the homepage, skype-debian_1.4.0.99-1_i386.deb, which also installed the dependencies libqt4-gui and libqt4-core. Well, Skype works fine, but cmake is broken now. Whenever I try to run cmake I get a lot of errors, for example 

CMake Error: Error required internal CMake variable not set, cmake may be not be built correctly.
Missing variable is:
CMAKE_SIZEOF_VOID_P

I've tried reinstalling cmake, removing the packages installed by Skype, but nothing worked, the problems are still there. Any ideas?

Ciao
Clemens

PS: Now I've tried to run cmake as super-user - it works - does this mean that any permissions are not set correctly now???

---

### Post by Belveder on 2007-08-18
Hi again,

I've tried to run cmake in the /tmp folder on an ext3 share and that works, while it does not work on a vfat mount. This makes me think that my skype installation hasn't got anything todo with the cmake problem at all. But the strange thing is that I've run it 100 times before the installation and it worked, and now it's broken. 

Maybe I'll ask the cmake mailing list...

Clemens

---

