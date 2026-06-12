---
title: "Niceness has no effect"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bruce89 on 2009-01-30
Using BOINC on Jaunty is a pain, as niceness doesn't seem to have any effect for some reason.

Has anyone else got this issue?

---

### Post by marmuta on 2009-01-30
Ugh, you got me scared. I thought user scheduling is enabled again in the kernel, but it it's not
```
grep -i user_sc /boot/config-2.6.28-6-generic 
# CONFIG_USER_SCHED is not set

```
I can't find anything wrong with nice. What are you seeing?

---

### Post by ssam on 2009-01-30
maybe this lkml thread is of interest
[http://thread.gmane.org/gmane.linux.kernel/787645](http://thread.gmane.org/gmane.linux.kernel/787645)

---

### Post by bruce89 on 2009-01-30
> **ssam said:**
> maybe this lkml thread is of interest
[http://thread.gmane.org/gmane.linux.kernel/787645](http://thread.gmane.org/gmane.linux.kernel/787645)

Nice, thanks.

This means I can't do anything processor-intensive without disabling BOINC (if I want to to not take ages).

---

