---
title: "Ubuntu On A Network Storage High-Speed USB Device"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by XombieShovel on 2007-12-07
I want to install Linux, but I need to keep Vista because I am a heavy gamer. I don't have enough HDD space for a dual boot, so I thought I might install Ubuntu on an external 500gb Free Agent hardrive. I also use that harddrive for network storage. I have used Linux before. So i had a couple questions.

Currently my Computer is plugged via Ethernet into a D-Link gigabit router, which is then plugged via ethernet into a Belkin Network USB Hub, which via USB is plugged into the network storage.

Router: [http://www.circuitcity.com/ccd/productDetail.do?oid=165020&WT.mc_n=4&WT.mc_t=U&cm_ven=COMPARISON%20SHOPPING&cm_cat=GOOGLE&cm_pla=DATAFEED-%3EPRODUCTS&cm_ite=1%20PRODUCT&cm_keycode=4]("http://www.circuitcity.com/ccd/productDetail.do?oid=165020&WT.mc_n=4&WT.mc_t=U&cm_ven=COMPARISON%20SHOPPING&cm_cat=GOOGLE&cm_pla=DATAFEED-%3EPRODUCTS&cm_ite=1%20PRODUCT&cm_keycode=4")

Network USB Hub: [http://www.belkin.com/networkusbhub/]("http://www.belkin.com/networkusbhub/")

External Hard Drive (mines 500gb): [http://www.amazon.com/Seagate-FreeAgent-Desktop-External-ST302504FDA1E1-RK/dp/B000NDBRJC]("http://www.amazon.com/Seagate-FreeAgent-Desktop-External-ST302504FDA1E1-RK/dp/B000NDBRJC")

Motherboard: [http://www.asus.com/products.aspx?l1=3&l2=101&l3=301&model=1160&modelmenu=1]("http://www.asus.com/products.aspx?l1=3&l2=101&l3=301&model=1160&modelmenu=1")

A couple questions:

1. Is this possible?

2. Can other computers in the network boot Linux from this also?

3. Can they do it at the same time?

4. Can it use programs on my computer?

---

### Post by JKyleOKC on 2007-12-07
I doubt that what you want to do is even possible, since your machine could not access the network or external drive until after booting Vista.

However have you considered installing VMWare Server on the external drive, creating a virtual machine there, and installing Ubuntu on said virtual machine? That should work nicely, and could be configured to access files on your Windows machine if Vista will allow such access.

Performance should not be degraded much, either. I'm doing essentially the reverse of this, booting into Xubuntu and there running virtual machines with Win2K and WinXP Pro, which let me support my Windows-using clients comfortably.

Google for "VMWare Server" to find the free version (I don't know whether it's Vista-compatible yet but it never hurts to try). You have to get a license for it to complete the installation, but it's automatic via the web...

Any machine on your network should be able to connect to the virtual machine once it's installed, but I don't think more than one at a time could have access. Otherwise conflicting write operations could and would wreak havoc.

---

