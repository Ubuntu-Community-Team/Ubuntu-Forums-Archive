---
title: "installing winamp"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-11-24
Hi folks anyone got it working on jaunty?

I have got as far as it wants libpng.so.2,

I can't find it. Tried a symlink to.12 or whatever it is.  It said "wrong version"  Can't recall its exact error.

```

root@tux:/usr/lib# root@tux:/usr/local/Winamp# ./Winamp
Debug> Profiler: load locales settings: 13 ms

libpng.so.2: cannot open shared object file: No such file or directory
Debug> Profiler: wacs/pngload.wac: 143 ms

Debug> Profiler: load db from disk: 0 ms

"Bitmaps/pledit-unselected.png"
Expression: bits
File: imgldr.cpp
Line: 260
Aborted
root@tux:/usr/local/Winamp# 

```

Any ideas?  It works on puppy!

---

### Post by Mark Phelps on 2009-11-24
See the link below to the WinHQ site on application compatibility for some tricks on installing WinAmp:  

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5")

---

### Post by Wobblybob on 2009-11-24
Have you thought about using Audacious from the repos, it's very much like Winamp

---

### Post by johnh10000 on 2009-11-24
> **Mark Phelps said:**
> See the link below to the WinHQ site on application compatibility for some tricks on installing WinAmp:  

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5")

Thanks for that, but the one in wine-doors I thinks, works fine.  I'm trying to the rpm -> deb one going in native ubuntu jaunty.

And in answer to have I use audiousious, I have I like it.  But winamp is just a chalenge..  It dosen't help the script is called Winamp (note upcase W)  and in it they shove all the errors to /dev/null which doesn't
help!

---

