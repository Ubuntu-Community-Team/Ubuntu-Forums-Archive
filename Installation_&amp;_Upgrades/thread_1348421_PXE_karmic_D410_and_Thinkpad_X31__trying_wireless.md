---
title: "PXE karmic D410 and Thinkpad X31 : trying wireless"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by jakatak on 2009-12-07
Hi,

I have a problem trying to install Ubuntu KArmic via PXE on two laptops.

PXE is booting fine, but when vmlinuz and initrd are loaded, The busybox intsallation procedure try to have DHCP address by the wireless card, not by the Ethernet Lan card.

I disconnect the wireless card, but it did'nt work.
Any idea ?
Can i desactivate wireless DHCP detection ?

Thanks,

---

### Post by jakatak on 2009-12-08
Hi,

Carl on the installation list help me and solve my problem :
here is my pxe/default lines :

netcfg/choose_interface=eth0

In the intrd option on pxe.

---

