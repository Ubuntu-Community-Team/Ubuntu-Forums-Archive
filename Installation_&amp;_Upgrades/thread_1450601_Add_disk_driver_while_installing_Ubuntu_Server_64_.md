---
title: "Add disk driver while installing Ubuntu Server 64 bits"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by LucRol on 2010-04-09
Hello
 
I would test Ubuntu 10.04 LTS on an Lenovo server TD200x with the integrated Raid-10 (LSI chipset).
Standard installation don't recognize the disk.
Lenovo give a 64 bits driver only for Red Hat and Suse.
- Can I use the Red Hat driver with Ubuntu ?
- How install the driver (if compatible) during the installation process ?
I've a file r8sas01sr47.tgz containing files kmode-mptbase-4.16.80.01-1-rhel5.2....
Best regards.
 
Luc

---

### Post by wojox on 2010-04-09
There's an app called [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto") that will convert rpm's to deb's

---

### Post by LucRol on 2010-04-09
Great !
I've converted the RPM driver to a DEBIAN one, but when I try the installation, how can I update the system with the new driver, the installation process actually desn't recognize my disks !...

---

