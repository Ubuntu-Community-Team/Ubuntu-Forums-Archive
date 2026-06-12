---
title: "Unable to Install Ubuntu 18.04 on Dell PowerEdge R6525"
date: 2021-04-12
forum: Installation &amp; Upgrades
---

### Post by crazyarjun on 2021-04-12
Hello Everyone, 

I am unable to install Ubuntu 18.04 on the Dell Server R6525. If I use the Server Edition the Installation will be stuck at detecting the Disks and will the error as below. Because of this OS installation did not proceed further.

> Block probing did not discover any disks big enough to support guided storage configuration.

If I use the Desktop Version Ubuntu 18.04 OS will be installed without any issues. However on the first boot itself I will get a Grub error. 

> error: attempt to read or write outside of disk 'hd0'. 
Entering rescue mode... 
grub rescue>


Tried fixing the grub issue with the [Ubuntu Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") and the outcome of it is successful but server won't boot into the OS not even for once and the grub issue is repeated.

Outcome of the Grub Issue: [Link]("http://paste.ubuntu.com/p/7VS4VrYJ7d/")

However if I use the Ubuntu 20.04 LTS, OS installation is successful and I am able to login to the system without any issues.

Ubuntu Support: [Link]("https://certification.ubuntu.com/hardware/201910-27388")

The Server having the Dell PERC H755 Card.


Anyone can advise me how to install the OS in this server?

---

