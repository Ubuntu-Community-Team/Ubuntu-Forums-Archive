---
title: "need to correct BIOS/UFEI problems (?)"
date: 2018-06-01
forum: Installation &amp; Upgrades
---

### Post by Rixter69 on 2018-06-01
Evening:

   Have been trying to get any distro(Linux-Ubuntu) to operate in the manner it should when running from pendrive! Here's what's going on; when I use Pendrivelinux, Unetbootin or LiLi to configure .iso to pendrive, all the distros I've tried (6 different flavors) encounter severe lagging/freezing problems. But when I use Rufus, all is great. The problem with Rufus: it does not support "persistence". Question: what does Rufus do different? AND/_OR_...how can I employ Rufus and get persistence? [Dell Optiplex 7020/9020 - Lexar 16GB 3.0 pendrive] Should you want documentation of all I've done, please request and be prepared for it will be a lengthy essay.

:confused:[SIZE=4][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by ubfan1 on 2018-06-01
The performance may simply be having the "toram" on the kernel boot line, to get the filesystem off the USB and into ram, at the "cost" of a 30 second copy command at boot time.  Other tools like mkusb offer that option as well as persistence.

---

