---
title: "Ubuntu freezes at login - BIOS won't save Changes - Won't boot from USB"
date: 2018-01-17
forum: Installation &amp; Upgrades
---

### Post by kickokim on 2018-01-17
Hello, I've tried to install ubuntu 17.10 on a laptop but I'm ecountering some serious issues.
My laptop is an Acer Aspire E 15 START with a Intel Celeron Processor N2840 and Intel HD graphics.
Ubuntu boots but everything freezes at login (when it gets to the desktop) and there's also a second more serious issue: bios settings don't save anymore and I can't boot from USB making it impossible to install another OS on this laptop. I can't login even in recovery mode.
Can anybody help me with these issues?
Thank you!

---

### Post by kansasnoob on 2018-01-17
You've been bitten by a nasty kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

The original 17.10 images were pulled a couple of weeks ago, but that's no help to you now :(

There are work-arounds but I think they all require that the installed OS be bootable. You might try booting with the nomodeset boot parameter and see if that gets you to usable desktop.

---

### Post by kickokim on 2018-01-17
I've managed to install windows by changing the hard disk, now I have a working os, but bios is still not saving settings. Can I fix this from windows?

---

### Post by kansasnoob on 2018-01-17
I would contact Acer support. If they provide a .exe BIOS download you may be able to update/fix the BIOS from within Windows, but that is just a guess!

---

### Post by kickokim on 2018-01-17
Already tried that, but it didn't work unfortunately

---

### Post by kansasnoob on 2018-01-18
Mostly just a free bump. The only thing I'd know of is trying to get the hard drive with Ubuntu 17.10 to boot to a usable DE and then following the repair steps in that bug report.

---

