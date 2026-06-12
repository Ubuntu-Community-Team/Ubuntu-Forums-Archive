---
title: "[SOLVED] upgrage manager dpkg --configure -a"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by newbemac on 2008-08-26
hi to all.

I just attempted to use upgrade manager and received this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have never received this before and when I entered "dpkg --configure -a"
in to terminal I receive a message advising I need to be a superuser.
any help?

thanks

---

### Post by Joeb454 on 2008-08-26
Enter ```
sudo dpkg --configure -a
```

---

### Post by newbemac on 2008-08-26
that was the fix.. many thanks

---

