---
title: "usb mouse and keyboard not working after video upgrade"
date: 2017-09-07
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2017-09-07
I just installed Xubuntu 16.04 on my Dell OptiplexGX 620 Dual boot system with Windows& Ultimate
Streaming videos from Amazon did not have good resolution, but evetything else seemed OK.  I queried about the problem and entered the following commands (as root):
```
apt-get update
apt-get install --reinstall xserver.org-video-intel xserver-xorg-core
```

now when the system boots up my USB mouse and keyboard are not working.  I'm getting two messages which say that there is a system error.

Help!!

notes: on Windows the video and everything else works fine.  I can boot in recovery mode, and the keyboard works fine.

---

### Post by reut2 on 2017-09-07
Well once again I just gave up and reinstalled from the live CD.  For some reason the video problem solved itself too.  I did not do a clean install--I did not format the root or home partitions.

---

