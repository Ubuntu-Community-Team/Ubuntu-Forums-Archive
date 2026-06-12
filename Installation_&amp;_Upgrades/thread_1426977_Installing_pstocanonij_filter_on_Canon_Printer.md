---
title: "Installing pstocanonij filter on Canon Printer"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by rhibberd on 2010-03-10
I installed the Canon IP2200 device drives for a Canon Pixma IP1700 printer using alien.  But the printer driver says it's missing the "pstocanonij filter".  How do I install it?

---

### Post by jimmers on 2010-03-11
Try Googling Canon iP1900_debian_printer.tar, worked for me, may bot work for you but worth a try, I use iP1800

---

### Post by rhibberd on 2010-03-11
> Try Googling Canon iP1900_debian_printer.tar, worked for me, may bot work for you but worth a try, I use iP1800

Thanks, but when I tried to install the cnijfilter-common, I got broken dependencies.:(  I think that something in Cups has changed to keep the driver from installing.

---

### Post by rhibberd on 2010-03-14
Update:

I was able to install IP1900 drivers by following this link:

[Follow this link.]("http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900")

The problem was with the cups changing from libcupsys to libcups.  Karmic (9.10) doesn't let you install the old libcupsys.  

For a Canon Pixma IP1700, the old scheme of installing European IP2200 drivers is out.

---

