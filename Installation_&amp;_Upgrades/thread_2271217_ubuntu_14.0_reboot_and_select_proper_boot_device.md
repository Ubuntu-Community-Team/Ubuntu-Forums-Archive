---
title: "ubuntu 14.0 reboot and select proper boot device"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by Jason_Wei on 2015-03-28
Hi everyone,

After trying to upgrade to Ubuntu 14, I'm unable to restart my computer. It takes me to error "Reboot and select proper boot device".

After googling around, it seems that others have encountered similar problems. The steps I took to try and fix this were:

1) created a bootable USB with Ubuntu 14 from my mac
2) started the computer with the bootable USB and hit "Try Ubuntu"
3) connected to internet and installed boot-repair
4) ran boot-repair with following paste

[http://paste.ubuntu.com/10695782/](http://paste.ubuntu.com/10695782/)

The boot-repair said it was "successful" and told me to try and reboot my computer. Unfortunately I'm running into the same problem.

At this point I'm out of ideas, and hoping that someone here can better interpret what the paste says and help me out. Thanks ahead of time!

---

### Post by Jason_Wei on 2015-03-28
Strange... trying to debug this myself... it seems as if Ubuntu doesn't recognize any of my hard drives? /dev/sda seems to be the USB stick that I'm booting off of.

I have both a HDD and a SSD installed which BIOS seems to recognize.

---

