---
title: "Ubuntu don't boot with windows 8"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by EngAG on 2013-03-08
I have windows 8  and was trying to install ubuntu , i installed it alone in another parition not alongside windows , the problem that after installation finished and i restarted ,windows booted and no sign of ubuntu 
I tried the boot-repair and no thing changed [http://paste.ubuntu.com/5595895/](http://paste.ubuntu.com/5595895/)

Any Ideas !?

---

### Post by oldfred on 2013-03-08
Does Windows boot? Script's NTFS driver is having issues mounting NTFS partition. That is corruption needing chkdsk from a Windows repairCD or hibernated system, which you should not have if dual booting.

And then you do not have grub fully installed. Boot-Repair has an option to uninstall and totally reinstall grub which you may need to run.

---

### Post by EngAG on 2013-03-08
Yes windows 8 boots normally 
I just ran the boot-repair and let it repair automatically !
I'll try to make chkdsk and reinstall grub and see what happen , thanks for replying :)

---

