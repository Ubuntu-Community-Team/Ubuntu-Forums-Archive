---
title: "Installing Ubuntu on RAID 0"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by acascianelli on 2006-07-02
I'm trying to install Ubuntu 6.06 on my system with an IC7-Max3 running 2x160gb's drives in RAID 0.  They are running off the Intel RAID controller.  When I try to run the Ubuntu installer, it still finds 2 seperate drives.

I've had this problem with Redhat distro's before but never Ubuntu.  Anybody know how to make Ubuntu see the logical RAID 0 drive?

---

### Post by scxtt on 2006-07-02
i had the same problem w/ my hardware RAID0 controller :(

---

### Post by acascianelli on 2006-07-02
[QUOTE=scxtt]i had the same problem w/ my hardware RAID0 controller :([/QUOTE]

What did you end up doing?  I think it may be easier if I were to use the onboard PCI RAID controller instead of the ICH5R.

---

### Post by scxtt on 2006-07-02
i ended up not doing anything about it at all :( ... i suppose my only recourse now is a software RAID0, which i might do someday (next reinstall sometime in the FAR future) ... i blame my chipset, cause even in windows it takes some special driver ...

---

