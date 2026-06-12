---
title: "Install KDE problems"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Nicktu on 2005-11-10
I tried to install KDE and i got an error saying something along the lines of Server X messing up and it can not boot a GUI now. Is there any fix I can do? If not, how can I uninstall KDE and use Gnome again? If there is a way to reinstall KDE let me know. Or if I can fix it.

---

### Post by etc on 2005-11-10
If you want to remove kde just do a 
sudo apt-get remove kubuntu kde kdm kdebase

kdm might be causing the problem

---

### Post by Kyral on 2005-11-10
He installed it with the kde package (which exists I guess)

---

### Post by Manny C on 2005-11-10
Maybe try
```
 sudo dpkg-reconfigure kde* 
```

---

### Post by Nicktu on 2005-11-11
Thanks i'm going to be gone for the weekend. So if anyone could leave me as many options as possible to try when I get home that would be appretiated. I ran an apt-get install kubuntu-desktop and apt-get install ubuntu desktop and neither worked. But I also forgot to tell it to boot as kdm so that could pose a problem. Now whenever i try to boot it goes to a server X error screen and freezes my keyboard up. I can boot in the recovery mode but I do not know what to do from there.

---

