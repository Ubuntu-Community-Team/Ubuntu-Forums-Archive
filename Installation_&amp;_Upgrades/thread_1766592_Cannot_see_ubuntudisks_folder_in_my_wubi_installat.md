---
title: "Cannot see ubuntu/disks folder in my wubi installation"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by aarsalankhalid on 2011-05-24
Hi,

I installed ubuntu 11.04 inside of my Windows 7 using live cd. All was working fine until three hours ago when I started my pc and selected ubuntu, it gave me grub command line. After searching the forum for sometime, I figured it was because grub couldn't find ubuntu. So, I rebooted from win7 and now all I can see is ubuntu.icon, wubi-uninstallation.exe, ubuntu and another folder. ubuntu/disk is missing. Can anyone figure out what's happening?

---

### Post by bcbc on 2011-05-24
Look for hidden folder C:\dir0000.chk - sometimes windows will remove files it believes are corrupted.

Checkout this link for a similar issue. [http://ubuntuforums.org/showthread.php?t=1763600](http://ubuntuforums.org/showthread.php?t=1763600)

In general try and avoid hard shutdowns while using wubi.

---

### Post by aarsalankhalid on 2011-05-24
> **bcbc said:**
> Look for hidden folder C:\dir0000.chk - sometimes windows will remove files it believes are corrupted.

Checkout this link for a similar issue. [http://ubuntuforums.org/showthread.php?t=1763600](http://ubuntuforums.org/showthread.php?t=1763600)

In general try and avoid hard shutdowns while using wubi.

Yeah...figured there wasn't much luck for me :(
Doing a clean installation of Ubuntu now...
Thnx for the help man..and the link you gave is very helpful.

---

