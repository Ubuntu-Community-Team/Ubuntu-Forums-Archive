---
title: "[SOLVED] Songbird 0.5"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by Jeenyus on 2008-08-05
I am trying to install Songbird 0.5 because I use Feisty and I've heard about a bug in Songbird 0.6 that prevents it from working correctly on some of the older systems.  I downloaded the .deb file and when I double click to install it this message appears in the package installer "Error: Dependency is not satisfiable: libc6"  I have no idea what this means and I am seeking guidance to get this working.  Thank you.

---

### Post by spiderbatdad on 2008-08-05
libc6 is a library. The package is available in synaptic. If you ran:```
sudo apt-get install libc6
```I believe you will see that it is already installed.

BE CAREFUL. do not try remove and reinstall libc6. You will wipe out your entire system, I believe...though it should warn you. I think something is wrong with the way that version of songbird is packaged.

I'm not entirely sure what libs feisty uses, but fairly sure about the above...that is, you already have it. So, I recommend use the other version of songbird or use a different player. songbird isn't that great for very large databases, anyway.

---

