---
title: "update manager"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2011-12-20
im having this error with my update manager everytime i do updates ill load a screenshot to show you, can anyone tell me how to fix it.

---

### Post by matt_symes on 2011-12-20
Hi

Open a terminal and copy and paste

```
grep -lZ "pidgin-developers" /etc/apt/sources.list.d/* | xargs -0 sudo rm
```Enter your password. I will not be echoed to the screen.

Then type

```
sudo apt-get update
```Kind regards

---

### Post by TheRacerX on 2011-12-20
that worked perfectly thank you, im starting to think i should back track to Maverick cause the new Ubuntu is got WAY too many glitches

---

