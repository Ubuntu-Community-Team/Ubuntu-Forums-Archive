---
title: "Fesity upgrade and intermittent network problems"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2007-04-21
When I wake up from hibernating, my computer sometimes does not get an IP address.  I check using ifconfig, and there's no address.  ifdown/ifup appears to work, getting an address from DHCP, but when I look using ifconfig, there's still no address, and no network applications work.  The only thing that fixes this is rebooting.

---

### Post by Piviul on 2007-04-21
Have you tried /etc/init.d/networking restart?

Piviul

---

### Post by rrwo on 2007-04-21
No, but the point is that I should not be having these problems.

Running a command when I wake up from hibernating is not a fix. It's a band-aid.

---

### Post by rrwo on 2007-04-21
> **Piviul said:**
> Have you tried /etc/init.d/networking restart?

It doesn't help.

If I ifdown my wireless interface, then I can ifdown and ifup my wired interface and it works.

My guess is that when there is no wireless network available, it still wants the wireless card to be the default card.

---

### Post by rrwo on 2007-04-27
I did a reinstall of Feisty, and for a brief time, everything was ok.

Now the problems seem to have come back again for my wireless card.

But alas, the audio is suddenly working. So either the sound works, or my audio works, but rarely both,  So I suspect that there may be a connection.  But maybe not.

Doing an /etc/init.d/network restart of ifdown/ifup eth1 does not help the problem at all.

My wireless access point is fine. Nothing has changed with the configuration. It's just not working sometimes.  Here's what ifconfig shows for the interface:
```
eth1      Link encap:Ethernet  HWaddr 00:13:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:b0002000-b0002fff 

eth1:avah Link encap:Ethernet  HWaddr 00:13:XX:XX:XX:XX   
          inet addr:169.254.8.169  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000 Memory:b0002000-b0002fff 

```

(The XX's are my editing of the MAC addresses.)

What is "eth1:avah", anyway?

Sometimes dhclient claims to get an IP address for it when it doesn't show for the device.  Othertimes it says it's gotten no lease form the DHCP server.  I note that the LED for the wireless doesn't go on.

---

