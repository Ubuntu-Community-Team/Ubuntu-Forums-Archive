---
title: "Install on RAID 1"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by nry on 2011-02-03
I attempted an install on a 120GB single HDD to begin with to make sure everything worked correctly, and it did. Perfect

Next was onto a RAID 1 (hardware) installation using two 320GB HDD

Now ubuntu detects this and I can install it without an issues at all.

Followed the exact process that I did when following the install for the single HDD (bar one option which mentioned SATA RAID devices)

Now once installation is completed, and I attempt to boot I just hang on the following screen:

[IMG]http://img209.imageshack.us/img209/9900/70612272.jpg[/IMG]

Whats causing this?

---

### Post by realzippy on 2011-02-03
Did the installer see both discs?sda and sdb ?

---

### Post by nry on 2011-02-03
It sees it as one mirrored disk.

Not too sure about the sda and sdb, can run though the process again if needed and double check?

---

### Post by realzippy on 2011-02-03
Just wanted to be sure if it is a real hardware raid.
Which controller?

---

### Post by nry on 2011-02-03
Its a kontron 986lcd-m/mitx board

[http://emea.kontron.com/products/boards+and+mezzanines/embedded+motherboards/miniitx+motherboards/986lcdmmitx.html](http://emea.kontron.com/products/boards+and+mezzanines/embedded+motherboards/miniitx+motherboards/986lcdmmitx.html)

With the following chipset: Intel® 945GM + Intel® ICH7R Chipset

---

### Post by realzippy on 2011-02-03
looks more like a fakeraid?
[https://wiki.ubuntu.com/DmraidSupport](https://wiki.ubuntu.com/DmraidSupport)

---

