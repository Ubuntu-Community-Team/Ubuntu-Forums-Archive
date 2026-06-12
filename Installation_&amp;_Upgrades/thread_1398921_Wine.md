---
title: "Wine"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by infla on 2010-02-05
Hello,

I've installed Wine long time ago. but i had to update it to instal a Program (a friend of me said that i could only install that program with the last version of wine). but I couldn't update it. then I found something on a website to update it. i've done that, but now there is something wrong with my wine. I can't install or open programs anymore with wine (my wine isn't installed anymore  :O.

So i tried to reinstall it, but I can't install it anymore. so I went to /usr/share to delete the map Wine, but I'm not allowed to do it.. so i was trying it in Terminal. but I think that I use the wrong Terminal Code. 

any ideas?

---

### Post by NikoC on 2010-02-05
Wrong code to uninstall wine? Can 't you just type the following in a terminal:

sudo apt-get remove --purge wine

This will completely remove your wine installation and then:

sudo apt-get install wine

This will re-install.

Good luck!

ps. There is a special wine support section on this forum!

---

### Post by infla on 2010-02-05
> **NikoC said:**
> Wrong code to uninstall wine? Can 't you just type the following in a terminal:

sudo apt-get remove --purge wine

This will completely remove your wine installation and then:

sudo apt-get install wine

This will re-install.

Good luck!

ps. There is a special wine support section on this forum!


well thanks, i'll try it now.

---

### Post by infla on 2010-02-05
> **infla said:**
> well thanks, i'll try it now.

okay, it does't work.

any other tips? or shall i make a thread in the wine support forum?

---

### Post by saif_held on 2010-02-05
> **infla said:**
> okay, it does't work.

any other tips? or shall i make a thread in the wine support forum?

What was the output on the terminal when you tried it?

---

### Post by infla on 2010-02-05
> **saif_held said:**
> What was the output on the terminal when you tried it?

Hello,

I use a Dutch Version of Ubuntu. this is the result:

 brecht@brecht-laptop:~$ sudo apt-get remove --purge wine
µ[sudo] password for brecht: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Pakket wine is niet geïnstalleerd, en wordt dus niet verwijderd
De volgende pakketten zijn automatisch geïnstalleerd en zijn niet langer nodig:
  wine-gecko wine1.2-gecko
U kunt deze verwijderen via 'apt-get autoremove'.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 4 niet opgewaardeerd.
brecht@brecht-laptop:~$ sudo apt-get install wine
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie 
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  wine: Vereisten: wine1.2 maar het zal niet geïnstalleerd worden
E: Niet-werkende pakketten:


just to say, Wine isn't installed anymore.. but it was before all this, but I can't instal wine again. that's the problem.. i was thinking about deleting the map Wine, that map is still in /usr/share

---

### Post by saif_held on 2010-02-05
Then I would recommend that you check Wine support forum before doing that. Maybe there's a better solution.

I actually could translate part of the text since I speak German. They're both indeed very similar.

---

### Post by infla on 2010-02-05
> **saif_held said:**
> Then I would recommend that you check Wine support forum before doing that. Maybe there's a better solution.

I actually could translate part of the text since I speak German. They're both indeed very similar.

yes I was looking to set my Ubuntu to english to copy paste the english version of that text in here, but I can't find the language settings.

however, thanks for your responds, i'll make a thread on the Wine forum.

---

