---
title: "Stuck on &quot;Configuring Network Interfaces&quot;"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Rubber_Ducky on 2007-05-18
Hi I've just installed Ubuntu (Dapper) for the first time. I tried to install Feisty but the live CD kept freezing.

Anyway when I boot up into Dapper it hangs forever on "Configuring Network Interfaces". I tried booting in "Recovery Mode" and still it didn't boot. I left it for a good 10 minutes since many people said the hang wasn't permanent but it still didn't boot.

What should I do now? You should know I'm a Win XP man usually and don't know too much about linux.

System spec:

AMD Athlon 64 3200+
1Gb of Crucial RAM
nVidia 7600GT (XFX XXXXXXXX... edition :p )
ASUS A8N-SLi SE Motherboard (Skt 939)
Using a Belkin Wireless network card for networking

---

### Post by loserboy on 2007-05-18
I had that problem, to be able to boot I had to take out my wireless card (although there are other ways to do it)

I went to a comp that had internet and looked up my wireless card to see if the chipset was supported and it wasnt

newer versions (edgy/feisty) offer more support for cards you could try installing one of those, but the first thing to do is find out what chipset your card has

---

### Post by Rubber_Ducky on 2007-05-18
Is there anyway of doing this within windows? Or should I look on the manufacturers site or what?

My card is this:

Part Number: # F5D7000uk
label next to it says ver.6000uk

Its called "BELKIN Wireless G Desktop Network Card"

---

### Post by loserboy on 2007-05-18
oh do u have a dual boot setup?

yea there are some sites that list compatibility, ill go find them if i can


this is just one of the sites, part of ubuntu wiki, but not always the best updated, ill look some more but i'm at work
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

---

### Post by loserboy on 2007-05-18
heres another that identifies broadcom chipsets [http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom](http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom)

ha, I just thought of something though, can you bot onto the dapper livecd still even though you can't boot normally?  if so boot into it and go to a terminal and type "lspci" 
that will give you the info we need on your card.

otherwise try looking around these forums to "disable network device configuring while booting" so we can learn more about your card

---

### Post by Rubber_Ducky on 2007-05-18
Yes I am running XP dual boot, and I can run off the Linux CD, so I'll go do that now and see what it says! 

Thanks for the help

---

### Post by Rubber_Ducky on 2007-05-18
Ok the results:

I ran lspci in terminal like you told me to, and since I can't copy paste between OSs heres what it says thats relevant:

Network controller: RaLink: Unknown device 0301

Everything else was the other components.

Also,  System > Networking acknowledges that there is a wireless connection, but even with all the right settings put in it can't connect to the internet on it.

---

### Post by loserboy on 2007-05-18
I'm not gonna be around a comp for the rest of the night, but search around using "RaLink: Unknown device 0301" as a keyword, and i'm sure you'll find an answer, if not ill check this thread tomorrow

---

### Post by Rubber_Ducky on 2007-05-18
Yes I have found the answer, but to the wrong question!

Everyone else seems to have the issue of their wireless card not being recognised, lucky them. At least their systems boot up! :p

I still havn't found anyone with a problem similar to mine. I'll keep looking though.

---

### Post by loserboy on 2007-05-21
man, I've been looking all over for an answer to this,I can't come up with anything that will surely fix it, seems that chipset is either the RT61 or RT2500 if you wanna keep looking. if you're set on keeping ubuntu maybe think about buying a more friendly card.

---

### Post by Shonkin57 on 2007-11-20
This may or may not help, as the thread is fairly ancient. But "RaLink" is a chipset that appears in my own network card, the one I foolishly swapped out of my laptop in favor of an old Orinoco silver card. Bleah. Anyway, my card is a HAWKING 2.4gig wireless card, and it is auto-identified by Ubuntu 7.10 as an RaLink card. I think Ubuntu 6.06 or whatever also properly identified it. Only odd behavior tonight is that it occasionally drops the network connection, and I have to re-start it via the networks applet (only takes a couple seconds, but still!).

Pressing on...

jon t

---

