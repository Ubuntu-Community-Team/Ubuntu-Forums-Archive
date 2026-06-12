---
title: "Upgrading 17.04 results in loss of internal keyboard and trackpad"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by jambonrose on 2017-05-03
Hi,
I'm working with Ubuntu for the first time at work. I've installed Ubuntu 17.04 on an HP Zbook 15 G3, and after a few changes (adding DNS nameservers in /etc/resolv.conf and turning off Hybrid Graphics and Secure boot in the UEFI), everything was working great.

I used the software update application to download a new kernel and other updates that I must admit I ignored. Once the computer restarted, the laptop's keyboard and trackpad ceased working. Plugging in an external USB mouse and keyboard works fine. I note that the internal keyboard and trackpad still work in grub, but  that booting into recovery mode in either kernel (4.10.0.19 and 4.10.0.20) does not change a thing - the keyboard ceases to work in the recovery mode menu.

Re-installing 17.04 from the USB drive resolved the issue. I then naively upgraded the system again, and the keyboard ceased working again.

I would love some help fixing this, as I am totally unsure how to proceed.

Thank you,

Andrew

---

### Post by Xian on 2017-05-04
If the previous kernel didn't fix the issue ... check in the Software Center for recent updates.

See if an upgraded package was applied that might impact your input devices.



[IMG]https://i.stack.imgur.com/i1Sop.png[/IMG]

---

### Post by Samppa_Linna on 2017-08-10
I have an HP ZBook 15 G3 as well but I've been using Xubuntu 16.04. Last week, I updated all the packages and since then I've suffered from the very same issue. *xinput list* doesn't show the laptop's keyboard and trackpad.

---

### Post by Samppa_Linna on 2017-08-10
So, it turns out *pnpacpi=off* was the culprit. Now it's back to fighting with network and suspend problems, it seems, since this boot setting improved things in those areas quite a bit.

---

