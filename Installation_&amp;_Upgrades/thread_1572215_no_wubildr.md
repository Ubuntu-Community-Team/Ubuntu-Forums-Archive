---
title: "no wubildr?"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by sharkins215 on 2010-09-10
Ok so i ran my installation on the windows side and everything went fine. Then i rebooted and selected the ubuntu installation like it said to but then everything pauses and it says no wubildr. This makes no sense to me because i can go back into windows and look at my C: drive and i can see the wubildr.... Any help greatly appreciated :)

---

### Post by wilee-nilee on 2010-09-10
Here is a link to a wubi wiki, there is a regular user who is usually online soon that is quite good at this wubi thang.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2010-09-10
there have been reports of delays booting wubi due to wubildr not being on the hidden windows boot partition - but I haven't heard of it just hanging. You don't say what version of windows you are using etc. but if it's vista/7 that sounds likely the cause.
[https://bugs.launchpad.net/wubi/+bug/566490](https://bugs.launchpad.net/wubi/+bug/566490)

---

### Post by garvinrick4 on 2010-09-10
Look in the Windows boot manager and see if there is an entry in there with the wubildr in there. It is called bcdedit in Vista and 7

Command line Windows I believe as administrater.
```
bcdedit
```

If there is no entry with its own identifier # with wubildr there it will not boot into Wubi install of Ubuntu.

---

