---
title: "[SOLVED] Update Manager (error message)"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by Maltaboy on 2008-11-26
Hello all,

I've got a problem with the Update Manager. Whenever I try to update or try to install some additional software, I receive the attached error message.

Could somebody please explain, what i can do to get rid of this?

Regards

---

### Post by taurus on 2008-11-26
Close down the update window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Maltaboy on 2008-11-26
Thanks a lot taurus!

Problem solved.

Regards

---

