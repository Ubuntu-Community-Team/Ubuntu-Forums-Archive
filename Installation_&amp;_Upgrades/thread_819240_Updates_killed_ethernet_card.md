---
title: "Updates killed ethernet card?"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by jbc-wales on 2008-06-05
Brand new pc, running Hardy 8.04, dual core etc.

System was working normally this am. 
System updates advised: all updates added.

Following required restart, the internet connection was lost.

Network manager no longer recognises the network device (ethernet-connected ASDL modem).

Cannot use manual configuration to connect

Tried ```
sudo pppoeconf
```

Declares NO INTERFACE FOUND, Sorry, no working internet card could be found...

Offers to run modconf to load driver manually

returns: ```
/usr/sbin/pppoeconf: 520: modconf: not found
```

Ran Ubuntu Hardward Tests

Realtek Ethernet Controller IS detected...
But then reports "No Internet connection"

Tried ```
dhclient
```

Reports: ```
No broadcast interface found - exiting
```

ifconfig returns

```
lo ...(etc)
```

but no eth0 or eth1

```
lshw -C network
```

returns: network UNCLAIMED and no LOGICAL NAME

Am now at my wits end. 

Can anyone point me in a right direction?

Is this likely to be a hardware failure? (An orange light on the ethernet controller is lit)

If all else fails, is there a reliable way to roll back the updates? And then presumably selectively update?

Any other advice?

(I'm a newcomer to Ubunut...though learning fast...generally the hard way!):(

---

