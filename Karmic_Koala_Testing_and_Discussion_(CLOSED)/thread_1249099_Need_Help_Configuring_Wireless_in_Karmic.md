---
title: "Need Help Configuring Wireless in Karmic"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brandoncolorado on 2009-08-24
Hi,

For a number of reasons, I want to be running Karmic on my HP Mini 1030nr netbook.  When I try the LiveUSB, the wireless can be enabled via the restricted driver window.  However, with alpha 2 I could not enable the wireless.  

Could someone help me determine:
1)  Which wireless card I have (I know it is broadcom).
2)  Whether I will be able to enable the card in Alpha 4 installed.

Thanks!

---

### Post by nhasian on 2009-08-25
```
lshw -C network
```

will tell you what network adaptors you have.

yes give alpha 4 a shot and see if you have better luck with the wifi.  you can make a live boot disc on a thumb drive with unetbootin

---

### Post by brandoncolorado on 2009-08-25
Here is what I get:

description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:24:2c:19:da:a9
       width: 64 bits
       clock: 33MHz


The Live works, but the install doesn't.  That is why I am afraid to install.

---

### Post by mess110 on 2009-08-25
try going to System > Administration > Hardware Drivers

maybe you can activate some drivers there.

if that is not the case try running the command

```
sudo ifup wlan0
```

if it can detect the hardware and configuration it won't say sth ending with "wlan0=wlan0"

maybe posting iwconfig can help you. Also if you know which wireless card you have and you have the drivers for windows you could try ndiswrapper

```
http://www.youtube.com/watch?v=v0Ist9aEKEg
```

---

### Post by brandoncolorado on 2009-08-25
> **mess110 said:**
> try going to System > Administration > Hardware Drivers

maybe you can activate some drivers there.

if that is not the case try running the command

```
sudo ifup wlan0
```

if it can detect the hardware and configuration it won't say sth ending with "wlan0=wlan0"

maybe posting iwconfig can help you. Also if you know which wireless card you have and you have the drivers for windows you could try ndiswrapper

```
http://www.youtube.com/watch?v=v0Ist9aEKEg
```



Thanks for the reply.  I think I have narrowed down the problem.

1)  When I boot from the USB drive, I get two different options for enabling restricted hardware drivers.  If I enable the fw-cutter one first, then the other, the wireless kicks right on and I'm off and running.

2)  On the installed version of Ubuntu, I only get the second option under restricted drivers.  I can't enable that one alone with the first.

To better show what I mean, I am attaching a screenshot.

---

### Post by brandoncolorado on 2009-08-25
As it turns out, b43 is installed in synaptic. Also, the driver seems to be installed in synaptic. However, the wireless won't start like on the live.

I see "no wireless extensions" and wlan0=wlan0.

---

### Post by brandoncolorado on 2009-08-26
Bump please help

---

