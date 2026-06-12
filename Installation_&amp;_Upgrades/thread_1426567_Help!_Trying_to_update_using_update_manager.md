---
title: "Help! Trying to update using update manager"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by naught405 on 2010-03-10
I have an Asus Eee PC 1005HAB with unr 9.10.  It works great except the update manager keeps trying to update but when I click install updates I get this error message right away > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried going to terminal and typing in exactly 'sudo dpkg --configure -a' but that didn't do anything.  Help, what do I do?

---

### Post by Sef on 2010-03-10
> I tried going to terminal and typing in exactly 'sudo dpkg --configure  -a' but that didn't do anything.  Help, what do I do?

When you type in the command do not use the quotes.  It should be like this:

```
sudo dpkg --configure  -a
```

copy and paste the code in if you want.

---

### Post by naught405 on 2010-03-10
uh, i do know how to enter commands...

---

### Post by naught405 on 2010-03-10
Figured it out. It was simply a matter of running the command while the update manager was still open.  I generally close windows I'm not working in on a netbook since I only have 1 screen and its small at that.

---

