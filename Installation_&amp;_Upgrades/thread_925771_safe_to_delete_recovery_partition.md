---
title: "safe to delete recovery partition?"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-09-21
I bought recovery DVDs for my VAIO computer. Can I delete the recovery partiton or will that mess up my computer?

the only thing i'm concerned about is that the recovery partition comes before my Windows partiton, so my boot.ini file reads:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)**partition(2)**\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)**partition(2)**\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

notice it says partition 2, so i guess partition 1 is the recovery. could that mess up my computer??

---

### Post by cariboo on 2008-09-21
If you don't plan on reinstalling windows, go ahead, and delete your recovery partition. You never know, restore cd and dvd have a habit of being in the way until you need them, then they seem to disappear.:)

Jim

---

