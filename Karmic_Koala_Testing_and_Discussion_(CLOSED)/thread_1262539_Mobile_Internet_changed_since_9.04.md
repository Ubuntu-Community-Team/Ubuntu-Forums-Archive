---
title: "Mobile Internet: changed since 9.04?"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2009-09-10
Hello All

Orange broadband is not working (again), so I popped my Web'n'Walk modem (e220) into my Karmic test box. Nothing.

Tried Network Connections in Admin/Prefs. Clicked the mobile internet tab, chose country and operator, challenged by dialog asking for keychain password (I've not set one), no connection.

9.04 'just worked' when you plugged the mobile modem in, and worked well on same hardware. Is there a change in the way you are supposed to start a mobile internet session, or is this a (serious for me) bug?

---

### Post by NoBugs! on 2009-09-10
Yes, the network system is completely different, currently it's using a NetworkManager 0.8 nightly release according to [here]("http://packages.ubuntu.com/search?suite=karmic&searchon=names&keywords=network-manager").

For better stability, you might want to try to install the old Networkmanager packages from jaunty:
[http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=network-manager](http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=network-manager)

---

### Post by GeorgeVita on 2009-09-10
... or better try the latest versions and 'report' any bug as we all need a better 9.10 (than 9.04) especially on mobile broadband h/w recognition.

By the way: what type of modem (manufacturer/model) did you get with Orange?

Regards,
George

---

### Post by pedrogfrancisco on 2009-09-10
For some reason on Kubuntu, using wvdial, with an Huawei E220, I sometimes get no DNS.

That rules out NetworkManager, probably.

If you fill a bug report I may read exactly what's happening and if it's the same as me, I'll mark the "Also affects me" thingie.

---

### Post by autark on 2009-09-11
> **NoBugs! said:**
> Yes, the network system is completely different, currently it's using a NetworkManager 0.8 nightly release... 
Not only that, HAL is being replaced by other components, which might have an effect on how pluggable devices are detected and handled.

---

### Post by keithpeter on 2009-09-11
> **pedrogfrancisco said:**
> For some reason on Kubuntu, using wvdial, with an Huawei E220, I sometimes get no DNS.

Hello All

Mine's a Huawei e220 as well.

I'll try again tomorrow, monitor logs, dmesg &c and file a bug. Mobile Web was really ace in 9.04 on Asus web books and it would be idiotic to walk away from that.

---

### Post by tekstr1der on 2009-09-11
FWIW, there have been several bugs with network-manager .8 and mobile broadband devices. Though most of the issues I've reported have been resolved, I still need to do the following after plugging in my Verizon UM150 USB device:

```
sudo killall modem-manager
```

After this, the device is listed and I am able to connect.

I still have this bug open here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913)

---

