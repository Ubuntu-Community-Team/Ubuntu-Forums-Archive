---
title: "Gave up waiting for root device. after upgrade to 12.04 from 11.10 on Hyper-V host"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by __m128 on 2012-05-08
I have just upgraded a VM running Ubuntu 11.10 to 12.04 running under a Microsoft Hyper-V hypervisor; now it fails to boot using the 3.2.0 kernel but it works with the 3.0 kernel. I have described the issue also here: [http://serverfault.com/questions/387041/gave-up-waiting-for-root-device-after-update-to-12-04-in-hyper-v](http://serverfault.com/questions/387041/gave-up-waiting-for-root-device-after-update-to-12-04-in-hyper-v)

Basically, the machine is running seemingly fine now using the 3.0 kernel; I can log into it with SSH and take a look at everything, and there is nothing glaringly wrong. However, on reboot, it plainly refuses to work. The hyper-v hasn't changed, only the Ubuntu version. Previously, I have manually enabled hyper-v integration as described here: [http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx) and verified that everything is loading correctly. My gut feeling is that the new hyper-v drivers somehow assign a different ID to the root device now and hence LVM chokes, but how can I verify this?

---

### Post by __m128 on 2012-05-09
I exported the hyper-v VM and tried to boot it in VirtualBox, and that works. So it must be some Hyper-V related problem. The host has 2003 Hyper-V; is this supported by the Hyper-V kernel drivers?

---

