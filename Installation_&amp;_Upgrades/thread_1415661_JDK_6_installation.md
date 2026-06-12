---
title: "JDK 6 installation"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by rosy Jovita on 2010-02-25
Hi everyone,

I am currently new to ubuntu. I would like to install jdk 6 in ubuntu. I've tried to install using this command: sudo apt-get instal ...
But in the end,i only got this result:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Someone please hellp,i've tried many times and still it doesn't works.

---

### Post by byStanderone on 2010-02-25
... sudo apt-get autoclean (before anything else)

---

### Post by byStanderone on 2010-02-25
...if the problem persist..then, sudo dpkg --configure -a

---

### Post by oldos2er on 2010-02-25
> **rosy Jovita said:**
> I am currently new to ubuntu. I would like to install jdk 6 in ubuntu. I've tried to install using this command: sudo apt-get instal ...
But in the end,i only got this result:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


If you have another package manager open, e.g. Synaptic, Ubuntu Software Center, or Update Manager, close them, then retry the command.

---

### Post by rosy Jovita on 2010-03-01
Thanks a lot, it works. :)

---

