---
title: "Pre-install questions"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by Motorbikeman on 2007-03-04
Hi folks,

I'm totally new to Ubuntu and Linux in general so please be gentle with me :) 

I'm strongly considering installing Ubuntu on my laptop which is a P3 900MHz IBM Thinkpad T22 with 384mb RAM.

I was wondering if anyone sees any problems with this straight away as I do need the laptop on a regular basis and should I be looking at version 6.06 LTS or 6.10??

many thanks in advance for your time.

---

### Post by bodycoach2 on 2007-03-04
Unless you can put more RAM on that laptop, I'd recommend Xubuntu. 384mb will make the system seem slow. If you can top out the machines memory, Ubuntu should work fine.

How's the battery life on that computer?

---

### Post by Motorbikeman on 2007-03-04
Ok, I'll have a look at Xubuntu then.

As for the battery life, that would probably be 'What life??' :lolflag:  It's an oldish laptop with the original battery and with out having the power supply plugged in, I get about 10 - 15 minutes out of it. Luckily, I very rarely ever need to use it away from mains power and it definitely makes itself worthwhile as it's one of the lightest laptops I've ever used so the lack of battery life doesn't really bother me.

---

### Post by Motorbikeman on 2007-03-04
Realised I have a bigger problem than memory. I have a BT Voyager 1060 wireless card that I NEED to work, I've looked around the forums for a way to configure it, but to be totally honest, just didn't understand what I was reading. if any one could point me in the direction of a VERY basic step by step guide (i.e. words of one syllable or less ;)  ) or pm/email me one, that would be hugely helpful.

---

### Post by tyres on 2007-03-04
Hi Motorbikeman,

I've no experience with the BT 1060 card, but I have  successfully got the BT 1055 USB adapter working with Ubuntu, and the BT 1065 PCMCIA laptop adapter.

What you need to know is what chipset the adapter uses. Try running the 'lshw' command. That should show you what hardware you've got. Look for something like 'Wireless interface'. On my machine it's the last entry anyway. That may tell you what chipset you've got. For example mine says "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller", so I know I've got a Broadcom 4318 chipset.

Once you know the chipset, look at the ndiswrapper home page. There's a list there of adapters that people have got working with Linux ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List%29").
Look for entries with your chipset. That may give you a clue as to what drivers you need (possibly you have the drivers on your card's installation disk).

ndiswrapper is a piece of software that runs Windows drivers on Linux. See this page for its use  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
You may find there is a native Linux driver for your card, in which case you don't need ndiswrapper, but I doubt it. BT isn't very Linux-friendly!

Good luck!

Colin

---

### Post by tyres on 2007-03-04
Hi Motorbikeman,

I just read that old thread that you posted to asking for help, and saw that the guy there who had the 1060 said it uses the bcmwl5 driver. That's the same driver I'm using for the 1065. 

I followed this HowTo to get that working 
[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

Hopefully it will work for you too ...

Colin

---

### Post by Phil1954 on 2008-03-11
I thank you for this excellent tutorial.  I have just installed xubuntu and got my BT 1060 working happily, all thanks to your article.  I know so little about linux but this was an excellent start to working with the Terminal and installing driver packages.

Best wishes,

phil

---

