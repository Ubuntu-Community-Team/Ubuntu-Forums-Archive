---
title: "Can't make java working under Chromium"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by ewuldoxx on 2010-04-15
I got chromium v5 (44292 build), got chromium ppa added for daily updates, have ubunturestrictedextras package, have java(it works under firefox) but i can't force java to work under Chromium. tried to create plugins folder in /usr/lib/chromium-browser/ and create link to javaplugin file, with ln -s command. it didn't help neither
tried running chrome-browser --enable-plugins %U, about:plugins doesn't show that there's java plugin installed also. don't know what can i do now.

Heard that installing sun-java6-plugin might help, but i get error that such pacakge can't be found.

---

### Post by ewuldoxx on 2010-04-16
I suceeded adding symbolic link into /usr/lib/chromium-browser/plugins/ and in about:plugins java plugin is shown, but it java still doesn't start

---

