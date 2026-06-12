---
title: "Can not install"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by jgb2 on 2013-04-30
When I try to install Ubuntu on my laptop I get the following messages:

[3.573780] Kernel panic – not syncing:UFS:Unable to mount root fs on unknown-block(8,1)
 [3.573838] Pid: 1, comm:swapper not tainted 3.0.0-12-generic #28-Ubuntu
 [3.573886] Call Trace:
+ about 7 further messages:

Can you please help?

Thanks

---

### Post by dino99 on 2013-04-30
is that laptop has a bios or a uefi ?

can you boot on the live iso, from liveusb or livecd, without installing it ?
maybe you need to check the mdsum : [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
and possibly need a boot setting : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

