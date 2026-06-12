---
title: "ghc6 Hash Sum mismatch ==&gt; upgrade fails"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dt96hasv on 2007-10-18
I've just upgraded to Gutsy, it worked flawlessly (well, lost a font, but that was easily fixed) except that the upgrade of GHC exited with a Hash Sum mismatch:
```

Failed to fetch http://se.archive.ubuntu.com/ubuntu/pool/universe/g/ghc6/ghc6_6.6.1-2ubuntu2_i386.deb  Hash Sum mismatch

```

Temporarily removing the package solved the upgrade, however my ability to work is somewhat crippled ;-) Trying to install afterwards gives me the same error, is there some way around this, and should the error be reported somewhere?

---

### Post by dt96hasv on 2007-10-19
This seems to only affect some repositories, so if you have this problem, the simple solution is:

1) Remove ghc6
2) Upgrade to gutsy
3) Choose another repository (non-swedish in my case) and re-install ghc6 

/Hans

---

### Post by hmus on 2008-01-13
hello guys..im getting the same  "Hash Sum mismatch" error, but in my case for every package i would try to install...i can't even install my video card, nothing is working.please help my machine be a normal one

---

### Post by zvacet on 2008-01-14
```
sudo apt-get update
```

If that don´t work go to the system>administration>software sources and choose other server.

---

