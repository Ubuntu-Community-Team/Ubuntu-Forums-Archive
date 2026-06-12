---
title: "Problem Ubuntu 9.10 minimal install on Asus 1005HA"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Spider1985 on 2010-01-26
Hi all,

   I have a problem when installing the Ubuntu 9.10 Minimal on mine Asus 1005HA, he cant find the Ethernet card, there are no drivers floating around...
When installing 9.10 or 9.10 remix there is no problem, but i only want command line!
Does anybody now how tackle this problem?


Kind Regards

---

### Post by gnack on 2010-01-26
That sounds odd - the minimal CD must be missing the atheros ethernet driver.  You could install 9.10 netbook remix and remove the desktop packages (easier).  Or you could install the atheros driver after the minimal install (harder).

This site has some notes doing this under Jaunty:

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by Spider1985 on 2010-01-26
> **gnack said:**
> That sounds odd - the minimal CD must be missing the atheros ethernet driver.  You could install 9.10 netbook remix and remove the desktop packages (easier).  Or you could install the atheros driver after the minimal install (harder).

This site has some notes doing this under Jaunty:

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

Tnx for your awnser!
There is no way to install the "Minimal" ubuntu without the driver right? or is there a way to add the theros ethernet driver?
Or is it possible to strip down the normal ubuntu 9.10 or remix to a "minimal" (only command based) install?


Kind Regards

---

### Post by snowpine on 2010-01-26
You can install a minimal CLI-only system using the Alternate CD, without an internet connection.

---

### Post by Spider1985 on 2010-01-26
> **snowpine said:**
> You can install a minimal CLI-only system using the Alternate CD, without an internet connection.

Thanks! iam going to take a look at it :KS

---

### Post by Spider1985 on 2010-01-27
Does anybody know the commands to make a 9.10 ubuntu install or 9.10 UNR totaly GUI free? So to strip down a install to 9.10?


Kind Regards

---

