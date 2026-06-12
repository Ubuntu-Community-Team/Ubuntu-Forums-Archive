---
title: "[SOLVED] installation with command line only"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by jamesjeffries1 on 2008-11-16
I've been using ubuntu and linux for a few years now on home laptops etc. just got hold of an old pc. thought it'd be interesting to set it up with just the command line. just wondered if anyone had any ideas on where to start before i started messing around? maybe ubuntu sever edition? would this include most of the commandline utilities and applications of ubuntu? or would they need installing seperately? 

it doesn't have a wireless card, only ethernet so was thinking of setting up my laptop as a DHCP server to share the internet to it via a hub i picked up ages ago. Is this the best way of doing it without buying a new wireless network card for this computer?


thanks,
James

---

### Post by kerry_s on 2008-11-16
you can use the server or alternate cd. not sure about the hub thing, i'm guessing you mean a router and you want to use the laptop as the gateway?

---

### Post by Pumalite on 2008-11-16
You have a lot of good ideas, but I'd like to know the memory and graphics in your machine.
A Server maybe OK. If not; this:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Your router seems Ok.

---

### Post by jamesjeffries1 on 2008-11-16
yes i would like to use the laptop as a gateway, might just buy a wireless network card so i can leave it doing stuff with out having to have my laptop there.

not sure about the specs of this computerit has no os at the moment, its my parents old one that they were going to thow out so my dad formatted it. 

Seem to remember from using it a few years ago that its a 1.3ghz P4 chip, with 512mb of RAM i think, but could be 256 or 384 maybe. 

graphics i think are on board, probably using shared memory. enough to handle a gui if i wanted, but only really interested in having a command line for the moment. 

main use is going to be big batch jobs involving machine learning experiments written in python. they slow down my laptop too much for me to use it for other things.

---

### Post by iponeverything on 2008-11-16
> **jamesjeffries1 said:**
> I've been using ubuntu and linux for a few years now on home laptops etc. just got hold of an old pc. thought it'd be interesting to set it up with just the command line. just wondered if anyone had any ideas on where to start before i started messing around? maybe ubuntu sever edition? would this include most of the commandline utilities and applications of ubuntu? or would they need installing seperately? 

it doesn't have a wireless card, only ethernet so was thinking of setting up my laptop as a DHCP server to share the internet to it via a hub i picked up ages ago. Is this the best way of doing it without buying a new wireless network card for this computer?


thanks,
James

you can do a strait command line install with Ubuntu server and it does not require many resources.  (of course, running squid, apache, mysql, postgresql, etc. etc. etc. it will)

---

### Post by jamesjeffries1 on 2008-11-16
ok, have got the command line installer running at the moment. 

if im going to buy a wireless card or dongle, does anyone have any comments about the wireless managers available on command line?

or if i dont could anyone suggest how to go about using my ubuntu laptop as a gateway, 

it is connected wirelessly to a router. I could connect the new system either directly through ethernet, or by using an old hub (like a really old version of a switch), which would allow me to install other computers in to the network more easily, but not sure if thats something i will want to do any time soon. I think i need to set up a dhcp server on my laptop, but dont know about how to use this to share the internet

---

### Post by iponeverything on 2008-11-16
Its super easy.

see my post in -- 

[http://ubuntuforums.org/showthread.php?t=983350](http://ubuntuforums.org/showthread.php?t=983350)

you might want to slap on apache and webmin -- just for the fun of it. 
(webmin has a little gui to configure dhcp)

---

### Post by jamesjeffries1 on 2008-11-16
thanks, that explains everything, think ill leave apache and webmin out for now, have no use for the at the moment and easy enough to put in later if i want.
cheers everyone

---

