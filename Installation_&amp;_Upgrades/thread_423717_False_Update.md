---
title: "False Update?"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2007-04-26
A version check shows 7.04, but I never got an "update successful" message, or anything like that.  Is it possible that in all the screwing around and aborted attempts that the upgrade is only partially done?  

How do I make sure that it really is 7.04, in some way other than the version file check?

---

### Post by Bernhard001 on 2007-04-26
Code: 

lsb_release -a

???

---

### Post by eentonig on 2007-04-26
Which should give you an output like

> me@MyPc:$ lsb_release -a
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:core-3.0-ia32:core-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
rfonteyn@EvoN600c:$ 

---

### Post by bapoumba on 2007-04-26
And:
```
~$ lsb_release -cd
Description:    Ubuntu 7.04
Codename:       feisty

```
for a shorter answer.

---

### Post by RogerDavis on 2007-04-26
OK, these all say 7.04, but I do see one big difference.  lsb_release -a does not show any LSB modules on mine, where that command on eentonigs machine shows several.  What's an LSB module, and is it bogus that I have none?

roger@roger-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
roger@roger-desktop:~$

---

