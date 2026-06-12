---
title: "Unable to open lock file?"
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by levi5 on 2014-11-29
Hi, I'm trying to install a few things via terminal but all I get is this message
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```
Any help? The stuff isn't important, just a couple gaming related things I could do without if i wanted, but I thought I'd check with the wizards here first.

---

### Post by steeldriver on 2014-11-29
What terminal command are you typing, exactly? are you using `sudo` to obtain root privileges?

---

### Post by levi5 on 2014-11-29
No I'm not, I'm using the apt get one to get a few things and nothing will installl.

---

### Post by levi5 on 2014-11-29
Thanks a bunch, I used sudo and it worked :D

---

### Post by Bucky Ball on 2014-11-30
Good news. Please mark the thread as solved to help others (see the second link in my signature).

Tip: whenever you get a 'Permission denied', try with 'sudo' at the beginning of the command. That is usually the issue.

Good luck. ;)

---

