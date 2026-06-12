---
title: "Wubi not starting"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by Zalastax on 2011-07-30
Running the latest wubi.exe on Windows 7 x64
It creates a %temp%/pylXXX.tmp.exe file (with wubi logo) that it removes after ~1 second.
It creates a %temp%/pylXXX.tmp folder wich is empty and that is not removed.

Running in XP compatibility doesn't help, removing generated files don't work either.
The wubi process dies quite quick and after it gets ~4000kB memory usage

I don't find any log files

---

### Post by bcbc on 2011-07-31
If you have python installed, some people have found removing the python path from the environment variables helps.

---

### Post by Zalastax on 2011-07-31
Thank you, it really worked!

---

### Post by bcbc on 2011-08-01
> **Zalastax said:**
> Thank you, it really worked!

Great! I created a bug report here: [https://bugs.launchpad.net/wubi/+bug/819318](https://bugs.launchpad.net/wubi/+bug/819318)

Please modify/correct it if I missed something or there's additional info you think should be there. 
Thanks

PS you can also mark this thread 'solved' from the thread tools above.

---

### Post by enrybo on 2012-08-17
Awesome! Works great!

---

