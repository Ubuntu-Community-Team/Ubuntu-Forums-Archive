---
title: "Mono upgrades"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by NeoFax on 2009-03-06
For about a week now I have not been able to update mono programs thru apt.  Dpkg says removing libqyoto**-cil and just stays there forever.  So I have to kill dpkg and run dpkg --configure -a or apt-get -f install to finish the rest of the upgrades.  How do I fix mono to work properly?

---

### Post by gnomeuser on 2009-03-06
Is there a bug open for this?

---

### Post by nystire on 2009-03-06
Try running 'sudo apt-get clean' and then retry the update. Maybe the mono install files were corrupted in some way.

---

### Post by directhex on 2009-03-07
I'll set up a Jaunty VM to try and confirm, though I've seen nothing like this

---

### Post by directhex on 2009-03-07
Sorry, unreproducible

---

