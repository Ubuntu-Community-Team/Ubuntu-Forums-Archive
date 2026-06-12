---
title: "Installing Second life on ubuntu desktop 11.04"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by laurieturpin on 2011-10-02
Hello

I have a Dell vostro 460  with:
Intel i5 processor 64bit
2GB memory.
Intel(R) HD Graphics Family
I am running ubuntu desktop 11.04

I am trying to install Second Life.
I have downloaded second life from the secondlife website and have unpacked it in my Download directory.

According to the readme file all have to do is:

cd SecondLife-i686-3.0.0.238864
./secondlife

The result is the screen flashes as if it trying to start up but then immediately closes and the program seems to crash. 
I read something about installing ia32-libs but when I tried 

apt-get install ia32-libs 


I got a message saying that the package could not be found.

Has anyone any ideas?

---

### Post by Frogs Hair on 2011-10-02
The packages is listed in my  Ubuntu 11.04  synaptic package manager ?  Here is the description .

```
This package contains runtime libraries for the ia32/i386
architecture, configured for use on an amd64 or ia64 Debian system running
a 64-bit kernel.
```

---

### Post by laurieturpin on 2011-10-08
Thank you for your reply.
It seems I need the proper GPU driver.
Ubuntu at present does not do a driver package I can install.
Since my system is duel boot Window 7 and Ubuntu 11.04 I will access Second Life via Windows 7.
Hopefully getting the latest Intel GPU drivers will soon be available.

---

