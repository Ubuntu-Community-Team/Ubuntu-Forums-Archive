---
title: "iopl() system call with Gusty upgrade"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by opscure on 2008-01-23
Hello everyone,

I was previously running LKL in 7.04 and have recently upgraded to 7.10.  For some odd reason the iopl() system call to allow access to all the i/o ports is taking up 50-100% of my cpu.  I have tried alternate programs such as uberkey which uses the same call and have experienced this issue as well.  On occasion the program seems to run out of resources and gets a segmentation fault (core dumped)....  Has anyone else experienced this issue or can think of any possible workarounds?   

Thanks,
-op

---

### Post by opscure on 2008-01-23
This seemed to make it work a bit better:
```
sudo setkeycodes e060 0xe0
```

I was missing a release key, but for some reason still taking up high percentage of cpu (30-50%) and blocking keyboard port and sending continuous stream of keys sporadically.

---

### Post by opscure on 2008-04-02
bump. :confused:

anyone tried it with Hardy?

---

