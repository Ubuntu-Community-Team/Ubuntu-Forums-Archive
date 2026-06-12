---
title: "Revo wired lan not working in Ubuntu 10.04"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by joewilly on 2010-07-07
Hi
using an Acer Aspire Revo with a MCP79 nvidia chip. After upgrading to 10.04 and getting a 2wire AT&T dsl modem, the revo wired lan will not work. I have a dell mini 9 and the wire lan works on it. Wireless works on both. reading the Ubuntu manual pages it seems that there is a driver problem, I need nfe driver. The explanation on how to add the driver talked about a loader.conf file. I think that was replaced in 10.04 grub2 with the /etc/grub.d/40_custom file.My question is if I add "if_nfe_load="YES" to the /etc/grub.d/40_custom file will it load the necessary driver? As you can tell I real new to this. Thank for all replies.
Joel Teel

---

### Post by joewilly on 2010-07-16
Installed Linksys USB300m USB to ethernet adapter. Works now, the ethernet plug on the acer Revo 1600 must be bad. The forcedeth driver does work for the Acer Aspire Revo 1600.
Thanks 
Joel Teel

---

