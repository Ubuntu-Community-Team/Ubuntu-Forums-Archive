---
title: "Finding out exactly what packages is installed"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by b0bby on 2006-07-06
Hello =)
Is there any way to find out exactly what packages I'v installed, with apt, on my box?

---

### Post by John.Michael.Kane on 2006-07-06
apt-cache should pull up the commands needed for what you want to do.

---

### Post by ajgreeny on 2006-07-06
Open up synaptic and go to File/History.  A dated list will appear of all you've installed using apt or synaptic.  Go to Settings/Preferences-Files tab and you can set how long you want the history to remain; the deafult seems to be for ever, so unless you have changed it yourself you should have everything since you installed.

---

### Post by aysiu on 2006-07-06
```
dpkg -l
```

---

### Post by John.Michael.Kane on 2006-07-06
aysiu thanks for the correction. I forgot about that code it's not often i have to look up what i install..

---

