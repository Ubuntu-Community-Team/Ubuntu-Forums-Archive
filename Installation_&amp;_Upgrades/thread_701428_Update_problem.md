---
title: "Update problem"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Pinpoint Focus on 2008-02-19
I have run the script dpkg --configure -a in the the terminal and received a message saying I'm not in super user mode, even though I have $ showing at the prompt.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


How do I access the super user mode to run the script dpkg --configure -a ?

Many thanks,

Robert

---

### Post by erfahren on 2008-02-19
> **Pinpoint Focus said:**
> 
How do I access the super user mode to run the script dpkg --configure -a ?

put "sudo" before it
as in 
```

sudo dpkg --configure -a

```

---

### Post by Pinpoint Focus on 2008-02-20
Thanks,  that sorted out the problem.

Robert

---

