---
title: "NM 0.7 and 3G mobiles"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Foaming Draught on 2008-10-05
I'm a gob-smacked little vegemite.  I just posted [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/278468"), triggered by apport.  But when I re-started my system, NM 0.7 recognised that I had a Samsung mobile phone plugged into a usb port, and brought up a dialogue which enabled me to log onto Telstra mobile broadband via my phone by clicking a simple drop-down menu.   Previously, I had to enter a complex script and use pon/poff in terminal.

It's wonderful stuff.  I guess that it would work for 3G cards and usb modems, too.  It would be nice to have a usage monitor, but I mustn't be churlish after such a great feature is introduced.  Who needs umtsmon now?

(Alpha 6 with all updates)

---

### Post by jfernyhough on 2008-10-05
I just tried it with my Nokia 6120c. Wow. Plugged it in, set it to PC Suite mode, and it's detected automagically. Set the provider, all done. Great.

Now if only I can work out why this particular phone doesn't like being used as a modem... (works fine on my old 6630).

--edit
GOT IT!

To enable mobile broadband tethering on your 3 mobile phone in network manager 0.7 nm0.7 e.g. Nokia 6120c 6120 classic (trying to hit some keywords for search here).

Edit the connection in NM0.7, and change the access point from '3internet' to 'three.co.uk' . Save and try again. You might also change the network type from '3G only' to 'prefer 3G'.

This is for a 3 monthly contract with Internet Max addon (1GB, not mobile broadband).

---

### Post by plun on 2008-10-05
Please take a look at this wiki and if possible also
add valuable info to it.

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

Its too many "UNKNOWN".....

---

### Post by Foaming Draught on 2008-10-05
You're right plun, there are too many "Unknowns".  But I haven't got the foggiest how to edit the wiki.  If someone else wants to do it:

Mobile phone
Samsung A411/A412  UMTS/HSDPA/GPRS/GSM
usb and bluetooth (haven't tested NM 0.7 connection with bluetooth)
Provider Telstra (with datapack)
Dial *99**1*1#
AP telstra.internet
No user or password necessary.
Working perfectly at download speeds between 240kbps and 1.3Mbps

---

### Post by plun on 2008-10-05
Well... I am a complete "wiki-noob" and a "WYSIWYG" fan. :)

Perhaps we have someone familiar with "strange" wiki syntax... ?!

---

### Post by foxy123 on 2008-10-05
I tried to connect my N95 in PC mode and was able to configure the connection. But after the reboot I cannot see the connection in the list of available connections.

---

### Post by adolfotregosa on 2008-10-07
hs2300 card (ms8775 from hp) connects but the manual dns do not get applied, i always have to edit resolv.conf and delete the first dns for all websites to open. :( besides that all is ok !!

---

### Post by zoomy942 on 2008-10-07
> **adolfotregosa said:**
> hs2300 card (ms8775 from hp) connects but the manual dns do not get applied, i always have to edit resolv.conf and delete the first dns for all websites to open. :( besides that all is ok !!


wait..  yours just works?  i have an embedded card from hp too... ill have to reenable it and see if it works

---

### Post by PmDematagoda on 2008-10-08
> **adolfotregosa said:**
> hs2300 card (ms8775 from hp) connects but the manual dns do not get applied, i always have to edit resolv.conf and delete the first dns for all websites to open. :( besides that all is ok !!

This may be something to do with some wrong information in the NM Service Provider Database, take a look [here]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders") and see if it is something wrong and if so, submit a patch to fix it(it is very simple as long as you have the necessary data).

---

