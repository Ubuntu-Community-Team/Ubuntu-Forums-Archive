---
title: "Need more space on /boot partition for upgrade to Gutsy"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2008-01-21
Dear Ubuntufolk:

I have been trying to upgrade Feisty to Gutsy via the Internet.  Live Disk doesn't work because of a video card incompatibility.  I get a message saying that I don't have enough space on the /boot partition.  I cleaned everything up with sudo apt-get clean, no improvement.  I would rather not get involved in resizing the partition since I have a dual boot and I am afraid that the pointers are going to get all mixed up, preventing me from booting at all.  How can I get rid of a kernel or something from GRUB?  I just updated Feisty prior to the Gutsy upgrade, so I am sure that there is something I can get rid of.  I need 11+ MB more space on /boot.

Thanks.

Whatawonderfulday

---

### Post by tophcito on 2008-01-21
Hello!

I think u can use the StartUp-Manager tool for that purpose. 

Just go to System -> Administration -> StartUp-Manager. In the window that comes up, go the the Advanced tab. The first checkbox allows you to enable limitation of kernels. Check it and set the number to something reasonable.

I think this should throw out all your old kernels, and make some more room under /boot.

Another solution might be to directly delete the kernel images via a terminal that are located at /boot. But I would rather not recommend to do that, since that has the potential to make your system unbootable.

good luck.

---

### Post by zvacet on 2008-01-21
Go to the synaptic and in search box type linux-image.Remove them all exept one with higher number.That should give you enough space.

---

### Post by Whatawonderfulday on 2008-01-24
I took the Zvacet option and removed a couple of old kernels and I had enough space to install.

Thanks.

Whatawonderulday

---

### Post by InuIzzy on 2008-02-22
Zvacet's Solution also worked for me.

---

