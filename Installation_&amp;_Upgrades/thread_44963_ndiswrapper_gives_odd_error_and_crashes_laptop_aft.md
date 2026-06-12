---
title: "ndiswrapper gives odd error and crashes laptop after sleeping"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by kerinin on 2005-06-28
i'm using a dell inspiron 7000 laptop with a pII 433 processor and 256 megs RAM with a linksys WPC54G v4 wireless PCMCIA card.  

i've been trying to get ndiswrapper to work smoothly for about two months now.  currently it works OK, but i feel like my network connection is slow, and i have two errors i can't find any reference to on google or here.

the first is that every time i start up, an error message is thrown that reads:

```
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper: using irq 11
ndiswrapper (NdisWriteErrorLogEntry:261): log: C000138B, count: 1 (00000102)
ndiswrapper (set_essid:57): setting essid failed (00010003)
wlan0: ndiswrapper ethernet device 00:0f:66:bc:12:ab using driver wlipnds
ndiswrapper: driver wlipnds (Cisco-Linksys, LLC.,01/05/2004,1.22.01.2004) added
``` 

there are some references to NdisWriteErrorLogEntry in various places, but none that seem helpful.  and i have no idea what 'essid' is.

the second behavior is that every time i close my laptop and then wake it up my network access is gone.  ifconfig says everything is ok, but i can't talk to the network.  even more surprising - if i try to restart the ndiswrapper module or remove the wireless card my kernel panics and i have to force-reboot my laptop.

last night i completely removed ndiswrapper and all settings (had to reinstall the linux image i removed so much) and reinstalled the most recent package, so it's up to date - still the same problem.

any help?  i know ndiswrapper is a common problem, sorry to bring it up again...

---

