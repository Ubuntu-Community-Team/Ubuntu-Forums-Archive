---
title: "lucid; kernel panic when mounting; but not in previous version..."
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by DoppyNL on 2010-05-16
Hi People,

Got something I can't wrap my head around...

System:
Ubuntu 10.04 Lucid; clean install; 32bit

When booting, I can choose 2 from 2 options (ignoring recovery mode):
- Ubuntu, with Linux 2.6.32-22-generic
- Ubuntu, with Linux 2.6.32-21-generic
(and then Windows Vista and Ubuntu 9.10 a couple of times)
The newer version appeared with an update from Ubuntu a couple of days after installation.


When booting from the first I get the following message:
```
Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```


When booting from the second, Ubuntu loads without a problem.

anyone know what is going on here?
Need more info? just let me know what.

---

### Post by alphacrucis2 on 2010-05-16
> **DoppyNL said:**
> Hi People,

Got something I can't wrap my head around...

System:
Ubuntu 10.04 Lucid; clean install; 32bit

When booting, I can choose 2 from 2 options (ignoring recovery mode):
- Ubuntu, with Linux 2.6.32-22-generic
- Ubuntu, with Linux 2.6.32-21-generic
(and then Windows Vista and Ubuntu 9.10 a couple of times)
The newer version appeared with an update from Ubuntu a couple of days after installation.


When booting from the first I get the following message:
```
Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```


When booting from the second, Ubuntu loads without a problem.

anyone know what is going on here?
Need more info? just let me know what.

There was a similar thread:

[http://ubuntuforums.org/showthread.php?p=9271554]("http://ubuntuforums.org/showthread.php?p=9271554")

---

### Post by DoppyNL on 2010-05-17
Looks very similar indeed.

But I'm not missing the file "initrd.img-2.6.32-22-generic" in my /boot dir.
It is also mentioned in grub.conf.
So it seems to be something else...

Perhaps try to recreate the file? using the instructions from the other thread? perhaps the file is corrupt or something... Can I safely do that?

---

