---
title: "virtual box removes the wirless connection"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by shamalawy on 2008-04-28
hi everyone, i have a serious issue here, when i install virtual box and try to run it on hardy, it tell me that there's a certain file missing so i go to the synaptic installer and install everything related to virtual box. after that, ubuntu tell me that it has to restart. after the restart the wirless connection simply disappears.. i don;t know if it;s a bug from the program or from ubuntu since that i'm a normal user. please i need to install virtual box because of some special programs that use at work.

one last thing.. automatix project is halted and i used to install vmware through it.. can anyone tell me how to install vmware instead of virtual box.

UBUNTU 4 EVAAAA

---

### Post by pytheas22 on 2008-04-28
First, if you're using the Virtual Box .deb from the repositories, I would try uninstalling that and instead using the package from Virtual Box's website, [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI) .  The version in the repositories has some issues in my experience, the one directly from Virtual Box just works.  This might solve your problem.


> one last thing.. automatix project is halted and i used to install vmware through it.. can anyone tell me how to install vmware instead of virtual box.

There are instructions at [http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html) for 7.10 but they'll probably work for 8.04 almost as well.

---

