---
title: "Need to put a mem=xxxx at livecd boot"
date: 2015-12-30
forum: Installation &amp; Upgrades
---

### Post by jakfish on 2015-12-30
My specs: Ubuntu 10.04 custom livecd on usb (made with remastersys); Sony Vaio VGN-P588E

I realize that 10.04 is long retired, but my query has to do with adding a temporary boot command or actually editing the isolinux.cfg

The Vaio will black-screen unless "mem=1900MB" is added in the menu.lst (the Poulsbo driver needs some ram)

At the menu of my custom livecd, after hitting tab, I get:

initrd=/casper/initrd.gz quiet splash --

My research says put the "mem=1900MB" after the "--" and a space [Obviously, without the quotes], but the Vaio is still black-screening.

What is the proper syntax at boot, and can I edit the isolinux.cfg on the usb drive to make this permanent?

Many thanks for any help,
Jake

---

