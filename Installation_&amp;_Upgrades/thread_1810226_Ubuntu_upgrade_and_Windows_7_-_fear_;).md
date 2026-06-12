---
title: "Ubuntu upgrade and Windows 7 - fear ;)"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by krecik12 on 2011-07-22
Hi. I'm thinking to upgrade my Ubuntu 9.4 to 10.xx. I have dual boot with Windows 7 right now.

I'm afraid that after upgrade I will not be able to boot into my Windows (I have soooo much stuff there...).

What is BEST and 100% save way of doing it?

PS. Once I did upgrade... had to reinstall Windows from scratch :(. Why there is this problem... :(

---

### Post by Mark Phelps on 2011-07-23
You need to do two things -- the first is CRITICAL.

1) Repair CD

Go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  (I'm presuming your PC can boot from CD).  This is CRITICAL to messing around with dual boot, because it is the main way to restore Win7 boot loader capabilities and Win7 boot -- should your Win7 OS filesystem become corrupted for any reason.

2) Image backup

Go to the Macrium Reflect website, download and install their free version in MS Windows.  Use the option to create a Linux Restore CD.  Attach an external drive and image off your Win7 installation.

NOW you have (1) a CD for repairing Win7 boot problems, and (2) a full backup of your Win7 install.

You can now repair/restore as needed -- and proceed.

---

