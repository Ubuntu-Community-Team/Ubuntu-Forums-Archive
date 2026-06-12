---
title: "Difficult Install (no gui)"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by topher4015 on 2006-08-30
Well I have this old nec pc, 433 mghz celeron and 96 mb of ram with no floppy or cd drives.  To install ubuntu on it I plugged the hd into a newer comp that boots from a disk and installed it to that hd but when I plug it back into the old comp, it says there is an error with x server which I am taking to be the gui.  I am alittle new to linux so take it easy on me.:rolleyes: Any help on why the gui won't come up is appreciated.

---

### Post by funchords on 2006-08-30
A couple of issues:

256 MB of RAM is recommended for Ubuntu.  You can get a way with less, but probably not that much less ...
[http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

When you install an operating system, it is going to set itself up for the hardware that is present at the install.  You can try this command, which should cause that configuration step to occur again:

sudo dpkg-reconfigure xserver-xorg

---

