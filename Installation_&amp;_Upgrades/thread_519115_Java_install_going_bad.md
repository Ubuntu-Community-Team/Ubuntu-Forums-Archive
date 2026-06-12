---
title: "Java install going bad"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Selage on 2007-08-06
Hello,

Java not helping me...

The things is, I'm installing Ubuntu on a laptop, all is good.
I was trying to install some new software from the ubuntu repos.
Hitting apply, first thing popping up, dkpg found bad something in packages

going to synaptec packetmanager, saying same thing
fix it with " sudo dpkg --configure -a"

acces to synaptic back, saying something is broken.

Found out java 5 is broken.

" Please reinstall", but i cant becuz all option i get from synaptic are remove and remove complete.

So Java 5 is blocking my install capabilities

Tried installing java 6 accordin to the java site, nothing working

Please help me fix this.

Thx

---

### Post by Pumalite on 2007-08-06
sudo dpkg --remove --force-remove-<packagename>

---

### Post by Selage on 2007-08-07
how can you see whats the exact package name?

Thanks

---

### Post by Selage on 2007-08-07
Also,

Java was never installed with synaptic.

i've had to install java for mozilla, and then things went bad. can you still remove that this way?

---

