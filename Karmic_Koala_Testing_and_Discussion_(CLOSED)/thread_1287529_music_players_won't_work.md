---
title: "music players won't work?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by djxstream on 2009-10-10
hi everyone, upgraded my 64 bit jaunty to the beta karmic..and since then Exaile won't load...nothing, i dont even notice a change in process manager.

so i tried reinstalling, same thing

tried amarok, wouldnt install

tried listen, installed, ran, scanned library, but doesnt play any songs...it just stutters for 2 seconds then stops, also reads every mp3 as 59:59 minutes

mp3s play fine in VLC. any thoughts? thanks.

---

### Post by ikt on 2009-10-10
Notice anything being mentioned about pulseaudio or your media players in the syslog?

system > admin > log file viewer.

---

### Post by djxstream on 2009-10-11
ah pulseaudio. forgot about that, i always remove it when i install a new build and removing it did the trick! thanks.

---

