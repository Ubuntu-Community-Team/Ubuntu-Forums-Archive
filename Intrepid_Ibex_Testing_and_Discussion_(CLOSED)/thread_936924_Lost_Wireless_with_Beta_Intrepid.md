---
title: "Lost Wireless with Beta Intrepid"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by JacquiOh on 2008-10-03
I've tried the old ndiswrapper thing that worked in Hardy and Gutsy but no joy.

And I can't get my 3G phone to work with the computer either, which is why I decided to upgrade :(

So I'm a sad saaad person right now! lol

The wireless light stays on whether or not the switch is turned on.

Can anyone help? This is the output of lshw -C network

```
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3c:b1:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:52:9e:f7:f6:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by iponeverything on 2008-10-04
If there is native driver that was working, remove the windows driver
 and at the prompt run:

nm-applet&

---

### Post by Frijolie on 2008-10-05
I'm not using a Broadcom wifi card but I'm having to continually type "nm-applet&" every time I load my OS to get a working Internet connection. Adding that line to Sessions doesn't help.

---

### Post by iponeverything on 2008-10-05
This might help:

[http://hllug.org/article.php/20080521214753647](http://hllug.org/article.php/20080521214753647)
or this
[http://sudan.ubuntuforums.com/showthread.php?t=924118](http://sudan.ubuntuforums.com/showthread.php?t=924118)

---

### Post by Kevbert on 2008-10-05
> **JacquiOh said:**
> I've tried the old ndiswrapper thing that worked in Hardy and Gutsy but no joy.

And I can't get my 3G phone to work with the computer either, which is why I decided to upgrade :(

So I'm a sad saaad person right now! lol

The wireless light stays on whether or not the switch is turned on.

Can anyone help? 

It seems that the Broadcom firmware drivers are not supplied with Intrepid Beta. You can get them from [COLOR="Red"][here]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR].  I would have thought the B43 drivers would be included. I'm in the same situation with my BCM4306 as I've just installed Kubuntu 8.10 Beta.

---

