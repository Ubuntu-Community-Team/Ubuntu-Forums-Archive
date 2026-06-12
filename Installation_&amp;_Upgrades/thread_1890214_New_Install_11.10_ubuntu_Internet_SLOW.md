---
title: "New Install 11.10 ubuntu Internet SLOW"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by blazerboy777 on 2011-12-03
Just installed and updated Ubuntu 11.10 32 bit version. My internet is going very slow, download speeds of around 200 kbs and upload of about 30-40 should be roughly 1300 and 250ish... 

Any ideas or help, this is not wireless, its ethernet, just a line running to my 3600HGV 2Wire Router (ATT-Uverse).

- Its causing my terminal updates to fail among other things. Connection Drops off then restarts, yet it doesnt make the notificiation, its just as if it stops working and starts back up. Router has no ipv6 connectivity, it doesnt support it. Just trying to give you guys as much info

---

### Post by blazerboy777 on 2011-12-03
Im getting botched downloads, screwing up the entire system with this. I dont get what the hell is going in, been tryna find out for the last 5-6 hours all i can find is disable ipv6, or other commands that dont work. How do i even disable ipv6? Does it even work? I mean this is so bad iv had to reinstall ubuntu about 9 times in the past 2 days trying to get it to work. Between unsuccessful installs to successful installs that get screwed up...

---

### Post by oldtimer7777 on 2011-12-03
> **blazerboy777 said:**
> Im getting botched downloads, screwing up the entire system with this. I dont get what the hell is going in, been tryna find out for the last 5-6 hours all i can find is disable ipv6, or other commands that dont work. How do i even disable ipv6? Does it even work? I mean this is so bad iv had to reinstall ubuntu about 9 times in the past 2 days trying to get it to work. Between unsuccessful installs to successful installs that get screwed up...

Sounds like a faulty network connection to me.  Modem, Router, etc etc...  Cable splitters..  data line..  Call your ISP have them do a quality check.

---

### Post by blazerboy777 on 2011-12-03
Theres no way its my isp or anything in my box, was running windows Perfectly fine 2 days ago, my laptop still runs circles (internet speaking) over my workstation.....its a linux problem theres some setting something wrong in it somewhere, some setting I need to flip, so file I need to change, I just dont know what...

Im running off my motherboard lan if that makes any difference, MSI GD65 P67A motherboard intel

---

### Post by oldtimer7777 on 2011-12-03
> **blazerboy777 said:**
> Theres no way its my isp or anything in my box, was running windows Perfectly fine 2 days ago, my laptop still runs circles (internet speaking) over my workstation.....its a linux problem theres some setting something wrong in it somewhere, some setting I need to flip, so file I need to change, I just dont know what...

Im running off my motherboard lan if that makes any difference, MSI GD65 P67A motherboard intel

Do you keep using the same ISO to create you installation disc? Sometimes a bad burn, or a bad image can cause this.

I always install from a live stick flash drive, and never use cd-rs dvd-rs as they can be problematic.

---

### Post by blazerboy777 on 2011-12-03
No iv installed from 3 sources, 2 are the same 32bit cd, ones on cd, ones on usb then another dvd copy of the 1.5 gb version with language packs installed. 

The one that iv been able to get up and im on is the usb one 

Restarts fine so its ok. Seems pretty stable so far,

The internet though is making me distraught theres something wrong and im searching, googling, yahooing everything but I dont want to change everything just to find out what i did screwed the system up.

What would be your first idea as what to do if this was happening to you.

Symptoms : slow speed (very slow) and sparatic network drop offs, but still showing as connected. I mean to even use the apt-get terminial command I have to disconnect the lan , and restart it and quickly go to terminal as it will usually start bugging up after about 20 seconds or so...

---

### Post by dandnsmith on 2011-12-03
I can see 2 areas which you could look to - one of which has already been mentioned.

- IPv6: find the network connections in the config system stuff, and edit the detail - there is a tab for IPv6 where you can tell the system to ignore IPv6. This sorted a problem for me at one stage

- I don't know the motherboard, but you might have one of the chipsets which cause a problem. To check, look using *lspci -v* to see if the ethernet is using module r8169 - if it is, then it needs to be reconfigured to use r8168 (as r8169 has problems which r8168 doesn't). This has solved problems I had with Mint11, Ubuntu 10.04 and Ubuntu 11.10 on one motherboard.

There are threads on sorting out the latter on these fora.

---

### Post by blazerboy777 on 2011-12-03
Wow you were right it is using r8169, ill look up how to change it and keep you posted. Thanks buddy.

---

### Post by dandnsmith on 2011-12-03
I started [here](http://ubuntuforums.org/showthread.php?t=1861865&highlight=r8169), but cannot currently get to the jamesonwillams link from there for the next stage todo.
The best page, anyway is [here](http://ubuntuforums.org/showthread.php?t=1465703), with good detail in the last posting by tlib747 (but watch out at the end, as I found the move command for the initrd doesn't work as intended because you end up moving the link, not the file)

---

