---
title: "Ram not being flushed"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wfp on 2010-03-21
Strange behavior on a clean restart i will see used Ram 713MB. Free Ram 1172MB. buffers/cache used 516MB. Free 1369MB. Now If i reboot right after this i see used Ram 453MB. Free 1451MB. buffers /cache used 262MB free 1623MB. Why the big difference htop shows nothing using up the ram, it least nothing I can see. Not really worried about the ram that much because i never use it all any way.

---

### Post by dcstar on 2010-03-21
> **wfp said:**
> Strange behavior on a clean restart i will see used Ram 713MB. Free Ram 1172MB. buffers/cache used 516MB. Free 1369MB. Now If i reboot right after this i see used Ram 453MB. Free 1451MB. buffers /cache used 262MB free 1623MB. Why the big difference htop shows nothing using up the ram, it least nothing I can see. Not really worried about the ram that much because i never use it all any way.

Every time you restart after any significant period of off-time certain scheduled cron jobs will run, they do not need to run after a reboot a few minutes later.

Comparing a boot after hours (or days) powered off to one a few minutes later is not valid:
```
man anacron
```

---

### Post by wfp on 2010-03-21
Thanks.:)

---

