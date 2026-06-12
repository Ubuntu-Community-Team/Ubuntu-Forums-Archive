---
title: "wireless lost after upgrade."
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-01-24
I install the lates Ubuntu few weeks ago. My wireless card (D-Link Aire Plus) was recognized immediately. Unfortunately I did a upgrade yesterday. After the upgrade, my wireless card can not be found any more. 

Blow up the "Network" tools in the Control Center, there are no items for wireless at all.

What could be the problem?
Someone can help? where can find the drivers for "D-Link"?

Thanks

---

### Post by szymon_g on 2007-01-25
hi.
i've get problem similar to your. i think the reason of it is a upgrading a kernel, without upgreading 'linux-restricted-modules'- in this modules was a driver for my abg3945 wi-fi card. is a command iwconfig showing something?

---

### Post by hopestorm on 2007-01-25
The iwconfig command yiels:
lo          no wireless extensions
eth0      no wireless extensions

I use 
$SUdo iwconfig wlan0 my-NET-ID
I got
Unrecogonized wireless requests .

Now, my wired connection is dead also, may be due to my installation of ndiswrapper.

That is, my computer is disconnected from internet totally, I can not even install more softwares (if necessary) to solve the problem.

---

### Post by Princey on 2007-02-26
I am experiencing the same problem. My wireless worked fine under Kubuntu Edgy. Did the upgrades this morning that upgraded my kernel and after reboot, no wireless devicies found. lspci does list my D-Link DWL 510 pci card, but that's about it. Knetwork manager says this :

> Link Down
Link Up
Network Device removed
NetworkManager is now connecting
NetworkManager is now connected
NetworkManager is disconnected
New Network Device found
New wireless network device found
Switched to offline mode
Wireless Network Disappeared


Thankfully, I've got a wired connection but it's the wireless card I have configured for main router configurations and vpn purposes. Any of you with that problem got it rectified?

---

### Post by Princey on 2007-02-26
Update:

Got it working after searching for linux-restricted modules in adept. Thing is I had it installed already. Oh well, I'm back in business now.

---

