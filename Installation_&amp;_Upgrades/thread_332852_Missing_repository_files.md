---
title: "Missing repository files"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by fjr0122 on 2007-01-06
I am trying to backup my ubuntu system, I have had multiple hardware problems and random shutdowns and I fear them happening again. When these happened I thought my system was toast and several times I booted and the home folder and all installed programs were gone (the first two times the desktop wouldnt come up at all).  But this last time magically, miraculously everything was in place when i booted (desktop home folder files everything). I want to be sure I dont ever have to re-find+re-install all the hundreds of programs I have chosen.

Anyways, the going tool for doing what I want to do seems to be aptoncd which I installed and tried to use, but it only reports 130 files installed and will happily back those up. But synaptic reports 1563 packages installed. So then I checked the /var/cache/apt/archives directory and there are only 130 files listed. 

Does anyone know how to get the other 1400 packages back into that directory so i can make a proper backup?

Btw, I'm using edgy and generally prefer to do things in the gui, though i'm not afraid of the CLI I just tend to not entirely understand whats happening....

---

### Post by bapoumba on 2007-01-06
Hi,
Not exactly your question, but :
```
sudo dpkg --get-selections >my_packages
``` 
(or any other file name) will give you a list of all packages installed. To reinstall them :
```
sudo dpkg --set-selections <my_packages
sudo apt-get update
sudo apt-get dselect-upgrade

```
You need to be connected to internet, through. The packages will be downloaded again, on a newly installed system for ex, or on a cloned intallation.

---

### Post by fjr0122 on 2007-01-06
I did all that, and it didnt get the caches back...

---

### Post by bapoumba on 2007-01-06
Well, the first command puts in a file all your installed packages. The second one is to use it on a newly installed system, or on another computer, where you want to install the exactly same packages.

---

### Post by fjr0122 on 2007-01-06
Thanks :)

Unless someone comes up with something better (like a way to force synaptic to download the packages again) I guess that will have to do.

---

