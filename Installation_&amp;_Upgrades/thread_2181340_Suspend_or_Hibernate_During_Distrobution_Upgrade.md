---
title: "Suspend or Hibernate During Distrobution Upgrade"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by bstrawn689 on 2013-10-17
If I was to suspend or hibernate my computer during a distribution upgrade to Saucy Salamander would it effect the upgrade? If either suspending or hibernating works let me know... Thanks in advance.

---

### Post by grahammechanical on 2013-10-17
Why don't you try it and tell us.

The last thing an upgrade needs is to be stopped part the way through it, whether the power is switched off deliberately or by accident. You will likely find that when you try to come out of suspend or hibernation that you are loading a broken OS.

Think about what an upgrade has to do. It has to identify all the packages on the machine and work out what needs to be upgraded. It then needs to download all of the upgraded packages and then remove the old ones whilst changing over to the new ones and all the time remaining a working OS.

I am always amazed that it works at all and I am never surprised if something goes wrong.

---

### Post by bstrawn689 on 2013-10-18
Well, I did hibernate while it was downloading updates for the distribution upgrade. Not surprising that it didn't effect anything. I feel that hibernate should work because it saves the state that the cimputer was in before shutting down as opposed to closing everything and than shutting down. In other words, it should save the exact point it was at during the distribution upgrade.

---

### Post by Frogs Hair on 2013-10-18
There are some threads related to interrupted upgrade problems. The download may not be affected but the unpacking and set up of new packages could be affected. There may also be installer questions during the upgrade an so it wouldn't proceed until answered .

---

### Post by bstrawn689 on 2013-10-19
I actually Hibernated a second time during the upgrade process. This was when it was replacing packages with the new downloaded ones. I since restarted the computer after the upgrade completed and the upgrade did succeed. Nothing seems to be wrong. I might have completed the upgrade by luck....hibernating at just the right times.

 Anyway, thanks for the help and if anyone can give a definite answer about whether you can Hibernate or not let me know...although from what everyone said so far it seems risky.

---

