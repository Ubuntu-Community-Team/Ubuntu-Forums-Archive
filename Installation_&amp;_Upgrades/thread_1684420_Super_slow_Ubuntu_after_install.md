---
title: "Super slow Ubuntu after install"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by phxtom on 2011-02-09
I installed Ubuntu 8.04 in a dual boot with Win 2000. After the install I immediately installed all updates. Then I upgraded it to 9.04. Afterwards, Ubuntu was extremely slow! For example, mouse lag of at least 5 seconds. Click to open a folder, 45 second delay. No matter what I click on it's extremely slow. Also on the pull down menus several programs are missing. I believe my only option is to uninstall Ubuntu and start over again. 
My question is How do I uninstall Ubuntu??

---

### Post by slooksterpsv on 2011-02-09
> **phxtom said:**
> I installed Ubuntu 8.04 in a dual boot with Win 2000. After the install I immediately installed all updates. Then I upgraded it to 9.04. Afterwards, Ubuntu was extremely slow! For example, mouse lag of at least 5 seconds. Click to open a folder, 45 second delay. No matter what I click on it's extremely slow. Also on the pull down menus several programs are missing. I believe my only option is to uninstall Ubuntu and start over again. 
My question is How do I uninstall Ubuntu??

Reinstall, just when you setup Ubuntu, you'll have too manually do the partitions, and you'll just choose the one that was previous Ubuntu, click on it, choose Change, change it to the current partition format (so if it was Ext3, choose Ext3), and choose mount point as /.

DO NOT CLICK ON FORMAT UNLESS YOU HAVE YOUR DATA BACKED UP

After that, click on swap, click on Change, for the format, choose Swap and click on OK, then make sure Grub is where you want it to be installed (default is to take over any other boot managers), and choose continue.

That's how I do it when I reinstall, that usually leaves my /home folder in tact, but reinstalls the OS.

---

