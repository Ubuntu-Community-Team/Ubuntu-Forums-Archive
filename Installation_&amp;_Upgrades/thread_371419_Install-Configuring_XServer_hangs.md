---
title: "Install-Configuring XServer hangs"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by ububeginner05021970 on 2007-02-26
Hi,

I'm new to Ubuntu and am having issues install ubuntu 6.06 - it always seems to stall on configuring xserver.xorg.

I have tried:
1)Desktop iso install - hangs on configuring xserver.xorg
2)Alternate iso - hangs on configuring xserver.xorg
3)Server iso - hangs when I attempt to install ubuntu-desktop/xubuntu-desktop separately. Server install works fine.

Looking at the forums, I have also tried:
"sudo dpkg --configure -a" after a login.

Processor: Intel P4 1.4 Ghz
RAM: 256 MB RIMM
IDE1: Seagate 120GB
IDE2: Toshiba CD-ROM
Video: Diamond Stealth 2 4MB

I am stuck - can anyone help me out?

Thanks,
-S.

---

### Post by Kateikyoushi on 2007-02-26
Try this.

```
sudo dpkg-reconfigure xserver-xorg
```

---

