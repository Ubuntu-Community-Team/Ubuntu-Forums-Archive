---
title: "Icon and Menu background colo(u)rs"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-03-20
I have noticed an icon issue continuing on from Karmic with some of the backgrounds on the panels not matching the theme. The icons in question are usually firestarter and banshee in my case, but many others seem to be also affected (see bugs below). While the drop down text on icons like skype are unreadable since the text font colour almost matches the theme colour.

Now this only seems to occur with the ambiance and radiance themes and just ruins the whole appearance. Also the contrast on the GDM login screen does not seem right with white font on a light background.

For the icon background I think [Bug #403135]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135") seems to cover the problem and also lists all the other affected icon buttons.

Regarding GDM I found [Bug #532844]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/532844")

For a LTS it would be great to see these little things nailed down just to give us that polished look it deserves. So if any of the above affect you maybe hit the 'affect you' button :)

---

### Post by victor9098 on 2010-03-27
The problem with the drop-down menus on Skype have been fixed in the last few days with an update, but the icon menus still seem inconsistent. Have attached a pic of an example. Hopefully they will nail this down too!

---

### Post by castrojo on 2010-03-27
Banshee is fixed but won't be uploaded until next week or so when 1.6 final goes in.

---

### Post by victor9098 on 2010-03-27
> **whiprush said:**
> Banshee is fixed but won't be uploaded until next week or so when 1.6 final goes in.

I was under the impression that this was a theme issue as it only happens under the default themes, a few other icons have the same problem (Firestarter for example), but other themes do not have this problem.

---

### Post by gotsanity on 2010-04-25
> **whiprush said:**
> Banshee is fixed but won't be uploaded until next week or so when 1.6 final goes in.

This still hasnt been fixed, do we know if it is gonna be fixed by release?

---

### Post by cariboo on 2010-04-25
I would suggest you stop using firestarter, as it hasn't been updated since 2005, the maintainer only adds bug fixes. Ufw, or if you need a gui Gufw is now the preferred way to set firewall rules.

---

### Post by gotsanity on 2010-04-25
I was refering to banshee in particular but I will keep that in mind.

---

### Post by MacUntu on 2010-04-25
You can install banshee-extension-appindicator. This fixes the background issue but unfortunately you'll lose some functionality (no skipping within tracks, no repeat/shuffle/rating).

---

### Post by victor9098 on 2010-04-25
> **cariboo907 said:**
> I would suggest you stop using firestarter, as it hasn't been updated since 2005, the maintainer only adds bug fixes. Ufw, or if you need a gui Gufw is now the preferred way to set firewall rules.

Not to go too much off the thread topic, but I thought that all the GUI options (gufw or firestarter) all use the same iptables? I like the information provided and easy to use GUI of firestarter, that is why I have choosen it over gufw.

MacUntu, yes I have tried using the banshee indicator extension, but whenever I close banshee it does not minimise to the tray, closes the whole application. Which is more an annoyance then anything.

Thanks for the suggestions!

---

### Post by gotsanity on 2010-04-25
> **victor9098 said:**
> 
MacUntu, yes I have tried using the banshee indicator extension, but whenever I close banshee it does not minimise to the tray, closes the whole application. Which is more an annoyance then anything.

Thanks for the suggestions!

Yeah, I was having the same issue. I am curious how hard it would be just to overwrite the icon image with a modified one. Its a little bit of a brutish work around but it could work. I'll look into it.

---

