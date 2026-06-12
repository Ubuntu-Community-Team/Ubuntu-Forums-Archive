---
title: "Accidentally removed executable permissions from &quot;/usr/&quot;"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by SrijanM on 2014-05-26
Hi,

I accidentally removed executable permissions from '/usr/' and thus all binaries have stopped working. Is there a way to revert it back or I will have reinstall ubuntu?

---

### Post by vanadium on 2014-05-26
Messing up with ownership and permissions in a linux system usually is fatal. Reinstalling is probably your best bet. It is possible to reinstall without erasing disks. In that case, all your user data and configuration will remain intact. Since you are reinstalling exactly the same Ubuntu version, this is safe. You will be up and running again in half an hour.
Before reinstalling, make sure your backup of your user files is up to date, just to be safe.

---

### Post by SrijanM on 2014-05-26
As /usr/bin files were also deprived of execute permissions I could not even boot my system for backup.

---

### Post by tgalati4 on 2014-05-26
Open a terminal:

```
sudo chmod -R +x /usr
```

Don't break your system.

---

