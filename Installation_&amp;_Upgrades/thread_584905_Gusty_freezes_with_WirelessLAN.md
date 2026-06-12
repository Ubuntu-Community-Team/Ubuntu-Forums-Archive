---
title: "Gusty freezes with WirelessLAN"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by DK-one on 2007-10-21
Hello,
I started using Linux with a Dapper Drake live cd. Since that worked perfectly I waited to the release date of feisty and installed that, and had the first time trouble with my rtl8180 wireless card. But then it turned out only the Driver was set on a blacklist and I was able to fix it.
This time I didn't update Feisy yet, but downloaded Gusty to check out if everything is working...

it turned out that it finds the wireless card alright and also gives me the names of the available networks, but once I give him the password my wirelesscard shows me a green light for being connected but gusty freezes and won't do anything not even to strg-alt-backspace.

Is that only a live-cd problem or will that appear also when I install gusty for good? 

Hope some one can give me an advice or should I stay with the rule never change a running system?

Thx Dominique

---

### Post by DK-one on 2007-10-25
Sorry I didn't solve the problem jet. Maybe someone out there could give me an advice with the problem above. If you need more Information on the Problem fell free to write that. I would be happy if someone takes some of his valuable time to help me out.

Thx Dominique

---

### Post by Aathos on 2007-11-07
There is a problem with the native driver for that wireless chipset that causes it to freeze the system when you try to connect to an encrypted network. The only workaround right now seems to be to blacklist the driver and use ndiswrapper.  There are several threads about doing that, but I have been thinking about writing a how-to just to put all the info in one place.  If you do a search for "rtl8180" you should find some relevant threads.

---

### Post by Aathos on 2007-11-07
Actually, I found a good How-To for installing the windows drivers by m_bridge [here]("http://ubuntuforums.org/showthread.php?t=580309"). He has it labeled for a different card, but it is the same chipset.  If you are still having problems, look at that.

---

### Post by krumble on 2007-11-10
I ran into the same exact problem when I installed gutsy on my laptop with the same wireless card.  Mine wasn't detecting any networks but when ever I would go to check the box to enable the card it would freeze and the only way to get it working again was a hard reset.  I got fed up with it and put edgy back on my lappy cuz the Wireless works without having to install any drivers.

---

