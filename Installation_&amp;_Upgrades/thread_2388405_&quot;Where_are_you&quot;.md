---
title: "&quot;Where are you?&quot;"
date: 2018-04-02
forum: Installation &amp; Upgrades
---

### Post by polyprobatos on 2018-04-02
I just installed (L)ubuntu on another machine, but was unhappy with the encrypted home folder. So, I installed it again, since it only takes about 10 minutes for Lubuntu, on a relatively modern machine.

However, on my first install, when I was at the "Where are you?" screen, I would type the name of my home city, it would recognise it, and I could select it. However, upon the second install, it would not recognise any place name, save for capital cities. Does anyone know why this is, or whether I can change my location after installation, to select my home city again?

It's a minor issue, but it bugs me.

[I]

Edit: I just reïnstalled a second time, and this time I could in fact choose my home city. It's still weird though.[/I]

---

### Post by TheFu on 2018-04-02
It is about choosing a time zone.  

My home (Squidbilliland) isn't anywhere near any cities in the list, but in the interest of getting the correct timezone set, I use New York City.

You can change the TZ later, with an environment variable (there might be a GUI) too.  When I travel, I usually set the TZ to which  ever is correct for the local city. There are reasons.

There is a tool -** tzselect** which can be used for this too, though it might only deal with console settings, it seems to work for my X11 stuff too.

---

### Post by polyprobatos on 2018-04-02
Yeah, but the TZ selector also only list capital cities, and like I said, after a third install, the installer did allow me to select my home city. So either that second install was completely bugged and denied part of the list both for the installer and the after-install TZ setting, or those two are not 100% the same thing.

> **TheFu said:**
> My home (Squidbilliland).

Beer came through my nose,..

No offense, seriously. Is 'Squidbilliland' an actual place? Also, is your neighbour Patrick Star?

---

### Post by TheFu on 2018-04-02
> **polyprobatos said:**
> Yeah, but the TZ selector also only list capital cities, and like I said, after a third install, the installer did allow me to select my home city. So either that second install was completely bugged and denied part of the list both for the installer and the after-install TZ setting, or those two are not 100% the same thing.



Beer came through my nose,..

No offense, seriously. Is 'Squidbilliland' an actual place? Also, is your neighbour Patrick Star?
Dan Halen [https://en.wikipedia.org/wiki/Dan_halen](https://en.wikipedia.org/wiki/Dan_halen)  is my neighbor. Right idea, wrong reference.  ;)  Fortunately, distances here are big enough that I don't have to smell anything coming from that direction.

NYC isn't a capitol.  My state capitol isn't listed either. Could you have installed different versions?  TZ information is constantly changing so updates happen all the time. I recall a few years ago that the guys maintaining these things for the entire world were being sued by a reference book over facts. [https://www.wired.com/2011/10/time-zone-data-lawsuit/](https://www.wired.com/2011/10/time-zone-data-lawsuit/) Is that possible?

---

### Post by polyprobatos on 2018-04-03
> **TheFu said:**
> NYC isn't a capitol.  My state capitol isn't listed either. Could you have installed different versions?

Ah no,.. Albany isn't it? Maybe I should have just said "big cities", or something along that line.

Nope, they were the same version, coming from the same install CD I burned the day before.

---

