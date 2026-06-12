---
title: "upgraiding to new versions"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by nicomazi on 2005-10-05
hi all,
is it possible to upgraid from ubuntu 5.04 to 5.1 using just ubuntu update tool?
and one more quiestion: if i install ubuntu 5.1 do i have to install kubuntu 5.1 separetly in order to have KDE?

thanks in advance

PS i'm new with all this, so go easy on me

---

### Post by yage on 2005-10-05
Hi, i don't think this is possible. But it can be done if you change the resp under /etc/apt/sources.list to breezy instead of warty

sudo gedit /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by manicka on 2005-10-05
It's not possible. Just change your sources.list as suggested from hoary to breezy (i.e. wherever you see the word hoary in the list change it to breezy) and follow the commands above.

Good luck!

---

### Post by nicomazi on 2005-10-05
thank you for replying so quick, but could you also elaborate on second quiestion?
thnx

---

### Post by SilentCacophony on 2005-10-05
You can install the kubuntu-desktop package via synaptic or

sudo apt-get install kubuntu-desktop

but some people find it's a bit messy afterwards (conflicting config files and such), and takes a lot more space having both.

---

### Post by floyd27 on 2005-10-05
sorry to but in ..
but.
what is the ideal way to install kde then..?

---

### Post by manicka on 2005-10-05
[QUOTE=floyd27]sorry to but in ..
but.
what is the ideal way to install kde then..?[/QUOTE]

sudo apt-get install kubuntu-desktop

or if you just want a kde machine download a kubuntu iso

---

