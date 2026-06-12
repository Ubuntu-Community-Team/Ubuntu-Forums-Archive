---
title: "western digital woes"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by penquin on 2006-06-22
Help me please.  

I am trying to dual boot my computer, but because of my WD hard drive I can't seem to do this.  I have tried almost everything to get my hard drive to be recognized as the size it is.  I have tried a control card, I tried starting from win98 and upgrading to winxp, I have tried just installing winxp, I tryed gpart live cd.  The only way I get the full 120G is if I use the WD Dynamic Overlay program (which doesn't allow dual booting) or if I only use ubuntu.  I want to use both winxp and ubuntu, but I can't.  I am about to try with my backup drive and my other hard drive in my machine to see if I can use two hard drives and have two partitions on the other hard drive to see if that works, but the only problem is that the other hard drive is only a 10G and my backup is a 20G and it may work in test because winxp doesn't care if it is a 10G.

---

### Post by kewldude606 on 2006-06-22
Do you know if it is SATA or IDE?  SATA cables are thin, about 2 cm wide.  IDE cables are 40 pins wide (2 or 3 inches) at the plugs.

---

### Post by penquin on 2006-06-22
It is an ide. I double checked with WD and they don't have any new DDO software.

---

### Post by penquin on 2006-06-23
you are not going to believe this I tryed a different jumper setting and put it slave to another drive then booted it as primary and now it is constantly recognizing it as 120 G.

---

### Post by drumkitcat on 2007-02-07
was that with the DDO software?

I'm confused.. you put it as a slave to another drive so the jumper was changed from master to slave... but then you booted it as primary - how? 

I have a WD 80gb drive that I fear may need the drive overlay to be recognized on my AMD K6-2 450mhz system as it's currently hanging looking for the primary ide - after I had completely installed ubuntu on it.

So, I'm just looking for options to get it working...

---

### Post by Huntz23 on 2007-03-21
A thing to consider is can your motherboard recognize drives that large?

If they can are the BIOS's enable for drives that large?

I have a WD 80GB that I have in my machine running xp and learned the hard way that it dont dual boot.  If there is anything I can help with let me know.

---

