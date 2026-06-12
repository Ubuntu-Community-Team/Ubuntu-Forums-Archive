---
title: "dpkg interrupted ??"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by jacquesdup on 2008-06-09
I am running the latest Ubuntu, and upgrades have been great,until today. I got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any suggestions? I went to terminal and typed in on the command line
dpkg -- configure -a

and it tells me I need superuser privileges.

Well, I am the admin, and logged in as such, what more is there that I am missing? Any suggestions would be appreciated.

---

### Post by Pumalite on 2008-06-09
sudo dpkg --configure -a

---

### Post by kellemes on 2008-06-09
About superuser privileges etc..
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Sef on 2008-06-09
> Any suggestions? I went to terminal and typed in on the command line
dpkg -- configure -a

and it tells me I need superuser privileges.

Well, I am the admin, and logged in as such, what more is there that I am missing? Any suggestions would be appreciated.

sudo temporarily gives you admin privileges, so you don't need to be admin all the time.

---

