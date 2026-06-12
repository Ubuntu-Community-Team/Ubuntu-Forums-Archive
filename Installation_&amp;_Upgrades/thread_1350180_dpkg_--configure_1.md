---
title: "dpkg --configure 1?"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by pifactory on 2009-12-09
I'm trying to run update manager but get the message:

E: dpkg was interrupted you must run 'dpkg --configure-a' to correct the problem.

Some explanation + advice how to do this please.

I'm trying to upgrade.

Thanks

---

### Post by mikewhatever on 2009-12-09
Open Applications->Accessories->Terminal, type in, or copy/past the following command, hit enter and type your password.

```
sudo dpkg --configure -a
```

---

