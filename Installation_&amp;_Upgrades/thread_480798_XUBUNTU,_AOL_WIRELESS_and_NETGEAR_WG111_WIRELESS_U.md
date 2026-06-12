---
title: "XUBUNTU, AOL WIRELESS and NETGEAR WG111 WIRELESS USB ADAPTER"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by dan fisher on 2007-06-21
I have got a USB wireless adapter which is on the compatibility list as being completely compatible with UBUNTU 7.04 (without ndiswrapper).

I have installed XUBUNTU 7.04.

I was told that after installation and plugging in said wireless adapter UBUNTU would detect it and install drivers.

Is this true of only UBUNTU and not XUBUNTU?

The system doesn't do anything when I plug the USB wireless adapter in.

I left the wireless adapter unplugged while installing ubuntu - was this a mistake?

The wireless adapter is a NETGEAR WG111 (the most compatible adapter I could find)

HELP!

also I will be able to connect to the AOL service from XUBUNTU through the wireless router supplied with AOL - a NETGEAR 54mbps wireless router (model DG834G v3) won't I?

I am not interested in using the AOL software (i.e. PENGAOL).

I just want a straightforward connection AOL is the cheapest service on the block here (UK).

---

### Post by dan fisher on 2007-06-21
By the way the machine is a DELL Dimension 8300

maybe USB isn't working?

---

### Post by dan fisher on 2007-06-21
ok on issuing the lsusb - list USB devices command I get:

Bus 005 Device 002: ID 0846:6a00 NetGear, Inc. WG111 Wifi (v2)

I bought this USB wireless card as the UBUNTU site says it works out of the box in feisty (7.04).

where to next?

I want to use the native drivers not the ndiswrapper drivers.

I thought it would detect and give me an installation dialogue something like plug n play ...

(XUBUNTU 7.04)

---

### Post by philcolbourn on 2007-06-24
Netgear seem to have poor product labeling.

You may have a wg111v2 based on realtek rtl8187.  Other people have reported that this works.

Other wg111v2 devices are based on the prism54 and some like mine are actually wg111v1 according to the netgear we site (s/n beginning with WG72...)

So you should see a rtl8187 module loaded using lsmod
also your should see an interface with 802.11 support listed when you enter iwconfig.

---

### Post by mattg89 on 2007-06-24
Go to Applications --> System --> Network
Does the Wireless connection show up?
If it does, it may just need enabling and DHCP configuring.
If not, then it is not recognised by the system, so the drivers are either not loaded, or not working.

---

### Post by dan fisher on 2007-06-24
thanks thanks thanks --- getting there

i've listed where I got to last night on the wireless forum

[http://ubuntuforums.org/showthread.php?t=480798](http://ubuntuforums.org/showthread.php?t=480798)

I chose this forum before I saw there was a wireless setup forum

---

### Post by jonty on 2007-06-24
I have the same model and found it worked as is with feisty.  I had to, however, go into the network-admin, select properties of "Wireless connection (wlan0)" and disable roaming mode.  After that I selected the network manually, and presto.  Al went well.  Good luck

---

