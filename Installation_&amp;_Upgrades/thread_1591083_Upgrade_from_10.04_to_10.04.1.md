---
title: "Upgrade from 10.04 to 10.04.1???"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by EvansFive on 2010-10-08
I have been running 10.04 for a while and I noticed while browsing forums that 10.04.1 exists.

BUT...when I run update manager I do not see any option to upgrade to 10.04.1.

All I get is "Your system is up-to-date".

Do I need to upgrade to 10.04.1 or are all the fixes included in my up to date 10.04?

If I need to upgrade to 10.04.1, how do I do this?

Thanks!

---

### Post by lisati on 2010-10-08
If you have been keeping things up-to-date with the update manager, you'll be fine.

---

### Post by EvansFive on 2010-10-08
Cool thanks for the quick response!

---

### Post by efflandt on 2010-10-09
If you have kept things updated check the output of: **cat /etc/*release**

You may be surprised.

---

### Post by spcwingo on 2010-10-09
If you've been updating your probably already running it.  You can find out by running this command in a terminal:

```
lsb_release -a
```

---

