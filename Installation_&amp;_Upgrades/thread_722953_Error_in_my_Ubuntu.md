---
title: "Error in my Ubuntu"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by salmaansharif on 2008-03-13
Hi All,
When ever i want to update or install new software or try to open synaptec package manager following Error window with error detail comes
E: dpkg was interrupted. You must manually run 'dpkg --configure -a' to correct the problem
E: -cache ->open() failed, please report.

As i am a new ubuntu/linux sytem user please help me to resolve the error

---

### Post by pingpongboss on 2008-03-13
Well, did you try running ```
sudo dpkg --configure -a
```

Also you may need to try ```
sudo apt-get -f install
``` to sort out dependency problems.

---

