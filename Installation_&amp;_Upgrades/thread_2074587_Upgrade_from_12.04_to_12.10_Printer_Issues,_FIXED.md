---
title: "Upgrade from 12.04 to 12.10 Printer Issues, FIXED"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by bk__888 on 2012-10-21
There seems to be a printer issue when upgrading from 12.04 to 12.10.

After updating I found my printer no longer seemed to work when trying to print a pdf file.

Opening the cups page [http://127.0.0.1:631/](http://127.0.0.1:631/) , I found the error -
*"The PPD version (5.2.8-pre1) is not compatible with Gutenprint 5.2.9."*

I found the fix here -
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/932882](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/932882)

Open Terminal and enter- 
sudo cups-genppdupdate
sudo restart cups

---

