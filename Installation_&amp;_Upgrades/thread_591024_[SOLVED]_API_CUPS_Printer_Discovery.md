---
title: "[SOLVED] API CUPS Printer Discovery"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-10-25
Has anything significant happened between 6.06 and 7.04 that would cause CUPS printer discovery to change from the API level? I am trying to debug from a configuration point of view a terminal emulator's failure to discover my printers under a clean install of 7.04. It could discover these printers on 6.06. I never stayed at 6.10 when I tried the upgrade route.

I found a solution:

I changed /etc/cups/cupsd.conf

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

#Printcap /var/run/cups/printcap
Printcap /etc/printcap

My application found the printers.

---

