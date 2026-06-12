---
title: "after upgrade to 10.10, ubuntu very slow"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by RegisG on 2011-10-26
Hello,

Here is what I've noticed :

* xorg seems trying to load fglrx even if the driver is not installed. I don't really know what driver it uses because there isn't any xorg.conf file.  The /var/log/X.0.log file seems to load RADEON(0)...  The graphic card is RADEON 9100 IGP ; what is the better driver for this chipset ? 

* impossibility to make a sudo -s in any terminal  ( gnome-terminal or xterm ) : the login hangs and the password is never requested.

Thanks for your help !

---

