---
title: "Sudden network disconnection."
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2009-10-08
Using the latest updates for Karmic, I've found it's starting to randomly disconnect from the network. Anyone else suffering similar?

---

### Post by taavikko on 2009-10-08
> **Sslaxx said:**
> Using the latest updates for Karmic, I've found it's starting to randomly disconnect from the network. Anyone else suffering similar?

Only when using wireless and ath9k is the driver...
[https://bugs.launchpad.net/bugs/414560](https://bugs.launchpad.net/bugs/414560)

---

### Post by Sslaxx on 2009-10-08
Thing is, I'm not using either of those (desktop PC, wired connection)...

---

### Post by taavikko on 2009-10-08
> **Sslaxx said:**
> Thing is, I'm not using either of those (desktop PC, wired connection)...

Does dmesg show any info?

Is there network heavy apps running at the time of disconnects? torrent... etc.

Have you tested resetting modem?

---

### Post by Sslaxx on 2009-10-08
Tried a router reset, did nothing. Next time I boot back into it I'll log the dmesg (should've anyway, I guess). Not running any network-heavy apps when it happened.

---

### Post by nilarimogard on 2009-10-08
It happens to me too, it appears the dns is resseted and the /etc/resolv.conf is left blank from time to time, for no apparent reason.

I solved it by completely removing network-manager (so that it doesn't delete my dns anymore) and entering my dns manually in the resolv.conf file (used OpenDNS).

---

### Post by taavikko on 2009-10-08
Also include "sudo lshw -C network"

Are the disconnect really random, or could you try to pinpoint them to something specific?

---

### Post by yellerKat on 2009-10-08
I had that very briefly last week; it disappeared after an update so I forgot about it.

Are you on Virgin Media cable? Could be them!

---

### Post by Sslaxx on 2009-10-08
No, not on cable. Demon is my ISP.

---

### Post by Sslaxx on 2009-10-08
For further info:

sudo lshw -C network:```
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

dmesg: [can be found here.]("http://sslaxx.twu.net/dmesg.8-Oct-2009.1241.txt")

---

### Post by taavikko on 2009-10-08
> **Sslaxx said:**
> For further info:

sudo lshw -C network:```
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

dmesg: [can be found here.]("http://sslaxx.twu.net/dmesg.8-Oct-2009.1241.txt")

So you're using KK in virtualbox... 
Try changing the NIC from the settings.

---

### Post by Sslaxx on 2009-10-08
Actually, no I'm not. I suspect that's the VirtualBox drivers reporting DISABLED.

---

### Post by Devour on 2009-10-08
I'm having a problem like this. It seems to really only happen when I'm playing a game like Quake III Arena or if I'm downloading something big. And it doesn't happen immediately. It appears to happen randomly while doing one of these things.

My sudo lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:7c:4a:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=192.168.0.100 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:9b:1a:c0:5c:88
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Here is my dmesg: [http://2353352.pastebin.com/m33deff50](http://2353352.pastebin.com/m33deff50)

The bottom part is really only the relevant part I guess.

---

### Post by notoriousdbp on 2009-10-09
Just to add my contribution here I'm using Karmic 64-bit and the performance of ath9k with network manager is terrible.  The network keeps suddenly dropping and refuses to re-connect.

---

### Post by cariboo on 2009-10-09
From the output of:

```
sudo lshw -C network
```

and dmesg you have a similar motherboard to the one I have try:

```
sudo lshw -C bridge
```

your network device should show up in that listing. I can see that the proper driver is loaded in dmesg, so It doesn't seem to be a driver problem.

Edit: This is in reply to Sslaxx, I bunch of me to's showed up while typing this post.

---

