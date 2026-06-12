---
title: "Maple 8 installation || filesystem case sensitivity"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by Tobi Vollebregt on 2005-04-23
Hello,

I'm having some trouble installing Maple 8. I need it sometimes for university and they put a linux version on the CD pack *yay*. Unfortunately, the entire cd filesystem is lowercase, while the script you are required to run accesses mixed-case commands/files/directories. So I copied the entire maple directory of the CD to /maple and tried to fix the case but this doesn't work. I can execute the ./installMapleLinuxSU script, but it exits almost immediately. I checked, and this is because the installer itself exits immediately. I think this might be because of the case-corruption. **Is there some way to mount a file system case-insensitive? Or otherwise, can someone tell me how the Maple 8 install files should be called, so I can rename them by myself?**

Thanks in advance, Tobi

---

### Post by Tobi Vollebregt on 2005-04-25
*YAY* I managed to succesfully install maple (after lots of struggling though).

However, now I can't run it, because errno is in some way undefined in libc. I've currently no idea how to solve this. Anybody?

> 
/root/maple8/bin.IBM_INTEL_LINUX/mserver: relocation error: /root/maple8/bin.IBM_INTEL_LINUX/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


---

### Post by Zhukov on 2005-05-30
Ive posted a solution for your problem, just search for Maple 8 in the search engine of the forums.

The thread is called:

HOWTO INSTALL: Maple 8


Hasta. :grin:

---

