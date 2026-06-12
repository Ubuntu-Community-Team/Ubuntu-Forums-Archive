---
title: "Priority (nice) Xorg KArmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scontin on 2009-10-05
Hi folks! :P

Do you know how to change priority value of Xorg in Karmic? I've been used to change it to -10 in Login Window/security, but in Karmic there is no way.

Thanks!!!!

---

### Post by ermeyers on 2009-10-05
man renice

ps a | grep bin/X

sudo renice -10 pid

---

