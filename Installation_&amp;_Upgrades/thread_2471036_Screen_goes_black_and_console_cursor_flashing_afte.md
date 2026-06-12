---
title: "Screen goes black and console cursor flashing after shutdown/restart"
date: 2022-01-20
forum: Installation &amp; Upgrades
---

### Post by shinoq on 2022-01-20
Hi,
after update kernel from 5.11 to Linux 5.13.0-27-generic on Ubuntu 20.04.3 LTS system is stuck after shutdown on black screen with console cursor flashing in left right corner. I have tried grub or deamon fix. Tried to wait but it never shuts down. Also left grub line GRUB_CMDLINE_LINUX_DEFAULT="" to see logs as they process but not working on shutdown/restart, keeps freezing. Only pressing power button for 5 seconds works.

Here are my logs from journalctl -rb -1 command:

[https://paste.ubuntu.com/p/VgdFxJXYcY/](https://paste.ubuntu.com/p/VgdFxJXYcY/)

really want to avoid reinstall, can I damage hardware by powering down with button each time? I am fairly new to ubuntu and linux overall.

---

### Post by kc1di on 2022-01-20
What Graphics card or chipset is in that machine?

---

### Post by KBar on 2022-01-20
> **shinoq said:**
> Hi,
after update kernel from 5.11 to Linux 5.13.0-27-generic on Ubuntu 20.04.3 LTS system is stuck after shutdown on black screen with console cursor flashing in left right corner. I have tried grub or deamon fix. Tried to wait but it never shuts down. Also left grub line GRUB_CMDLINE_LINUX_DEFAULT="" to see logs as they process but not working on shutdown/restart, keeps freezing. Only pressing power button for 5 seconds works.

How long does it stay in that state for? Until this gets fixed, select 5.11 from the GRUB menu and keep using the older version. To ensure it's fixed and fixed quickly, file a bug report with```
ubuntu-bug linux
```and follow the instructions.
> really want to avoid reinstall, can I damage hardware by powering down with button each time? I am fairly new to ubuntu and linux overall.
That depends on the type of hardware. 

Nobody can say much without more information.

---

### Post by shinoq on 2022-01-20
AMD Ryzen 5 4500U with Radeon Graphics Renoir
chipset: Advanced Micro Devices, Inc. [AMD]    FCH LPC Bridge
MB: ASUSTeK COMPUTER INC.  PN50

---

### Post by shinoq on 2022-01-20
> **KBar said:**
> How long does it stay in that state for? Until this gets fixed, select 5.11 from the GRUB menu and keep using the older version.


It is permanently stuck. 

I managed to install other kernels and boot on kernel 5.11 but it's not booting up properly, only one monitor works and no networking at all. It happens same up to kernel Linux 5.13.0-23-generic, once I boot from Linux 5.13.0-25-generic it's all good, just no reboot nor shutdown. Do I really need to reinstall :/

also got new two entries after getting target reboot while on 5.13.0-25:
[IMG]https://www.linuxquestions.org/questions/attachment.php?attachmentid=38169&d=1642720575[/IMG]

---

