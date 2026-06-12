---
title: "Having some trouble while trying to update."
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by T4RTER S4UCE on 2008-04-20
I just started using Ubuntu on my laptop about two weeks ago. Since the release was near enough I decided I would download the early version of 8.04, but I have had a problem with updating. Every time I try to update it comes up with this message;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

     I'm not very experienced with computers so I, so I decided to just stick; 'dpkg -- configure -a' through the command line. When I did it told me that I needed "superuser privileges" to run it.
     
     So I guess my question is; How do I get 'superuser' privileges, or should I be doing something entirely different.

---

### Post by oilchangeguy on 2008-04-20
type:
sudo dpkg --configure -a

---

### Post by Iandefor on 2008-04-20
prefix the command with sudo:```
sudo dpkg --configure -a
```For more information, feel free to consult this [helpful article]("https://help.ubuntu.com/community/RootSudo").

---

### Post by T4RTER S4UCE on 2008-04-20
That appears to have worked.
Thank you very much.

---

