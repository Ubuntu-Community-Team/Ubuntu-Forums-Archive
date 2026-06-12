---
title: "Help please, how to uninstall flash player 9?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by fluffy muppet on 2008-03-23
I am totally new to kubuntu (started using it today!). I went on a page to view something and it asked me to install flash player 9, I have installed things on windows no problem so I thought this would be just as easy.
Well I installed it and it now it keeps crashing and I get some message keep coming up! (nspluginviewer and something else?)
I went and had a look around and deleted 2 folders that were to do with it (I'm not even sure where from now, oops) as I couldn't find 'uninstall' anywhere but it hasn't solved the problem and I'm still getting crashes.
Please, please if anyone could baby step me through finding and uninstalling the remainder I would be so grateful. :confused:

---

### Post by PmDematagoda on 2008-03-23
Try:-
```
sudo apt-get remove --purge flashplugin-nonfree
```
to see if you can remove Flash, if you can then try and reinstall it again.

---

### Post by fluffy muppet on 2008-03-23
> **PmDematagoda said:**
> Try:-
```
sudo apt-get remove --purge flashplugin-nonfree
```
to see if you can remove Flash, if you can then try and reinstall it again.
 
Sorry, where am I supposed to enter that? I have no idea about this at all :(

---

### Post by PmDematagoda on 2008-03-23
You are supposed to enter it in a terminal.

You can bring up a terminal through Applications>Accessories>Terminal.

---

### Post by LaRoza on 2008-03-23
Or you could open Synaptic Package Manager, and search for that package and uninstall it from there.

System->Administration->Synaptic Package Manager

---

### Post by fluffy muppet on 2008-03-24
Arrgh, I entered that in the terminal but it said it wasn't installed :mad:
This is the message I am getting on screen frequently : KDE crash handler nspluginviewer crashed and caused signal 11 (SIGSEGV). 
This all started after trying to install flash 9. What can I do please??

---

### Post by PmDematagoda on 2008-03-24
Try and install the Flash plugin again with:-
```
sudo apt-get install flashplugin-nonfree
```

Post any error messages you get.

---

