---
title: "Problem Starting Belkin usb Wireless N at Boot"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by igb on 2009-04-07
I have installed Jaunty Beta and applied all updates. I have a Belkin usb wireless N card, which Jaunty recognizes out of the box (well done everyone). Note this card requires ndsiwrapper in Intrepid. It works fine with Network manager.

However, I want to configure this computer to have a static ip and load wifi at boot time. I have removed Network Manager and configured /etc/network/interfaces thus:

```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
  wireless-essid manorfm
  address 192.168.0.80
  network 192.168.0.0
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1
```

When I boot, iwconfig can see the Access point but the wireless is not connected. Restarting the network with sudo /etc/init.d/networking restart makes the card connect as expected.

However, this is going to be a headless box in another building, so starting the network manually is not an option:lolflag: I can't see anything obvious in the logs.

Ian.

---

