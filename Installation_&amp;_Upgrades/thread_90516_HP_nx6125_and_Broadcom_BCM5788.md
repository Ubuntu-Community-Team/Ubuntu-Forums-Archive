---
title: "HP nx6125 and Broadcom BCM5788"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by ddenis on 2005-11-15
Hi,

Finaly, i have made an ubuntu installation on my hp nx6125 with the help of his tutorial [http://www.kastor.org.ar/hpnx6125/](http://www.kastor.org.ar/hpnx6125/)

My network interface (rj45) does not function. it's a Broadcom NetXtreme BCM5788 10/100/1000

The interface seems to function but refuses all dhclient or all ping.

I have tried to change my kernel to 2.6.12-9-k7, but that does not change anything.

Anybody can help me ?

Use a another kernel ?

Compile a specific modules ?

Thanks

---

### Post by yesplease on 2005-11-15
I suppose you need to search for ndiswrapper howto's like [https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

You could also ask kastor, they seem to have got it working. 

Make notes and write a nice howto :)

---

### Post by ddenis on 2005-11-16
I don't think.

The module tg3 is not working (no ping, no dhcp but the interface is up and seems working).

Maybe, i can change my kernel but i have to be sure that the tg3 module will be working. I try the image 2.6.10, 2.6.11 without result.

I can also compile the bcm5700 module but i try it and i have an error about a wrong kernel-headers...

Now, i am lost and don't now what i can do ....

Denis

---

### Post by chatuser on 2005-11-23
- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Everything works now, damn ACPI !!

---

### Post by VLeshka on 2007-08-11
I have BroadCom BCM5788 too.. LAN card does not work. Ubuntu 7.04.
I have download BCM5788 driver from [www.broadcom.com](www.broadcom.com), but there are only suse and red hat versions.

I need www link Ubuntu BroadCom BCM5788 LAN Driver..

---

