---
title: "uninstall ubuntu with system restore?"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Agzander101 on 2011-08-21
before i go and get rid of wubi for the real deal, i would like to know if i can get rid of ubuntu by doing a system restore. i never mind doing system restores and i have my recovery disks if needed

thanks

---

### Post by wojox on 2011-08-21
If you want to uninstall wubi open Run and type:

```
C:\ubuntu\Uninstall-Ubuntu.exe
```

---

### Post by Mark Phelps on 2011-08-22
A common misconception is that MS Windows Restore works like a "time machine", that is, it restores the state of your PC to some earlier date.

It does NOT do that.

Instead, what it does is replace some Windows system files and some registry entries with older files and registry entries.

So, since Wubi intalls Ubuntu in a manner similar to Windows apps, it's possible that running System Restore will remove it.  But it will also remove all other Windows Updates since then.

If you've tried to uninstall it and that doesn't remove it, you can remove it manually by doing the following:
1) Find the Wubi system file and remove it (I think it's called root.disk or something like that)
2) Download and install EasyBCD from the NeoSmart Technology forums, run it, and use the Edit Boot Menu option to remove the Ubuntu entry.  Save the result.

This will get rid of the essential components of Wubi.  It won't clean out registry entries, but since you're not using Wubi anymore, that won't matter.

---

### Post by Agzander101 on 2011-08-26
no i mean get rid of the actual thing

---

### Post by Mark Phelps on 2011-08-27
> **Agzander101 said:**
> no i mean get rid of the actual thing

The "actual thing" is the root.disk file I mentioned.

Follow the instructions in my earlier post -- and that will get rid of Ubuntu.

---

### Post by bcbc on 2011-08-27
Refer to [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

---

