---
title: "video resolution"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by amrigo on 2007-02-13
Hi 
I just install ubuntu on a celeron d processor with pcchips p25g motherboard but the screen resolution is not ok it is flickering and many images above the others. 

I try xf86connfig but it ask me i must be superuser, i dont remenber the root password, how can i create a root password without the root password ?

And how can i fix the screen resolution problem  ?  

Thank´s in advance

---

### Post by taurus on 2007-02-13
What video card do you have on that machine?  You probably need to install a driver for it.

And regarding superuser--root, check out this link.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by amrigo on 2007-02-13
it is a onboard agp video card inside the motherboard that is pcchips p25g with via p4m800 northbridge and vt8237 southbridge how can i install a driver for this onboard video ?

---

### Post by taurus on 2007-02-13
```
lspci
```

---

### Post by amrigo on 2007-02-13
I have no access to the computer right now but tomorrow i will post the information returnerd by the lspci command.

Thank´s

---

### Post by amrigo on 2007-02-13
from the command line i must type :
sudo xf86config

it will prompt me for my user password and enable the xf86config to me ?

is there any other command line tool to config the screen resolution ?

---

### Post by taurus on 2007-02-13
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by amrigo on 2007-02-15
thank´s a lot it is working now
best regards

---

