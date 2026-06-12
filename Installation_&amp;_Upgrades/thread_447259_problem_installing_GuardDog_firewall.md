---
title: "problem installing GuardDog firewall"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by pacsum on 2007-05-17
when the sys finishes downloading the firewall, it gives me this error:

[I]"The following NEW packages will be installed:
  guarddog
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 488kB of archives.
After unpacking 1458kB of additional disk space will be used.
Get:1 [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) feisty/universe guarddog 2.5.0-1ubuntu1 [488kB]
Fetched 488kB in 18s (26.9kB/s)                                                
Selecting previously deselected package guarddog.
(Reading database ... 99598 files and directories currently installed.)
Unpacking guarddog (from .../guarddog_2.5.0-1ubuntu1_i386.deb) ...
Setting up guarddog (2.5.0-1ubuntu1) ...
Unable to start guarddog firewall - /etc/rc.firewall does not exist"[/I]

any suggestions??

---

### Post by jbro on 2007-05-18
This apparently happens because the install is checking if the /etc/rc.firewall file exists. If you have not previously used guarddog, this file will most likely not be there. That's OK. Go ahead and try to start guarddog and you will get a brief explanation about the "missing rc.firewall" message. When you are done configuring your firewall, guarddog will create the appropriate rc.firewall script for you.

Regards,
jbro

---

