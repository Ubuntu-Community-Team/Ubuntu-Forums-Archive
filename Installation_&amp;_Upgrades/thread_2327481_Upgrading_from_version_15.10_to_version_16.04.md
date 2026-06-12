---
title: "Upgrading from version 15.10 to version 16.04"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by RichardET on 2016-06-11
I upgraded my system from version 15.10 to 16.04 via the online upgrade option.  It went well and everything works.  But since this system was originally a 15.10 system, there were historical remnants of 15.10 listed within the 'software & updates' menus;  I simply removed the line listing the 15.10 disk as a software repository and edited the ppa source from wily to xenial.  Is this what everyone does?  Does it matter?

---

### Post by bapoumba on 2016-06-11
It is best to disable the ppas on upgrade. You probably got lucky it all went well without trouble :)

---

### Post by grahammechanical on 2016-06-11
If you run

```
sudo apt update
sudo apt upgrade
```

You might see "not found" errors if those PPAs do not exist in xenial. And sometimes the developer has not moved their Personal Package Archive into the xenial repositories. They may not have upgraded their software to Xenial. PPAS are used to install software. Not all PPAs are used to update software. Those kind of PPAs I disable once the software has been installed.

Regards

---

