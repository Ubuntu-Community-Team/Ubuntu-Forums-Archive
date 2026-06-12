---
title: "Atheros AR242x (AR5414) stopped working"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wiscalico on 2009-04-04
After some time where I pushed updating Jaunty Alpha-something on my MacMini I jumped into it last night... now the wireless isn't working anymore :(

I can't find any networks and can't manually search from them:

```
je@macmini:~$ sudo iwlist wlan0 scan
wlan0 Interface doesn't support scanning : Network is down
```


I can't bring the network up:

```
je@macmini:~$ sudo ip link set up dev wlan0
RTNETLINK answers: Resource temporarily unavailable
```


lshw says that my wireless device is disabled... how do I enable it?

```
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1c:b3:b1:c1:3d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
```

---

### Post by bgerlich on 2009-04-04
try sudo ifconfig wlan0 up

---

### Post by wiscalico on 2009-04-05
> **bgerlich said:**
> try sudo ifconfig wlan0 up

As far as I know this i just another way of doing (sudo ip link set up dev wlan0). Anyway I tried it and the result is here:

```
je@macmini:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable
```

---

### Post by bgerlich on 2009-04-05
I had the same problem in early alpha, solved it by installing compat wireless. Also madwifi seemed not to be affected by the problem. It is probably some kind of chip wake up problem (check dmesg for more info), some people reported that pressing the wifi button during boot seemed to help.

I always found the ath5k to be unstable with my wireless chip(wake up, noise floor calibration, transfer rate automatic setting). Since about middle February compat wireless daily is solving most of the problems for me.

If the problem persists post dmesg output either here or on launchpad here:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299993)

---

### Post by wiscalico on 2009-04-05
Thanks mate...

I shutdown my MacMini completely and waited 5-10min before I turned it on again. Now it works as before.

I have no idea how the hell I got it disaled... not like I have a key on the keyboard for it :-S

---

### Post by binbash on 2009-04-05
I have 2 notebooks which use ar242.If your notebook has a wifi button , SOMETIMES you have to press the button to get the wireless working.

---

### Post by bennachie on 2009-04-05
> **wiscalico said:**
> Thanks mate...

I shutdown my MacMini completely and waited 5-10min before I turned it on again. Now it works as before.

I have no idea how the hell I got it disaled... not like I have a key on the keyboard for it :-S

My Mac Mini was a bit temperamental until I configured Network Manager to make the connection automatically at login. Prior to that, I sometimes had to resort to rebooting the system (although I think that, apart from giving you time to make a no doubt much-needed cup of coffee, the 5-10 min break may have been unnecessary). As you point out, there is no convenient wireless button on a Mac keyboard to make the card jump into life.

---

