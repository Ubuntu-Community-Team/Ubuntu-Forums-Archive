---
title: "is there really any development eviroment for ubuntu ?"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by supertappy on 2010-03-04
sorry i'm a bit of a noob with ubuntu, but have been using the dreaded windows for many years, programming. My tool of choice is Delphi, which no longer exists for linux.

There is this freeware (of course) application called lazaraus which I can install, but whenever i try even run the simple program i get

/usr/lib/lazarus/0.9.28.2/lcl/masks.pas(28,22) Fatal: Can't find unit contnrs used by Masks

what happened to setup.exe? and all needs doing to install, just click next, next, next ,next, wait a bit and there is delphi sitting in the start menu, and it works

ending rant now

sighs

---

### Post by supertappy on 2010-03-04
and yet again trying eclipse with c++

sudo apt-get install eclipse eclipse-cdt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
eclipse is already the newest version.
E: Couldn't find package eclipse-cdt

---

### Post by n0dix on 2010-03-04
Try with:
```
 $ sudo apt-get install eclipse 
```

---

### Post by Mighty_Joe on 2010-03-05
> **supertappy said:**
> 
what happened to setup.exe? and all needs doing to install, just click next, next, next ,next, wait a bit and there is delphi sitting in the start menu, and it works


Are you trying to run a Windows executable on Linux? It does not work that way. Did you try installing Lazarus through Synaptic?
It looks like eclipse-cdt is not in the main Ubuntu repository.  Do you have the universe repository enabled?

---

### Post by supertappy on 2010-03-06
>>Are you trying to run a Windows executable on Linux?

no, um that wont work obviously

>>It looks like eclipse-cdt is not in the main Ubuntu repository. >>Do you have the universe repository enabled? 

i'll check it

thanks

---

