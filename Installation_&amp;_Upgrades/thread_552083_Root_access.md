---
title: "Root access"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by Mr G on 2007-09-16
I installed Ubuntu and everything went great.  I was wanting to install add-ons in the form of bin files which you need to have access to the root.   I try to access this, but I'm denied access.  The only password I ever setup was the one to sign on.  What can I do?

---

### Post by Koybe on 2007-09-16
Ubuntu is uding the group admin and the sudo command to gain root access. So you should gain root acces using :
```
sudo 'your command'
``` then type your own password. and in fact ```
sudo su
``` to get root.


[There]("https://help.ubuntu.com/community/RootSudo") you can find some info

---

