---
title: "IBM ThinkPad X60s Heats up on Ubuntu 12.04"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by brodedra on 2012-08-08
Hi!

I have been facing a strange problem after installing Ubuntu 12-04 LTS on my IBM Lenovo ThinkPad X60s laptop (Ultra portable series). The system gets really heated up. This is very abnormal because I had been using it flawless with Ubuntu 11.04

Do I need to install any drivers that can calm down the heat? cause this is really annoying and the system is like red hot within 30 minutes of usage inspite of the fan working properly!

I did a very clean installation from ground zero again just to make sure nothings wrong in the installation. Yet, the problem persists! :confused:


[LIST]
[*]I have Intel CoreDuo Processor 1.8 GHz 2MB L2 Cache
[*]2 GB DDRII Ram (800 Mhz FSB)
[*]60 GB Hitachi 5400 RPM Drive 16MB Buffer
[*]Intel Wi-Fi abg
[/LIST]

Help is really appreciated.

---

### Post by mörgæs on 2012-08-08
If you let it stand idling with only **top** running, does it still overheat? 

Do you see a high CPU load in **top**?

---

### Post by brodedra on 2012-08-08
> **mörgæs said:**
> If you let it stand idling with only **top** running, does it still overheat? 

Do you see a high CPU load in **top**?


The system works in a stable state. I checked the CPU process map too - it's around 5% usage under idle condition (i.e, just after the system boot).

However, what I had observed is that when I use internet, it generally gets heated up. If I turn the Wi-Fi adapter off, the system cools down. My search led me to the System manual of my ThinkPad which indicates that the Wi-Fi daughter card is located below the keyboard on the right side - exact place where the maximum heat is felt. This indicates that some how, using the Wi-Fi is probably heating up my system. However, turning it off leaves me without internet!

It really gets so hot that I possibly can make a coffee on it! Phew! :(

---

### Post by mörgæs on 2012-08-08
Sounds like you've found something. What happens if you use a wired internet connection for some time?

---

### Post by brodedra on 2012-08-08
> **mörgæs said:**
> Sounds like you've found something. What happens if you use a wired internet connection for some time?

On LAN, it works like a champ. No heating or anything. But I have to keep Wi-Fi disabled. Found a tool called "thinkfan" used to control fan speed for Thinkpads. However it didn't help either. What actually worked for me was to do a full system update - after which, it's back to normal on Wi-fi without heating up. This either means some driver glitch has been resolved or simply put, I'm struck by a miracle. But whatever it is, my system is back to normal and I'm rocking! :guitar:

Thanks.

---

### Post by TheCan on 2012-08-28
I got the same issue on a "normal" X60 (not X60s) and after I found [this Thread]("http://ubuntuforums.org/showthread.php?t=875195") I also suspect the wireless card to cause the heat problem. The laptop runs very stable though, but it is very unpleasant to touch it.

The heat certainly does not come from the SSD which sits in the middle right but certainly from the lower right part of the base cover where the Wireless card sits. In my model it is a Intel PRO/Wireless 3945ABG [GOLAN] card.

Does putting the card into power save mode really help? Otherwise I think I shall consider replacing the card by something else, this heat is really extreme!

It would be interesting to know though if this problem also happens when running older Ubuntu versions like 10.04...

---

