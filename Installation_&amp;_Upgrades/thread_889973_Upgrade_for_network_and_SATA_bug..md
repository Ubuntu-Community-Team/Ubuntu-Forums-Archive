---
title: "Upgrade for network and SATA bug."
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Dragonatorul on 2008-08-14
I'm a very new linux and ubuntu user, just installed it this summer. That is, I tried to install it only to find out that ubuntu has two major bugs when it is installed on my brand new motherboard (Asus M3N78-EH). The SATA drives are not seen and the on board network adapter does not work. 

I don't need to use my SATA but there's not much that I can do without a internet connection. I just checked today and found that there is a fix for these problems [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162"). 

I would be eternally grateful if someone could tell me how I can install that update, maybe walk me through it. 

Thank you.

---

### Post by cariboo on 2008-08-14
If you change your Bios to ACHI the only operating system that will have any problems is windows xp as it doesn't have native drivers for sata drives. If you were to post a listing of:

```
lspci
```

We may be able to assist you in solving your network card driver problem. This is not a bug by the way, you don't expect windows to support new hardware, you always have to install drivers, so why should it be a bug in Ubuntu if it doesn't have the newest drivers for your hardware.

Jim

---

### Post by Dragonatorul on 2008-08-15
It looks to me that I just need to recompile the latest kernel. Preferably for AMD Athlon XP 64bit dual core. Could someone tell me where I can find it and how I can do that without access to the internet from inside Ubuntu? I mean downloading it on a flash stick and then transfering it into ubuntu.
I think I need a kernel newer than 2.6.24-20.

Thanks.

And the lspci command only lists about a dozen unknown nvidia devices.

---

