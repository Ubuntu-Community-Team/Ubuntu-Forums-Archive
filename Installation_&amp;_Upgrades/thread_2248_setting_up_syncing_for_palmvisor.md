---
title: "setting up syncing for palm/visor"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2004-10-26
I found a web site that gives me instructions such as those below to set up the devices to sync my visor, and it all works good .... until I reboot and I loose all of this stuff... How can I make it permanent ??

TIA, 

Jim

 mknod /dev/ttyUSB0 c 188 0
            mknod /dev/ttyUSB1 c 188 1
            mknod /dev/ttyUSB2 c 188 2
            mknod /dev/ttyUSB3 c 188 3
            etc...
            chmod 666 /dev/ttyUSB*

and 

cd /dev
            ln -s /dev/ttyUSB1 pilot
            ln -s /dev/ttyUSB1 palm

---

