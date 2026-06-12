---
title: "[SOLVED] Serious problem with upgrading to Ibex"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Safder on 2008-11-01
Hello everyone,

I tried to updrade to 8.10, but i am facing a myriad of problems with this release, first for some reason i couldn't perform all the upgrades, so when I try to run the packet manager, i get this dialog box asking me to run a "partial upgrade" tool, when i try to run that i get an error message saying "An upgrade from intrepid to hardy is not supported with this tool", and this happens every time i try to get some updates using the packet manager, so essentially i am kinna stuck

In addition to this, my compiz doesn't seem to work with Ibex, The title window bar with the "close,minimize,maximize" buttons are missing, so essentially I have to alway do an "Alt f4" to close windows. and also non of the compiz effects work.... I tried to run "compiz-check" after being suggested by someone from one of the threads and this is what i see

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS690M [Radeon X1200 Series]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

So it seems everything works fine with the compiz-check, but i dont know what to do solve the problem

I use an Acer extensa 5420 with and AMD Turion 64 mobile processor and an ATI Radion X1250, Also i can't see any of the updates on GNOME, like tabbed browsing, This has been a disappointing experience for me...so I hope i can switch back to 8.04. Is there an ez way to switch to 8.04 and is there a way to fix to all this problems?

---

### Post by Partyboi2 on 2008-11-03
Open a terminal and try 
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Safder on 2008-11-03
> **Partyboi2 said:**
> Open a terminal and try 
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

so what is this going to do? i.e. what is the end result?

---

### Post by Partyboi2 on 2008-11-03
If your upgrade was interrupted or failed running those commands could possibly finish the upgrade process.

---

### Post by Safder on 2008-11-04
so, I did what you suggested, and i finally got everything working except Firefox, i have no idea why it's acting the way it's acting...any page i go to, it goes gray and it takes forever to load, it's very frustrating... also i had to run those commands quite a few times to install all the upgrades...any suggestions? ? ?

---

### Post by jimv on 2008-11-04
Backup your /home folder and do a fresh install of 8.10.

/my 2 cents.

---

### Post by Safder on 2008-11-04
please..any better suggestions..i spent hours doing the upgrade, it'd be better if i could avoid doing a fresh install

---

### Post by Partyboi2 on 2008-11-04
> **Safder said:**
> so, I did what you suggested, and i finally got everything working except Firefox, i have no idea why it's acting the way it's acting...any page i go to, it goes gray and it takes forever to load, it's very frustrating... also i had to run those commands quite a few times to install all the upgrades...any suggestions? ? ?
There have been a few threads started about firefox running slow and greying out, unfortunately I have know idea on a fix , maybe someone else might know.
Maybe you try using [[COLOR=Blue]swiftfox[/COLOR]]("http://getswiftfox.com/") and seeing if there is any difference.

---

### Post by Safder on 2008-11-04
Anyways thanks for the help with the other stuff...I appreciate it

---

### Post by Safder on 2008-11-04
Ok ppl....i think i got my firefox working now with the latest flash...
and in my case..the problem was flash indeed, I am not sure which version of flash I was running.
The reason, I couldn't find out that, cuz everytime I went to a website using flash, I got the "dimmed" firefox...and i just had to shut down the application, anyways..after going through many suggestions, I figured that I need to remove "flashplugin-nonfree" and install it fresh. Also I am using a 64 bit version of flash, which I couldn't get from the main Adobe website, so instead i stumbled across this tutorial which showed [how to install flash for a 64-bit Ubuntu]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html"). Anyways I want to thank "Partyboy" for helping with a lot of the initial installation.):P:popcorn:

---

