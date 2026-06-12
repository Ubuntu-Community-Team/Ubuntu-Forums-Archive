---
title: "dpkg --configure -a fails with a parse error"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Jarn on 2007-10-22
My upgrade failed so I had to close it and try via apt-get, but now when I try it tells me to run "dpkg --configure -a" and when I do that I get:
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 2 package `libc6':
 `triggers-pendi' is not allowed for third (status) word in `status' field
```

---

### Post by futurezero on 2007-10-23
I had the same problem. I tried to update Kubuntu from Feisty to Gutsy using Adept Manager and my computer stop working in the middle. When I restarted it, I couldn't continue the update. 

Every time a try to use apt or Adept Manager, I receive a message that tells me: "....you must manually run 'dpkg --configure -a' to correct the problem" 

When I run dpkg, i receive the message: "dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 2 package `libc6':
 `triggers-pendi' is not allowed for third (status) word in `status' field"

Do you have any idea what can I do?

---

### Post by Jarn on 2007-10-23
I think I got it to work by renaming 0003.

---

