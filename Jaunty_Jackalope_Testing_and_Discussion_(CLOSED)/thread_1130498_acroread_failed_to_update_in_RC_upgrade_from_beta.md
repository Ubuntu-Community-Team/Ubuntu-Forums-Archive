---
title: "acroread failed to update in RC upgrade from beta"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by raymondh on 2009-04-19
```
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_9.1.0-7jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas on what to do?  This was an upgrade from 9.04 beta to RC

Am looking in launchpad and see a bug, but on 8.10. Thought I'd throw it to the group before I start tweaking.
  
Thanks in advance

Raymond

---

### Post by Rallg on 2009-04-19
Yes, I had some similar error. I don't recall the details, but it might be that the DEB needs to be installed as root (rather than merely sudo). In any case, I ignored the update error message, got the DEB from Adobe, and installed it. Works fine.

---

### Post by FuturePilot on 2009-04-19
Try removing all related Acroread packages then reinstalling them.

---

