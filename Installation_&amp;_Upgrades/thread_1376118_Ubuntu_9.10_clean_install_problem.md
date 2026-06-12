---
title: "Ubuntu 9.10 clean install problem"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by downthesun01 on 2010-01-08
I'm doing a clean install of 9.10. Everything installed just fine so user up my wifi.  I opened the update manager and started downloading updates but the update manager greyed out. After letting it sit overnight with no change I restarted my computer which led to an umountable file system error. I tried reinstalling ubuntu again and had the same problem. Does anyone have an idea of what the problem could be? I had 9.10 working just fine with wubi before deciding to get rid of windows all together and do a fresh install of ubuntu if that matters..

---

### Post by darkod on 2010-01-08
Boot with ubuntu cd, Try Ubuntu option and in terminal check the filesystem with fsck. If you have only ubuntu now, your root is probably /dev/sda1. If not sure check your partitions first with:
sudo fdisk -l

Once you know which is your root partition, run the check with:
sudo fsck /dev/sda1

Depending where it got stuck, it may or may not help.

---

### Post by running_rabbit07 on 2010-01-08
Sounds like you may have a bad LiveCD.

---

### Post by downthesun01 on 2010-01-08
I've run fsck and that freezes up too. I'm not at home right so I'm not too sure what it said. I think it was something about something "ending in status 1" and  from there it just sits there. I'll post more info when I get home.

---

