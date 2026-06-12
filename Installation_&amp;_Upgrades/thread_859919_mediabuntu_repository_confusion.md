---
title: "mediabuntu repository confusion"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by mdsharp24 on 2008-07-15
I've never installed anything from the mediabuntu repository, but tonight I added it to my apt sources to check out skype and right after I ran apt-get update it said I had 14 updates. One of the updates was amarok but I didn't install that via the mediabuntu repository.

Can someone clear up my confusion please.

Michael

---

### Post by bapoumba on 2008-07-15
Moved to "Installation & Upgrades".
Are you using KDE, or have you been testing it?

---

### Post by mc4man on 2008-07-15
Medibuntu has it's own version of amarok which is seen as an upgrade (higher version) over the ubuntu repo version. What the  difference is never payed attention to, the ubuntu version probably has some things not included or disabled. 
You could find the difference by comparing the debian rules file from each repo's amarok source.

---

### Post by mdsharp24 on 2008-07-15
[QUOTE=Are you using KDE, or have you been testing it?[/QUOTE]

I am not using KDE, but I do have many of the libs installed because I prefer some of the KDE apps over Gnome.

mc4man, I guess that does make sense... so if I understand you correctly whether it is wish or not wise I guess is up to the user and makes no difference to the health of the system

Thanks for both of your posts :)

Michael

---

### Post by mc4man on 2008-07-15
> makes no difference to the health of the system No effect on 'health', personally I use the medibuntu. Now i'm curious as to diff. if any, I'll edit back if there is.

Edit; quick glance only this  --with-mp4v2 is in medibuntu ver. > FAAD2 is the fastest ISO AAC audio decoder available

though the readme from the ubuntu version has this to say about libmp4 (faad2)
> optional .....
libmp4v2 (mpeg4ip 1.5 is recommended, faad2 is less reliable)

---

