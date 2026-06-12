---
title: "After Upgrade to 9.10 - Problem with XSANE+LIDE25"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by fellow138 on 2009-12-16
Hallo,
My Installation:
Ubuntu 9.10, X86, 32Bit, 3GB-Main-Storage
2 Screens with NVIDIA under driver 185.18.36
Linux Kernel 2.6.31-16-generic
gnome 2.28.1.

After new installation from scratch by downloaded and burned ISO-File I installed XSANE 0.996. No Error occured during installation.
But:
After the installation and calling XSANE from desktop or from Menu, the opening-window of XSANE appears for half a second and disappears without any error-message.

The debug.log contains the followns records:
                                 _**debug.log**_
 Dec 14 14:56:34 PC_NAME saned[2093]: saned (AF-indep+IPv6) from sane-backends 1.0.20 starting up
 

 Dec 14 14:56:34 PC_NAME saned[2093]: check_host: getpeername failed: Socket operation on non-socket
 

 Dec 14 14:56:34 PC_NAME saned[2093]: init: access by host [error] denied
 

 Dec 14 14:56:34 PC_NAME saned[2093]: saned exiting
 

 Dec 14 14:56:53 PC_NAME saned[2106]: saned (AF-indep+IPv6) from sane-backends 1.0.20 starting up
 

 Dec 14 14:56:53 PC_NAME saned[2106]: check_host: getpeername failed: Socket operation on non-socket
 

 Dec 14 14:56:53 PC_NAME saned[2106]: init: access by host [error] denied
 

 Dec 14 14:56:53 PC_NAME saned[2106]: saned exiting
 

 Has anyone any idea about this problem?


best regards


Dieter


PS: The Scanner worked perfectly under the previous ubuntus 8.xx, 9.xx and is working without problems under windows xp,vista too.

---

