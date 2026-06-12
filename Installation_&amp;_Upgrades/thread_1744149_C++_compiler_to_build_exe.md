---
title: "C++ compiler to build exe?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by arcull on 2011-04-30
Hi there. This may not be the right forum for my question, but anyway maybe someone knows the answer :) I just wonder if this is possible: I would like to build windows application (exe) using NetBeans in my Ubuntu 10.10, coding in C++. Thanks for answers.

---

### Post by dino99 on 2011-04-30
[https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)
[http://stackoverflow.com/questions/2701392/how-can-i-install-a-new-version-of-gcc-on-ubuntu](http://stackoverflow.com/questions/2701392/how-can-i-install-a-new-version-of-gcc-on-ubuntu)

gcc is the ubuntu compiler

---

### Post by arcull on 2011-04-30
> [https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)
[http://stackoverflow.com/questions/2...-gcc-on-ubuntu]("http://stackoverflow.com/questions/2701392/how-can-i-install-a-new-version-of-gcc-on-ubuntu")

gcc is the ubuntu compiler Thanks man, but maybe I didn't make my self clear enough. I would like to build windows exe and NOT linux executable with gcc or similar compiler. Is that even possible? Thanks again.

---

### Post by dino99 on 2011-04-30
> **arcull said:**
> Thanks man, but maybe I didn't make my self clear enough. I would like to build windows exe and NOT linux executable with gcc or similar compiler. Is that even possible? Thanks again.

its all about logical man :(

---

### Post by teachop on 2011-04-30
> **arcull said:**
> I would like to build windows exe and NOT linux executable with gcc or similar compiler. Is that even possible? Thanks again.
Yes, there is a compiler that targets windows in the repositories, look for mingw32 package.  I have not done this, but it sounds like fun.

The sub-forum Development & Programming | Programming Talk may connect you more directly with fellow travelers in this area.

---

### Post by arcull on 2011-04-30
> Yes, there is a compiler that targets windows in the repositories, look  for mingw32 package.  I have not done this, but it sounds like fun.

The sub-forum Development & Programming | Programming Talk may connect you more directly with fellow travelers in this area. Yep, this is it, I'll give it a try, much thanks for help :)

---

### Post by teachop on 2011-04-30
> **arcull said:**
> Yep, this is it, I'll give it a try, much thanks for help :)
Good deal.  Post back sometime how it all worked out, it will be interesting.

---

### Post by srs5694 on 2011-04-30
FWIW, I sometimes use MinGW to compile the Windows versions of my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) and [FixParts](http://www.rodsbooks.com/fixparts/) programs. Sometimes I use Microsoft's Visual C++ under Windows, though. MSVC++ produces smaller binaries, but MinGW is more convenient for me, since my main computer runs Linux. The binary-size issue seems to be because of the need for MinGW to statically link some library code, the equivalent of which is provided by standard Windows DLLs for MSVC++

---

