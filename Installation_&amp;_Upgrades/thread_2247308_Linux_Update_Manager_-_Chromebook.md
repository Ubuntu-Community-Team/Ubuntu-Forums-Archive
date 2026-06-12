---
title: "Linux Update Manager - Chromebook"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by harry28 on 2014-10-07
I installed Linux ubuntu 12.04 LTS on my Acer C720 chromebook a couple of weeks ago and it has been running fine with no problems. Recently, I had a pop up for the update manager, asking to install the latest version of Linux Ubuntu (14.04.1 LTS) and update some apps which are installed. This may sound like an odd question to ask but, is it as easy as just pressing update to install the latest updates or do I have to do something else to get it to install on my chromebook (last time I tried to update an app, I couldn't boot install Linux from chrome os after I install the update)?

---

### Post by grahammechanical on 2014-10-07
It should be as easy as clicking the button. The problems come if the update includes an upgrade to the kernel which in turn requires any proprietary video driver to be compiled for it. This is where I think things breakdown.

Ubuntu 14.04.1 has newer a Linux kernel and hardware modules than 14.04. It will still be kernel 3:13. So, there may not be any issues. Can you revert to an open source video driver?

You can stay where you are if you want to. The kernel in 14.04 will supported for the full 5 years of the LTS period and so will the kernel in 14.04.1 but if you move on to 14.04.2 and 14.03 and possibly 14.04.4 you will have to upgrade to 16.04 within a few weeks of it coming out to have a Linux kernel that is still supported.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

