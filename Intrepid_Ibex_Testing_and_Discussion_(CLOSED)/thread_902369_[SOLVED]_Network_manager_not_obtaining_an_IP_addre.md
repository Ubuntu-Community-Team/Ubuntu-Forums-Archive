---
title: "[SOLVED] Network manager not obtaining an IP address"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by NachoMas on 2008-08-27
Hi!
I am having some problems after updating network manager to 0.7. It seems that network manager is not able for some reason to configure the interface with the info it gets from DHCP. If I make a manual dhclient -i eth0, I get and IP address, but if I try to obtain the IP address with Network manager, then the icon starts spinning and after some time it says I have  no network connection. Now, the interesting thing is that wireshark shows that the dhcp request is being sent and replied... so the machine gets an IP address, but somehow nm fails to configure the interface! I'm attaching the trace from wireshark and the output of ifconfig after trying to get the IP address in nm... The only way, as I said is by using dhclient manually... I hav just upgraded network-manager without upgrading anything else to Intrepid.. .could that be the problem?

Thanks for the help! I'm a bit puzzled by this one!
/Nacho

Update: Ah, well, upgrading ifupdown and dhclient3 made the trick...

---

### Post by Scunizi on 2008-08-27
Good work doing the trace.  It should really be  listed on Launchpad where the DEVs can get to it and figure out a fix.  You could also ask about it in irc.freenode.net #ubuntu+1

Must be early for me.. I missed that you'd solved it and had the solution. Early hour and no glasses is my excuse.. :)

---

