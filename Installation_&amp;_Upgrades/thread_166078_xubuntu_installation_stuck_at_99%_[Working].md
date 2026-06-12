---
title: "xubuntu installation stuck at 99% [Working]"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by kh4nh on 2006-04-25
Hi guys,
I was trying to install a fresh xubuntu and following the guide closely. After successfully installed the base system, edited sources.list, and apt-get update, i sudo apt-get install xubuntu-desktop. apt-get downloaded packages and got stuck at the point where:

get:99 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main unzip 5.52-3ubuntu2.2 [147K]
   99% [Working]

it has been staying there for an hour now. Any advice would be appreciated. Thanks

---

### Post by dermotti on 2006-04-25
I would have just canceled and tried again. And if it still didn;t work i would have rebooted. Theres no reason for it to take an hour

---

### Post by kh4nh on 2006-04-25
[QUOTE=dermotti]I would have just canceled and tried again. And if it still didn;t work i would have rebooted. Theres no reason for it to take an hour[/QUOTE]

i tried it before and this is the 3rd time.
If i rebooted, the base system can't boot. It complained about some device

---

### Post by dermotti on 2006-04-25
Hmmm not sure what you got going on there. I would highly reccomend going with Dapper xubuntu though...much much better.

---

### Post by kh4nh on 2006-04-25
Thanks. Apprently I got it working by removing/commenting the first line in sources.list that references the cdrom drive

---

### Post by frosa on 2007-12-30
> **kh4nh said:**
> Thanks. Apprently I got it working by removing/commenting the first line in sources.list that references the cdrom drive

Had the same problem here with Ubuntu 7.10 (installed via Live DVD). After commenting out the cdrom line in sources.list like you pointed out solve it for me too.

---

