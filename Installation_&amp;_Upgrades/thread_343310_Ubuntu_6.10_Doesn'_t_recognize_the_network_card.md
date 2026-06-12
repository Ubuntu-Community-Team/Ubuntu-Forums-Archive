---
title: "Ubuntu 6.10 Doesn' t recognize the network card"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by juaninse on 2007-01-21
I have just installed Ubuntu 6.10, and to my dismay found that upon installation eth0 was not recognized.  The thing is: the install live CD has no trouble identifying the network component.  It' s only after install.

I'm talking about a desktop computer with a VIA motherbord with integrated ethernet card.  Am I missing something obvious?

---

### Post by wpshooter on 2007-01-21
Did you check your CD integrity by running the verification function found on the initial Ubuntu boot screen menu ?

If all else fails, try installing from the ALTERNATE CD.

---

### Post by petteriIII on 2007-01-21
I had the same problem. In the end it was only that network-address was fixed while it ought to be DHCP. Look at: System/Addministration/Networksettings: there it reads.
You can change it there too. Hope this helps

---

### Post by hopestorm on 2007-01-24
same problem..

Networks work fine under old release. After the upgrade, networks, both wired and wireless are gone....I can not even install new software, because of the losing of networking.

---

