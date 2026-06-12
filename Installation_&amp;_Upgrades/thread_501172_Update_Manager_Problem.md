---
title: "Update Manager Problem"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Vuto on 2007-07-14
When I try and install updates in the update manager it always come up with 
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
So I typed in > dpkg --configure -a in the terminal and then it came up with
> dpkg: requested operation requires superuser privilege

coud someone please help me fix this problem? and what is a superuser?

---

### Post by scrooge_74 on 2007-07-14
type sudo dpkg--reconfigure -a

then type your password and that should set things right

Remember that for admin task you use the sudo command and give your password, either from the command line or from inside your GUI of choice

---

