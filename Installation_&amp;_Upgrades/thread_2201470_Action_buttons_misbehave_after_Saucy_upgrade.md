---
title: "Action buttons misbehave after Saucy upgrade"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by nonkreon on 2014-01-24
Hello all,

I upgraded to Saucy a few days ago since Raring becomes history on Monday (RIP), by changing the sources.list versions to saucy (I know it's unofficial and not supported, etc.) . Everything went flawlessly except only for one thing: 
Ever since the upgrade the action-buttons shutdown and restart only log me out, and I'm back at login screen. The command ```
sudo poweroff
``` succeeds in shutting down the system, however. 

Any idea why this happens and on how to fix it? I have scanned askubuntu and launchpad for a similar issue but had no luck :<. I don't have any PPA's enabled thus everything I can think of should be the stock version, proposed and backports repo is enabled if that helps.

Thanks for your help!
Regards

---

### Post by egeezer on 2014-01-24
Did you try right-click on the dropdown under your name (top right) and look at Properties?  You might still be able to set it up there.  (Not sure, myself - I tried 13.10 for a while but went back to 12.04.  I can't recall if I used that or the good old sudo shutdown now -h -P)

---

### Post by nonkreon on 2014-01-24
[QUOTE=egeezer]Did you try right-click on the dropdown under your name (top right) and look at Properties? You might still be able to set it up there. (Not sure, myself - I tried 13.10 for a while but went back to 12.04. I can't recall if I used that or the good old sudo shutdown now -h -P)[/QUOTE]I tried removing and readding action-buttons but that didn't help :<. I don't recall ever having such item, could not find it in addable panel items. But the "Log Out" dialog at the Applications menu acts the same way as well.

---

### Post by nonkreon on 2014-01-26
OK, I got this:

Today I tried suspending but that didn't do anything at all. Then I tried to suspend once more and got the error: 
```
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.systemd1 was not provided by any .service files
```

A quick search led me to [this bug report on launchpad]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1196752") and saw installing systemd-shim solved the filers problem, and realised I didn't have systemd-shim installed! Installing it solved my problem.

---

