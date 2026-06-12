---
title: "sony vaio brightness control on lucid"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by svaens on 2010-03-24
Hi all, and especially sony vaio users. 

Brightness works great on Karmic. 
When I hit Fn+f5, it gets dimmer and the little ubuntu message box pops up in the corner to tell you it is getting dimmer. 
When I hit Fn+f6, it gets brighter (if it isn't as bright as it can be) and the little ubuntu message box pops up in the corner to tell you it is getting brighter.

However, with Lucid, When I hit the 'dimmer' combination, while something happens with the notification, (it shows) both the notification and the actual screen brightness do not change!
Same for when going brighter (thought I cannot tell if that is because it is already as bright as it can be, because I can't make it dimmer first to test that!) 

Anyone else have this problem?

Is this a graphics controller thing ? That is, am I having this problem because of a bug in my in use free open source radeon driver (for my ATI card) ? Or is the code that provides this functionality somewhere else? Will it be fixed when i am able to install the ATI proprietary driver ?

---

### Post by coffeecat on 2010-03-24
What model are you using, because....

> **svaens said:**
> Is this a graphics controller thing ? That is, am I having this problem because of a bug in my in use free open source radeon driver (for my ATI card) ? Or is the code that provides this functionality somewhere else? Will it be fixed when i am able to install the ATI proprietary driver ?

No, I believe it's something to do with Sony's implementation of ACPI. Which varies from model to model and Fn-F5/F6 works just fine in Lucid on my Vaio VGN-NS20S.

You might want to file a bug on Launchpad. And/or, [this thread]("http://ubuntuforums.org/showthread.php?t=465491") is old now and I don't know whether the OP is still working with Sony DSDT tables, but you might want to contact them. Information about your model might be useful to whoever is working on the driver now.

---

### Post by serfcx on 2010-03-24
Works fine on my Vaio PCG-GRS615SP

---

### Post by svaens on 2010-03-24
I've got a soni vaio VGN FW35G
with ATI Mobility Radeon HD 3470.

and like I said, it worked fine for Karmic (which I still use on my 'work' partition). 

So I will do as you suggest... find where I can file a bug, or something.. .

update:

Ok, posted a bug: Bug #546201
The thread you provided the link to seems indeed a bit old, and is archived and closed for commenting now. However, I did find it interesting, and provided the information as part of the bug report. Here's hoping!

---

