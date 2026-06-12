---
title: "XMMS without sound after upgrade"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by jan on 2006-06-08
Upgrade from Flight 5 to Dapper final - heh, sometimes (somehow it is not regular) i get this if i want to play mp3:

"Couldnt open audio: ..." dialog. Wtf is that? I knew i should stick with Flight 5!!! ](*,)

---

### Post by jan on 2006-06-09
PLEASE HELLLLP!!!! :confused: :confused: :confused:

---

### Post by jan on 2006-06-21
Hm a system update solved the problem somehow...

---

### Post by pale_ipis on 2006-06-21
probably because xmms (1.2, if thats the version u use) uses an older version of libssl, found this out after doing dpkg -i xmms***.deb on dapper

---

