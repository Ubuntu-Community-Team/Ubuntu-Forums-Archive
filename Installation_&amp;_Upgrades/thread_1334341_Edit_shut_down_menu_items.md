---
title: "Edit shut down menu items"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by ubuntopoly on 2009-11-22
Does anyone know where to find the configuration scripts for the shutdown menu on 9.10? I would like change the hibernate function that can be invoked from the System Shutdown->Hibernate button.

Under ubuntu 9.04, I had to edit the file   
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
and replace the hibernate tool, i.e. use s2disk. No longer works under 9.10.


I can do sudo /usr/sbin/s2disk from command line but that is a bit tedious and insecure.

Thanks Fritz

---

