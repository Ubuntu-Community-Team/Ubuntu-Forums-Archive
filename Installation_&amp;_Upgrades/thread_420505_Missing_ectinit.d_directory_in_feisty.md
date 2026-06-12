---
title: "Missing ect/init.d directory in feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by kathmary on 2007-04-23
After uninstalling VMware Server, I now seem to be missing ect/int.d directory.  I noticed this after the  message from the VMware Workstation installer that asks: 


```

```  "What is the directory that contains the init scripts? [/etc]"

This is not the correct directory, according to what I have read.  It should be ect/init.d


I don't know what to do.  I booted up a live cd and saw that there is an ect/init.d directory on it.   I don't want to reinstall Ubuntu unless there is no other way.  Someone please help!!!

By the way, I am using Feisty.

---

### Post by taurus on 2007-04-23
Nope.  It is **/etc/init.d**.

---

### Post by SishGupta on 2007-04-23
The defaults for the vmware installation should work...

I always just mash enter past everything.

---

### Post by kathmary on 2007-04-25
Thanks for answering me!  I am still not used to knowing what files are what on linux.  It seems I deleted the init.d folder somehow when uninstalling Vmware.  Probaby deleted the whole folder rather than just a file in it!

---

### Post by taurus on 2007-04-25
If you removed the whole directory /etc/init.d, then you shouldn't be able to boot.  And if you are able to boot into GUI, then you still have /etc/init.d.  What's the output of this command from a terminal?

```
ls -la /etc/init.d
```

---

