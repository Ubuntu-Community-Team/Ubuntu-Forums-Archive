---
title: "BCM4328 networking at Ubuntu Jaunty Alpha 6"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sfeone on 2009-03-17
Hi everyone,

Tonight I installed the Ubuntu Jaunty Alpha 6. Before that I used Ubuntu Intrepid with ndiswrapper module in BCM 4328 chip.

Surprisingly Jaunty detected the wireless signal without installing ndiswrapper-things with windogs native driver after running this command:
```

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan

```

And, the result of 'lshw -C network' is given by
```

sfeone@Jaunty:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:65:88:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.11 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```

I think that module 'wl' is right thing for me. But after providing some login information such as PEAP, user name and user password, the system goes to freeze totally. I can't move even mouse cursor. Helplessly I had to press the power button to restart. But, nothing else got better than before. To do this, I referred the following website: [http://backports.ubuntuforums.com/showthread.php?t=959451&](http://backports.ubuntuforums.com/showthread.php?t=959451&).

How can I get rid of this freezing and automate this login process with wireless networking?

Thank you so much for your time in advance.
Han

---

### Post by overdrank on 2009-03-17
Moved to  Jaunty Jackalope Testing and Discussion

---

