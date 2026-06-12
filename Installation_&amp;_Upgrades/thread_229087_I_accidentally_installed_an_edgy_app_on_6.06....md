---
title: "I accidentally installed an edgy app on 6.06..."
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by MM23 on 2006-08-03
and it upgraded my libc6 file which has caused a ton of locale bugs. now, I did some thinking, and I thought I could just force libc6 to downgrade back to the old dapper version... but when I do that, synaptic says it's going to remove EVERY SINGLE APPLICATION I HAVE EVER INSTALLED ON MY SYSTEM. I am not kidding. it wants to remove firefox, apt, gaim, zsnes, abiword, alsa, amarok, you name it. it never updated these when I installed that one little thing (just an amarok update, believe it or not... it installed a few xine things and libc, and i already downgraded the amarok/xine stuff back to where it was.) from edgy, fyi---they're all still the breezy versions, so if I could just find a way to replace the edgy version of libc6 with the old breezy version, i think everything would be fine.

how can I do this without reinstalling (not possible) or completely removing everything on my system to do so? why the hell does synaptic want to remove applications which i already know will work fine with the old libc version? is there a way to force it to install just libc?

---

### Post by dtfinch on 2006-08-04
I haven't found myself in this sort of situation, but in Synaptic, whenever more than one version of a package is available, you can try "Package->Force Version". Hopefully, that'll enable you to downgrade to the old one, but I often have strong doubts whenever apt-get is concerned.

---

### Post by Eddie Hung on 2006-08-04
I have exactly the same problem - attempting to downgrade USING force version results in it removing all (I assume) packages that use the library your downgrading - any way round this?

Eddie

---

### Post by MM23 on 2006-08-04
Well, I finally figured it out.

Aptitude is the answer. Make sure your sources.list has ONLY 6.06 repos on it, and type in sudo aptitude install libc6 and it should work. Amazing. Aptitude is much better than apt-get.

---

