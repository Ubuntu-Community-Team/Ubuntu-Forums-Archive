---
title: "ubuntu 9.04 beta and modems"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bob Appleby on 2009-04-11
Having failed to make a modem connection with either 8.04 or 8.10 I decided to try 9.04 beta, with the hope that the newest version would take pity on those of us without broadband. It did not but did say to install Gnome Network Admin. At [http://packages.debian.org/unstable/gnome/gnome-network-admin](http://packages.debian.org/unstable/gnome/gnome-network-admin)
there was a download section, but it listed 12 different architectures. Which one should I download?

Is it obvious how it is to be used once installed, or are there instructions somewhere.

---

### Post by lfaraone on 2009-04-11
Is there some reason you can't use the one in the Jaunty APT repos?

```
sudo apt-get install gnome-network-admin
```

---

### Post by Bob Appleby on 2009-04-11
Is there some reason you can't use the one in the Jaunty APT repos?

I clicked on the reference in Jaunty and it said it was not available.

---

### Post by lfaraone on 2009-04-11
Look, you usually don't install packages by downloading them manually from the internet. 

Open up a terminal and enter the above command, or go to System>Administration>Synaptic Package Manager and wait for it to load. When it does so, go to the search box and search for "gnome-network-admin". Then double-click on the entry to mark it to be installed, and press "apply".

---

### Post by Bob Appleby on 2009-04-12
Thanks for the info. I'll do it next time I get to the local library. The reason I tend to download manually is that I since I can't yet connect to the internet at home with the ubuntu machine, so I have to use the Windows tower.


> **lfaraone said:**
> Look, you usually don't install packages by downloading them manually from the internet. 

Open up a terminal and enter the above command, or go to System>Administration>Synaptic Package Manager and wait for it to load. When it does so, go to the search box and search for "gnome-network-admin". Then double-click on the entry to mark it to be installed, and press "apply".

---

### Post by lfaraone on 2009-04-12
kk, you probably want [http://packages.ubuntu.com/jaunty/i386/gnome-network-admin/download](http://packages.ubuntu.com/jaunty/i386/gnome-network-admin/download)

---

