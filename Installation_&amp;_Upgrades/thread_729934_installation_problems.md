---
title: "installation problems"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by greggybell on 2008-03-20
im new to unbuntu and i have gutsy. Every time i try to install or download anything it comes up with this: [I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.[/I]

where do i run it from? or what do i do?

thank you

---

### Post by ohzopants on 2008-03-20
You have to run this command in the terminal.

You will probably have to run this actually:
```

sudo dpkg --configure -a

```

---

### Post by greggybell on 2008-03-20
thank you, what do i do next or is that it?

---

### Post by ohzopants on 2008-03-20
dpkg is a program to install programs from .deb files.  Synaptic and Aptitude use it (somehow... I think).  If you are installing software and something bad happens your database of installed programs and dependencies can become broken.  That command should have fixed it.  

To make sure it worked, try to install something.  It doesn't have to be a new program, updates are a good test too.

---

