---
title: "Hard drive recognition"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by suddentwigs on 2011-07-26
Hi there. I have been running ubuntu studio 10.04 lucid lynx since its release, with one internal Samsung hard drive and one external Seagate USB 2.0 drive. I recently added a Western Digital USB 3.0 external hard drive. It works fine when it is the only one connected, but when I reconnect my existing hard drive, it only detects both of them until the computer is reset. When I switch it back on, only the Seagate USB 2.0 hard drive is accessible, the WD 3.0 is not mentioned anywhere, even on the disk utility accessory. What can I do to make them both permanently accessible? Thanks.

---

### Post by dino99 on 2011-07-26
Some (all?) USB3.0 controllers aren't bootable

better to install the latest intel driver from xorg-edgers ppa

[http://askubuntu.com/questions/12139/does-ubuntu-support-usb-3-0](http://askubuntu.com/questions/12139/does-ubuntu-support-usb-3-0)

and glance at your bios settings; is it updated ?

---

