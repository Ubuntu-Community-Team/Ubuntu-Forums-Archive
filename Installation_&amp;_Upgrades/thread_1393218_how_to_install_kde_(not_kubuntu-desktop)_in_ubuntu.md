---
title: "how to install kde (not kubuntu-desktop) in ubuntu 9.10?"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Haber_Nir on 2010-01-29
hi i want to ask how to install kde (not kubuntu-desktop) in ubuntu 9.10.
thx ahead
H.N.

---

### Post by Dayofswords on 2010-01-29
```
sudo apt-get install kde
```
i beileve that will work, but you should check around first

---

### Post by Haber_Nir on 2010-01-29
nop its doesn't work
maybe kdebase package?

---

### Post by Haber_Nir on 2010-01-29
anyone?

---

### Post by Ian Clark on 2010-01-30
```
sudo apt-get install kubuntu-desktop
```

---

### Post by cha5on on 2010-02-11
Well, it's possible to install each of the individual packages that belong to KDE, which you can pretty much determine by "aptitude search kde".  However, it's important to keep in mind that KDE is a "software compilation", so to speak.  Is there a specific reason why you don't want to install kubuntu-desktop?

---

### Post by Ian Clark on 2010-02-16
yes, I was trying to see if Kdenlive would function better (i.e., just function) under KDE. But I was wrong. I uninstalled kubuntu-desktop, but all the extra programs remained, and I had to go delete them individually. Not recommended.

---

