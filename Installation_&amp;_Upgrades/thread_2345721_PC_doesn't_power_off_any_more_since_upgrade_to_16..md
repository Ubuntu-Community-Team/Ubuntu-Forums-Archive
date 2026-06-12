---
title: "PC doesn't power off any more since upgrade to 16.10"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by roadrash on 2016-12-07
Ever since upgrading from 16.04 to 16.10, my PC no longer powers off.  I select shutdown and it exits ubuntu but PCV stays turned on unless I press the power button. Is there any predominant fix I can do to resolve this?

---

### Post by Jeroen_Mathon on 2016-12-07
Hey Roadrash,

Have you tried running the following commands as root?
```

shutdown -P now
halt
poweroff
systemctl poweroff

```

---

