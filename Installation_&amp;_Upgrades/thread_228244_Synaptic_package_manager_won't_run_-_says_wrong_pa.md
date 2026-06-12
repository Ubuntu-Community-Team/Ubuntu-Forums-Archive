---
title: "Synaptic package manager won't run - says wrong password"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by PsiPhi on 2006-08-02
Got a fresh install of Dapper from the 6.06 LTS CD.
Everything totally vanilla and when I try to run Synaptic I get a pop-up message that says "*Failed to run /usr/sbin/synaptic as user root: Wrong password*"
The password I used was the password I logged in with, the user created during installation.
When this didn't work I created a password for root and tried that instead, still no luck (so I removed the root password again).
I can run it from the command line (sudo synaptic) though, and with the normal user password it works.
Same applies to other root level applications, like services-admin.

---

### Post by aysiu on 2006-08-02
Change the Synaptic command to this: ```
gksudo synaptic
```

---

### Post by PsiPhi on 2006-08-03
Thanks, that worked. 
Two things though.
 1. For other newbies reading this the application "**Alacarte Menu Editor**" under Accessories is what you use.
 2. Why did Ubuntu install with the command **gksu** instead of **gksudo**?

Previously I had Breezy Badger installed and the same thing happened. After I had installed about 4 or 5 times (for other reasons) it was OK?

---

