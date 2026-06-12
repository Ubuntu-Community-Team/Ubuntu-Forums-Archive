---
title: "why wont this driver load??"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by cjmiller00 on 2010-06-17
Im using the drivers from netgear cd and they are installed into ndisgtk.  
log showing activity that

Jun 17 15:06:15 cablehanger kernel: [13644.100143] usb 1-4: USB disconnect, address 7
Jun 17 15:06:18 cablehanger kernel: [13647.592057] usb 1-4: new high speed USB device using ehci_hcd and address 8
Jun 17 15:06:18 cablehanger kernel: [13647.772486] usb 1-4: configuration #1 chosen from 1 choice
Jun 17 15:06:18 cablehanger kernel: [13647.904065] usb 1-4: reset high speed USB device using ehci_hcd and address 8
Jun 17 15:06:19 cablehanger loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver arusb_xp

how do i get the driver to load.

---

### Post by ddrichardson on 2010-06-17
Can you post any output from:
```
sudo cat /var/log/syslog | grep loadndis
```

---

### Post by ddrichardson on 2010-06-17
I take it that Ubuntu didn't support it - that you didn't got straight to ndiswrapper?

---

### Post by cjmiller00 on 2010-06-18
> **ddrichardson said:**
> Can you post any output from:
```
sudo cat /var/log/syslog | grep loadndis
```

 Jun 18 10:39:32 cablehanger kernel: [ 5569.002754] ndiswrapper  (load_wrap_driver:108): couldn't load  driver arusb_xp; check system log for messages from 'loadndisdriver'

LOG STATES the following. 
un 18 10:39:32 cablehanger kernel: [ 5568.512135] usb 1-4: new high  speed USB device using ehci_hcd and address 5
Jun 18 10:39:32 cablehanger kernel: [ 5568.692873] usb 1-4:  configuration #1 chosen from 1 choice
Jun 18 10:39:32 cablehanger kernel: [ 5568.824075] usb 1-4: reset high  speed USB device using ehci_hcd and address 5
Jun 18 10:39:32 cablehanger loadndisdriver: loadndisdriver:  load_driver(35: couldn't load  driver arusb_xp

i also found this interesting....

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it  will be ignored in a future release.
arusb_xp : driver installed
    device (0846:9001) present (alternate driver: ar9170usb)
so im assuming i need to get rid of that default driver.  or should it  stay. since im trying to get the other in there i should remove it but I  dont want to hurt anything.

---

### Post by ddrichardson on 2010-06-18
The general consensus of opinion is that the ndis wrapper will not work for this chipset, although some cards have had some success.

Debian has a wiki page for it here [http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb) but I haven't got time to go through it for Ubuntu tonight, can you postthe output of:
```
sudo lsusb|grep 0846
```

---

### Post by cjmiller00 on 2010-06-18
> **ddrichardson said:**
> The general consensus of opinion is that the ndis wrapper will not work for this chipset, although some cards have had some success.

Debian has a wiki page for it here [http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb) but I haven't got time to go through it for Ubuntu tonight, can you postthe output of:
```
sudo lsusb|grep 0846
```


Bus 001 Device 003: ID 0846:9001 NetGear, Inc. WN111 v2 802.11n

the ar9170usb is installed  per ndiswrapper -l

device (0846:9001) present (alternate driver: ar9170usb)
i suppose the real question here is how to switch that alt driver to the other proper device driver.  Even more importantly is how will future aps look at either driver.  which is better to use as far as drivers are concerned. 

at the moment under the wireless conn manager i have two to choose from . wlan0 and wlan2.  the radio button on the exterior still controlls both wlan 0 (onboard broadcom ) and wlan2 (netgear wn111v2 generic driver).  

* now how to disassociate with radio on /off button. hmmmm.

---

### Post by ddrichardson on 2010-06-18
If a native driver is available, I would use it over NDIS. The message is telling you that you don't need ndiswrapper because there is a native driver present. A Windows NDIS driver isn't necessarily the better option. I know it's present on 10.04, I just checked but there is a possibility the firmware is not present in previous releases. If you aren't using 10.04 can you:
```
ls /lib/firmware/ar9170.fw
```

Your post is a little confusing, network manager isn't loading drivers - modules are inserted into the kernel.

---

### Post by ddrichardson on 2010-06-18
Incidentally, the driver you're attempting to load in ndiswrapper - it is an XP driver and not Vista/Win7?

---

### Post by cjmiller00 on 2010-06-19
> **ddrichardson said:**
> If a native driver is available, I would use it over NDIS. The message is telling you that you don't need ndiswrapper because there is a native driver present. A Windows NDIS driver isn't necessarily the better option. I know it's present on 10.04, I just checked but there is a possibility the firmware is not present in previous releases. If you aren't using 10.04 can you:
```
ls /lib/firmware/ar9170.fw
```Your post is a little confusing, network manager isn't loading drivers - modules are inserted into the kernel.


yes im with 10.04

i removed ndiswrapper and im back down to my onboard card.  no netgear. no wlan2 only wlan0 broadcom

what about removing broadcom driver and only having netgear.  how could i do that. or how could i get the netgear driver into the hardware drivers.

---

### Post by cjmiller00 on 2010-06-23
I reimaged my box and blammo!!!! works off start.  but...

this connection looses strenght and resets.  ill trouble shoot and determine either
1. usb
2. router
3. software. 

if # 3 then ill be back

---

