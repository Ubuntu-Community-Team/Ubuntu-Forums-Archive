---
title: "Ubuntu Hangs at Detect Hardware"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by nachi2 on 2014-04-07
Hi,

I am deployed a new VM and and tried to install the Ubuntu 14.04 LTS server version. Booting it from the CD. The installation stop at the stage "detecting hardware" and power off the VM. I tried version 12.04LTS as well. But still experiencing the same issue. 

Search on the forum and i updated the CD boot option to the below code. Made no difference. 

[SIZE=2] 	Code: noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off

Can someone please assist me.

[/SIZE]Thanks
Nachi

---

### Post by coldraven on 2014-04-07
Are you trying to install the 64bit version on a 32bit system?
If you are using VirtualBox you can get ready made server images from here: [http://virtualboxes.org/images/](http://virtualboxes.org/images/)
Just download and run. You only need to change the default user and password.
> **Active user account(s)** (username/password): ubuntu/reverse

---

