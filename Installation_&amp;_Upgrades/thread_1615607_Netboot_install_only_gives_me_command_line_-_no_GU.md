---
title: "Netboot install only gives me command line - no GUI"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by greasy19 on 2010-11-07
Hello, I have just installed ubuntu 10.04 via a netboot install.

When my system reboots I only have the command line - no gui. Could someone kindly inform me what command I need to run in order to get a GUI - many thanks.

---

### Post by cherva on 2010-11-07
I'm not sure but you probably need to install the ubuntu-desktop package if you want GNOME.
```
sudo apt-get install ubuntu-desktop
``` 
If you want KDE install the kubuntu-desktop package.
```
sudo apt-get install kubuntu-desktop
```

---

### Post by greasy19 on 2010-11-07
Cheers buddy.

I was so close! I initally installed kubuntu using the command you gave but it was a bit to much for my old laptop.

I tried something similair but instead of 'ubuntu-desktop' I tried 'ubuntu' and 'ubuntu 10.04'

It appears to be installing now, so many thanks.

---

### Post by cherva on 2010-11-07
You can install xubuntu if your machine is old and GNOME and KDE are hard for it.
```
apt-get install xubuntu-desktop
```

---

