---
title: "Graphics Card Upgrade Advice plz"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by madmak on 2008-09-26
Hia guys im not really too sure when it comes to upgrading hardware as its something iv never done before iv been using ubuntu for about 8 months or there abouts now and have made the complete switch of having an ubuntu only box with no major problems so far because i preffer to use ubuntu than w1nd0ws now but the only downfall is my graphics card drivers and being unable to use the visual effects on ubuntu, i was wondering if anybody could tell me how i can figure out what graphics cards are compatable with my pc, at the moment an lspci displays that iv got

```
VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

but theres no 3d drivers for linux for sis cards as iv read on this forum and on other forums that they dont intend on releasing them to linux distros and only release them to the motherboard companies or something along those lines :)

I wanted to add a card that can atleast handle gif animations and the visual effects on ubuntu without having to open the gif image through a browser like opera or something to see the animation.

To be honest im just kind of sick of the lack of support that sis seems to offer for linux and want to use a diffrent card.

My motherboard is an Asus A7S8X-MX with chipset SiS 741GX and im looking for something not too expensive but that can handle the visual effects in ubuntu but im not too sure how to figure out what cards are compatable if theres actually any because i notice the chipset of this mb is sis aswell so im unsure if that means my board will only accept sis graphics cards or can i use a card like nvidia etc on this board?

Could anyone tell me how to figure out what cards are compatable with my pc or what graphics card would be a good upgrade from this thanks id really appreciate it, im fed up trying to fiddle with the xorg.conf and ending up watching videos that only play half the size in the center of my screen lol.

---

### Post by Pumalite on 2008-09-26
Try to get an Nvidia 7800GT AGP.

---

### Post by madmak on 2008-09-26
judging from your post count mate you seem like a knowlegable guy i can accept advice from lol

will that deffo work with this board and are they expensive in the uk? i dont plan on buying it untill tuesday when i get paid im just lookin for suggestions what would be the best upgrade but tbh i guess anythings gotta be be better than sis and i know from what iv read nvidia are good cards

thanks mate

---

### Post by Pumalite on 2008-09-26
I have one and is great. The only problem you might run into is getting it. Everybody is using PCIExpress by now and 8800 or 9600. If you get it; it should be cheap.

---

### Post by madmak on 2008-09-26
As i say iv got a couple of days to go before i buy a card so that gives me time to find one :)

This was a pc pre-built in a shop about 4 years ago that i got off my cousin last week because he got a laptop, but the thing with sis and there 3d drivers just made me want to bin this card and look for a better supported one.

Thanks for your help mate i really appreciate it, i guess its off to ebay with me now then eh? see if i can get a cheap one lol

thans again mate

---

### Post by Pumalite on 2008-09-26
You are welcome. Good luck!

---

### Post by flainn on 2008-09-26
I just got a 7300GS card (128 MB RAM) new from <a href="http://www.newegg.com/">Newegg</a> for about $30. Works like a charm under Ubuntu 8.04.

---

### Post by neoanderthal on 2008-09-26
> **madmak said:**
> As i say iv got a couple of days to go before i buy a card so that gives me time to find one :)

This was a pc pre-built in a shop about 4 years ago that i got off my cousin last week because he got a laptop, but the thing with sis and there 3d drivers just made me want to bin this card and look for a better supported one.

Thanks for your help mate i really appreciate it, i guess its off to ebay with me now then eh? see if i can get a cheap one lol

thans again mate

do you know if your computer has AGP, PCIe or just regular PCI slots?
A lot of the less-expensive computers available that have integrated graphics don't have any sort of graphics slot available, other than a plain old PCI slot or two.

**edit**
sorry mate, just realized you put your motherboard model up, and I had a look. I'd second the suggestion for 7800, and also offer that ATI Radeon x1950 Pro works very well with compiz, etc.

---

