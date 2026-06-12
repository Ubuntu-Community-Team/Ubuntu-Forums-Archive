---
title: "Ubuntu won`t Boot"
date: 2020-03-04
forum: Installation &amp; Upgrades
---

### Post by mrclover on 2020-03-04
I'm trying to install Ubuntu and it install normally, but when I reboot, a blue window pops up saying "Default boot device missing or boot failed". When I switch to Legacy mode on bios, this message does not appear, but it says "No bootable device" instead. Reinstalled ubuntu and the error persists, and I did automatic partitioning (erase disk and install ubuntu) on every try. Any solution? By the way, i'm using an Acer ES1-572 and i'm installing Ubuntu 19.10

---

### Post by oldfred on 2020-03-04
All Acer need "trust" setting on your ubuntu UEFI entry. It will not show as Ubuntu nor work until you rename it.

I think these are all similar, some may explain better.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)
Acer Travelmate B117 (success - after some UEFI boot troubles) Trust related
[https://forum.siduction.org/index.php?topic=6272.0](https://forum.siduction.org/index.php?topic=6272.0)

---

