---
title: "libc6/gcc error?"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by KaiserM08 on 2007-07-05
Hello! My name is Matt. I'm new to this forum but have been using Ubuntu v6.06.01 for almost a year.  I use it for everything I do, but mostly for development.  I downloaded GCC and G++ via Synaptic right after I installed the OS, and they worked fine until about a month ago.  Whenever I tried to compile either C or C++ code, it doesn't work.  It can't find any of the header files I include and doesn't seem to understand anything about the code.  I uninstalled both gcc and g++ and reinstalled both again, but still nothing.  So this pointed me to the possibility of my C Library being messed up.  I can't uninstall it through Synaptic or Apt without uninstalling every program on my computer that uses libc6.  I've tried reinstalling other components like libc6-dev and libstdc, but every time it relies on a DIFFERENT version of the original libc6.  When I try to install the different version of libc6, it says I need a different version of one of the other components.  When I try installing both at once, Apt declares it impossible.  What do I do?  I need C and C++ back...I've tried all I can think of.  Any suggestions?  Thanks for your time,

~Matt><>

---

### Post by taurus on 2007-07-05
You need to install the build-essential package instead of only GCC.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by KaiserM08 on 2007-07-05
> **taurus said:**
> You need to install the build-essential package instead of only GCC.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

It worked, thanks alot!  So why did gcc work before I installed the build-essential?  Thanks again for your help, my development is back on track now!

---

