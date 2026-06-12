---
title: "Upgrade or Fresh Install?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by brk3 on 2007-10-18
I'm running Feisty and am looking forward to getting on to Gutsy.  Question is, how is the sucess rate with the upgrade manager or do the team recommend backing up and a fresh install?

Thanks in advance.

---

### Post by linuxwizard on 2007-10-18
If you upgrade make sure you remove are disable any repos you have added to your source list. If you have used automatix you could have issues upgrading. 

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade. If you have used EasyUbuntu or Automatix (neither of which is recommended nor supported), you may have problems upgrading to a newer version that requires a fresh install.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes).

---

### Post by cogadh on 2007-10-18
I went the upgrade route and everything worked fine, but I decided to try a clean install anyway and have regretted it completely. The migration manager fails to run, video drivers won't install, screen resolution/settings can't be adjusted, Gnome doesn't load properly... and that's just what I have encountered so far. I highly recommend going the upgrade route, especially if you already have a fully functional Feisty install.

---

