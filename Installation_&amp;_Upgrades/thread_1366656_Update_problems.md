---
title: "Update problems"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by mattyvette on 2009-12-28
I keep having the same message come up when I try to update my computer.  If someone can please help me, that would be great.  Below is a copy of the message that I keep getting.  

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

my e-mail is [EMAIL="stonefamily2003@comcast.net"]stonefamily2003@comcast.net[/EMAIL].

---

### Post by avtolle on 2009-12-28
Go to the terminal Applications>Accessories>Terminal and at the prompt type ```
sudo dpkg --configure -a
```
You will be asked for your password, which will not appear in the terminal (no ***, etc., just a blank), and after typing that in, you will receive some messages. If additional errors are reported, please post them here.

---

### Post by phillw on 2009-12-28
> **mattyvette said:**
> I keep having the same message come up when I try to update my computer.  If someone can please help me, that would be great.  Below is a copy of the message that I keep getting.  

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

my e-mail is [EMAIL="stonefamily2003@comcast.net"]stonefamily2003@comcast.net[/EMAIL].

Hi & Welcome.

Have you Ran ```
sudo dpkg --configure -a
``` ?

Regards,

Phill.

---

