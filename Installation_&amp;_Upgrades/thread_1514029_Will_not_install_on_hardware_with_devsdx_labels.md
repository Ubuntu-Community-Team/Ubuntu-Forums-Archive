---
title: "Will not install on hardware with /dev/sdx labels"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by pebl on 2010-06-20
I downloaded both Ubuntu lite and the full CD. I tried to install both. Problem is, the automated install will not recognize any of my devices, all are labeled /dev/sdx, not /dev/hdx. I brought up both of the HD configuration programs and made a suitable environment, then went back to the automatic install. When it gets to the 4th screen, (HD setup), it just sits for ever. I can cancel out of it and try again, no good. I have no way of changing all my USB and storage from /dev/sdx to /hdx in the BIOS, and this machine is not even a year old. Supermicro Workstation server. :confused:

---

### Post by darkod on 2010-06-20
And why do you think it needs to be /dev/hdx?

Earlier /dev/hdx was used for IDE disks, and /dev/sdx for SATA. But these days even IDE disks are named /dev/sdx. That is not the issue.

If it's a server machine and you are trying to install the Desktop version, it might not recognize the controller, potentially.

---

