---
title: "Ubuntu Server 18.04.1 installer fails to recognize drive size"
date: 2019-04-01
forum: Installation &amp; Upgrades
---

### Post by ryan-abmx on 2019-04-01
We have SuperMicro server with an LSI 9361-8i controller hooked up to two 12TB HGST drives in RAID1. When we try to install Ubuntu Server, the installer incorrectly reports that the RAID 1 is 87T, when we only have two 12TB drives connected. I can switch to the other tty and run fdisk, which shows the expected 10.9TB of usable space on /dev/sda. Any idea why the installer would be reading the size incorrectly? When we try to go ahead and install, it errors out...I assume because it's trying to format 87TB when it doesn't exist.

[https://imgur.com/VCNhYYg.png]("https://imgur.com/VCNhYYg")
[https://imgur.com/ksNG1Fo.png](https://imgur.com/ksNG1Fo.png)

---

