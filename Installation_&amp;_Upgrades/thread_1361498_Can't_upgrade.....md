---
title: "Can't upgrade...."
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by medicalystoned on 2009-12-22
I can not upgrade from Intrepid to Jaunty so that I can go to Karmic. Adept just won't do it. I tried from terminal and get this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

so i do and get this

dpkg: requested operation requires superuser privilege


 I admittedly have not touched my linux machines and i am alittle lost. any help would be great. Thanks in advance..---- peace

---

### Post by medicalystoned on 2009-12-22
sorry, i forgot to add.... i know i could just do a clean install with a new disc.... it is just more fun to learn how to do things from terminal.... thanx again----- peace

---

### Post by bumanie on 2009-12-22
In terminal > sudo dpkg --configure -a

---

### Post by medicalystoned on 2009-12-22
> **bumanie said:**
> In terminal

that gives me this...

dpkg: dependency problems prevent configuration of gwenview:
 gwenview depends on libkipi6; however:
  Package libkipi6 is not installed.
dpkg: error processing gwenview (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gwenview


am i wasting my time? should i just do a clean install?

---

### Post by sanderj on 2009-12-22
In my experience, upgrading to a new distro version is a tricky thing. Upgrading twice is even more tricky.

Anwyay: I would advice to use the GUI: System -> Administration -> Update Manager. Fist update within the current version. If that workds OK, do the distro upgrade via the same GUI.

HTH

---

### Post by medicalystoned on 2009-12-22
bump...... seeing if today brings any more advice....... thank you in advance.

---

### Post by sanderj on 2009-12-23
> **medicalystoned said:**
> bump...... seeing if today brings any more advice....... thank you in advance.

Bump? More advice? Have you done what I advised you to do?

I will now unsubscribe.

---

