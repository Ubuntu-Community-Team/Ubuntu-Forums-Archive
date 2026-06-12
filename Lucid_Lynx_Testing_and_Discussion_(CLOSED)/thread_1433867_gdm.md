---
title: "gdm"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whitetimer on 2010-03-19
Hi All

Just clean installed Lucid from Alternate and trying to install Nvidia Proprietary drivers.  so when i open a terminal and type 
sudo /etc/init.d/gdm stop i just get a black blank screen, no login prompt....

I have also tried ctrl/alt/f1 and then i get an error about x server not closing ...

Any suggestions ?
:popcorn:

---

### Post by cgb on 2010-03-19
Not sure if I understand the problem fully or not.  If you hit ctrl/alt/F6 does it not give you a terminal session?

---

### Post by Half-Left on 2010-03-19
If sudo gdm stop doesn't work, try this a bit more extreme method. ```
sudo killall Xorg
```

---

### Post by brimondyl on 2010-03-19
I have the same problem I think except I have the VIA Unichrome graphics. My login screen is black, and theres no way to do anything alt f1 f7 none of them help

---

