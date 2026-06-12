---
title: "Can't upgrade to ubuntu 9.10, graphic card not supported"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Kreky on 2009-11-22
Hello
I'm a bit of a noob around this stuff, I'm trying to upgrade to 9.10 but warning comes saying my graphic card (ati radeon 9600 pro) is not supported and doesn't have drivers, so I cancel the installation...
Will those drivers come?
Should I switch to NVidia, it seems nvidia works better for linux

---

### Post by Mark Phelps on 2009-11-23
> **Kreky said:**
> Hello
I'm a bit of a noob around this stuff, I'm trying to upgrade to 9.10 but warning comes saying my graphic card (ati radeon 9600 pro) is not supported and doesn't have drivers, so I cancel the installation...
Will those drivers come?
Should I switch to NVidia, it seems nvidia works better for linux

In answer to your first question -- NO.  ATI has dropped support for your card and others and there will be no new drivers that support them.  However, there are open source drivers that will be installed by default.

Before you do the upgrade, you should remove the ATI drivers that you're using at present.  To confirm that you're using ATI drivers, open a terminal and enter "fglrxinfo".

To remove the ATI drivers and replace them with the open source drivers, see the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

In answer to your second question, maybe.  Don't know what drivers Nvidia supplies that work with the current Ubuntu versions.

---

