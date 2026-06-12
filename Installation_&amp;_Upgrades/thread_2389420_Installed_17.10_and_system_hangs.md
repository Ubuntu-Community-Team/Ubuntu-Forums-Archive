---
title: "Installed 17.10 and system hangs"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by alex2wr on 2018-04-16
I have the same problem in my Dell Precision M4500 running Ubuntu 17.10 when using Nouveau driver but when using NVIDIA drivers I get a black screen right after login.  And like this posts says, when using the nouveau driver, the system freezes.

I posted a question in askubuntu.com with all the details including the symptoms and the counter measures I tried.  You can find this post here: [https://askubuntu.com/questions/1025393/ubuntu-17-10-and-18-04-beta-2-display-driver-issues-freezing-black-screen-after](https://askubuntu.com/questions/1025393/ubuntu-17-10-and-18-04-beta-2-display-driver-issues-freezing-black-screen-after)

[System Configuration]
Dell Precision M4500
Intel Core i7 740QM
NVIDIA Quadro FX 1800M
(Upgrades)
Ram +16GB
SSDs
WiFi 802.11*ac*

One other thing I tried not clear in my post is that this issue happens in clean new installations as the only system, no dual boot.

I don't know what else to try so please, if know what else I can try ask ahead.

Thank you,

---

### Post by QIII on 2018-04-16
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2376106](https://ubuntuforums.org/showthread.php?t=2376106)

---

### Post by cruzer001 on 2018-04-17
Dell states that a M4500 can support up to 16G of ram, but it has four processor options.  One being the i7 Extreme Edition that would support 16G.  However the 740QM can only support 8G of ram.  Could this be the problem?

[https://ark.intel.com/products/49024/Intel-Core-i7-740QM-Processor-6M-cache-1_73-GHz](https://ark.intel.com/products/49024/Intel-Core-i7-740QM-Processor-6M-cache-1_73-GHz)

[https://www.dell.com/downloads/global/products/precn/en/precision-m4500-specsheet.pdf](https://www.dell.com/downloads/global/products/precn/en/precision-m4500-specsheet.pdf)

---

### Post by alex2wr on 2018-04-17
Interesting thought, I'll pull one stick out leaving it with 8GB and see what happens.  Interestingly enough, I'm writing you from Ubuntu 16.04.4 LTS without any issues so once I reinstall 17.10 again, ill try that.  If, that happens to be the issue, it would then be a Kernel issue problem, right?

---

