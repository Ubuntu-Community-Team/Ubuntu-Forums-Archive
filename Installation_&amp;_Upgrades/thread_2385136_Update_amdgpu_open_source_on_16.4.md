---
title: "Update amdgpu open source on 16.4"
date: 2018-02-16
forum: Installation &amp; Upgrades
---

### Post by robehickman on 2018-02-16
Hi, I just got a rx560 gpu which is working fine with 17.10 live cd checked with unigine benchmarks. However my installed OS is 16.4 which only boots with the integrated gpu (a4-5300), it hangs on a purple screen when I boot it with the rx560. Also the 16.4 live image doesn't support the gpu and runs in low graphics mode. I assume because of this that the driver version included with  16.4 does not support the card.

Is it possible to update the driver version on 16.4? While I could update to 17.10 I don't see any point as 18.4 will be out in a few months. This computer serves multiple functions and as such it's configuration is very complex, I'd rather stick to LTS releases.

---

### Post by deadflowr on 2018-02-16
I see that the 16.04 hwe stack for X was just updated for me.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

You might see if the update brings in what you want.

The kernel was updated a while back, so it's was only a matter of time before the X stack was too.

---

### Post by robehickman on 2018-02-16
I'll see. I'm not seeing the password prompts to decrypt my drives or the usual boot splash so it isn't getting to X11.

---

### Post by robehickman on 2018-02-16
Thanks that worked.

---

