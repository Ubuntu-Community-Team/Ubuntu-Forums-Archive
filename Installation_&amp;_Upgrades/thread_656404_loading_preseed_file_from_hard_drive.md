---
title: "loading preseed file from hard drive"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by skmah on 2008-01-02
I'm able to load our preseed file from a web server url, however we want to be able to load the preseed file from the 1st hard disk.

According to this page:
[https://help.ubuntu.com/7.04/installation-guide/hppa/preseed-using.html#preseed-loading](https://help.ubuntu.com/7.04/installation-guide/hppa/preseed-using.html#preseed-loading)
You can only load the preseed file from CDrom, url, usb-media, or embedded in the initrd.

I have tried:
preseed/file=/hd-media/preseed.cfg
that doesn't seem to work, also tried file=/preseed,cfg and /dev/sda1/preseed.cfg

---

