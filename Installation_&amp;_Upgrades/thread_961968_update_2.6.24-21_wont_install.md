---
title: "update 2.6.24-21 wont install"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by JordanLeach on 2008-10-28
when i hit the install updates icon it comes with an error reading:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do i do to fix this problem?

---

### Post by Amarsingh0793 on 2008-10-29
You do what it says! 

Open a terminal, type in 
```
sudo dpkg --configure -a
```
Type your password and let it do it's thing. That's it :)!

Hope this helps :P

---

### Post by JordanLeach on 2008-10-29
thank you very much. i really don't know much about this kind of thing. im just getting started. but thank you.

---

### Post by Amarsingh0793 on 2008-10-30
No problem :)

---

