---
title: "prism 2.5 wont connect on fresh upgrade"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by roman5x3 on 2008-10-21
I just upgraded to intrepid and my wireless will not start up.  It is able to find the networks and lets me attempt to connect but fails every time. 

Here is the tail of my dmesg output:
```

[ 4330.148866] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[ 4344.148532] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[ 4363.148796] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[ 4368.551961] wifi0: invalid skb->cb magic (0x0000001a, expected 0xf08a36a2)
[ 4368.568074] wifi0: LinkStatus=2 (Disconnected)
[ 4368.568358] wifi0: LinkStatus: BSSID=00:14:bf:1e:49:62
[ 4369.206280] wifi0: LinkStatus=1 (Connected)
[ 4369.206545] wifi0: LinkStatus: BSSID=00:14:bf:1e:49:62
[ 4369.211455] wifi0: invalid skb->cb magic (0x0000001a, expected 0xf08a36a2)
[ 4369.215462] wifi0: invalid skb->cb magic (0x0000001a, expected 0xf08a36a2)

```

My lscpi:
```

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```


Please help.

Roman

---

### Post by roman5x3 on 2008-10-25
I tried a live cd of Intrepid Ibex and it was able to pull up the wifi no problems which leads me to believe that the problem is somewhere in the upgrade of network manager.   What I want to do is wipe out all the network settings left over from Hardy and start fresh.  My question is where are those setting and what would be the easiest way to get rid of them?  Keep in mind that I tried completely removing network manager and all its config files via synaptic and reinstalled it and it did not work to erase the files left over from Hardy.

Roman

---

