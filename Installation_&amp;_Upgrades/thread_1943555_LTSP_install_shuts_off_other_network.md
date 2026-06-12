---
title: "LTSP install shuts off other network"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by ceaecc on 2012-03-19
I have two network connectors, on on the mainboard and the other in a PCI slot, and have tried LTSP several times both from a live-CD session (actually 11.10 is a DVD) and by installing to disk. Both network connections work fine for connecting to the intenet, but as soon as LTSP is tested from the live-CD session the internet shuts off and nm-tool reports that connection -- whether it is eth0 or eth1 -- as unavailable or unmanaged. I have been unable to find an explanation anywhere of the meaning of the State reports for nm-tool, as have seen unavailable, unmanaged and unconnected but am not sure the difference between those states. 

This could be related to the computer, Dell Optiplex 755, because using the same PCI card on an older computer I did have LTSP from Edubuntu 8.04 up and running OK. 

I have tried switching cables each way and reinstalling, switching cables after installing, every possibility, and the behavior is the same.

Any possibilities? Thanks for thinking about this...

---

### Post by ceaecc on 2012-03-19
For example, if I install LTSP with the internet cable on the mainboard connector (eth0) and the gigabit router on the NIC card (eth1), then eth0 does not work, registering a state of unmanaged or unavailable with nm-tool. But I can get the internet back by switching cables to eth1, and then nm-tool reports eth1 as connected. The same phenomenon occurs in reverse of the two network connectors.

---

