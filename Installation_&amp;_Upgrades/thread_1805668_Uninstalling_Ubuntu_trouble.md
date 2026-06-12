---
title: "Uninstalling Ubuntu trouble"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by chingyg on 2011-07-16
Hi, I installed ubuntu 10.04 for the sake of my computer programming class during the spring semester, but now I want to uninstall it because I rarely use it. 

I'm running windows 7 home premium. Here's what I've done so far. I downloaded EasyBCD 2.1 and installed the windows 7 bootloader to MBR. Then, when I try to delete the linux partitions from my disk management, I don't see it anywhere. Here's what I see instead:

(C:)
HP_TOOLS
RECOVERY (D:)
SYSTEM

I'm not really sure what to do now. Is there another way to delete the linux partitions? Thanks!

---

### Post by dino99 on 2011-07-16
depend on how it was installed: inside windoz(eg wubi) or with its own partitions.
Formatting is the way to delete partitions, be sure of which you select (and always when partition is not used)

---

### Post by chingyg on 2011-07-16
> **dino99 said:**
> depend on how it was installed: inside windoz(eg wubi) or with its own partitions.
Formatting is the way to delete partitions, be sure of which you select (and always when partition is not used)

I installed it from a usb using wubi.exe so it can boot through dualboot. I'm not sure how to format because this is a laptop and windows 7 premium came with it already installed.

---

### Post by bcbc on 2011-07-16
Go to the control panel, Add/remove programs and select Ubuntu. That will remove it completely. (You didn't have to reload the Windows bootloader in the MBR, but it doesn't hurt either)

---

