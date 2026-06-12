---
title: "Can't get VMware NAT/Bridged networking to work after install..."
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-10-26
I just installed VMware (FINALLY got it figured out after it screwed up with the 7.10 upgrade).  My VM's are running, but my networking doesn't work for them.

I have two networking interfaces in my computer.  An Ethernet interface (eth0) and a wireless Dlink card (ath0).  Currently, I have vmnet0 configured to NAT with the ath0 interface on subnet 192.168.1.0\24, which is the same subnet as the rest of my house network.

I've been running vmware-config.pl over and over, playing with different network settings, and I still can't get Internet explorer in Windows VM to get google.  Don't know what's wrong....

Please help!

---

### Post by Somatik on 2007-10-27
> **diablo75 said:**
> I just installed VMware (FINALLY got it figured out after it screwed up with the 7.10 upgrade).  My VM's are running, but my networking doesn't work for them.

I have two networking interfaces in my computer.  An Ethernet interface (eth0) and a wireless Dlink card (ath0).  Currently, I have vmnet0 configured to NAT with the ath0 interface on subnet 192.168.1.0\24, which is the same subnet as the rest of my house network.

I've been running vmware-config.pl over and over, playing with different network settings, and I still can't get Internet explorer in Windows VM to get google.  Don't know what's wrong....

Please help!

I'm using bridged networking and everything is running smooth

---

### Post by diablo75 on 2007-10-27
I figured out my problem.

For some reason, if I have my ath0 interface bridged to VMware, VMware won't start at all.  Won't even come up.  But it will work if I NAT it to VMware, and let it probe for the available network.  I told it to NAT my wireless adapter (ath0, in this case), and probe for an unused subnet during config.

Then, start VMware Server back up and connect to the local host as usual.  Then edit your machines virtual machines.  I selected custom this time, and then picked vmnet2 out of the list.  Then start my VM up, and networking worked!

---

