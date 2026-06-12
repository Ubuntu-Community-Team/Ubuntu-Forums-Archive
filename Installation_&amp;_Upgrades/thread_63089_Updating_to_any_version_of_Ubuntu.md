---
title: "Updating to any version of Ubuntu"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by tamarku on 2005-09-06
Alright.  I started using Linspire Linux and jumped from distro to distro.  Now I tried Ubuntu and it is amazing.  All of my peripherals work right out of the box,  and can be mounted and used right out of the box, i.e. HP DVD writer, HP ScanJet 2200c Flatbed scanner and an HP PhotoSmart 8150 printer (if you haven't noticed I like HP peripherals, but not too crazy about their PC's).  Now all I have to try is my Palm Pilot and Iomega zip Drive.  Whew, wayyy too many toys.  

Anyway,  I am most impressed with Ubuntu and have been using it 100%.  I hear talk of the 5.10 Breezy Badger Update coming up so I'm wondering how do these installs take place?  Can I download and ISO and just reload and all my settings will be there? Or will I have to Backup things out of my regular routine and then integrate into Breezy?  If someone could point me to a Link, I searched the forums, or explain this too me so when Breezy is ready I can jump I would greatly appreciate it.  

And, If any of the Ubuntu team sees this I'd like to say keep up the good work.  Like I said this is the first Gnome version of Linux I tried that everything worked right off the bat.

---

### Post by adwait on 2005-09-06
You just need to change the /etc/apt/sources.list file, and change all the references from hoary to breezy. Then run
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Heres a link: 
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

---

### Post by XDevHald on 2005-09-06
First off, thank you for your compliments to the team of breezy badger, and second, please wait until the end September or the middle of October before upgrading to breezy. Beta is still in the air and is running nasty critters that don't like to give you a break from errors.

There is a way without having to use an ISO CD and it's quite simple.

 > 1) sudo gedit /etc/apt/sources.list
2) Change ALL hoary or warty, whichever one you're using and change it to **Breezy**
3) sudo apt-get update
4) sudo apt-get dist-upgrade

Again, please wait, it's a risk not worth taking.

---

### Post by tamarku on 2005-09-06
Really, THANKS!!  This is great.  Do you have any idea when Breezy will be ready for General Release?

---

### Post by tamarku on 2005-09-06
Okay I will wait then.  Thanks for all the great help.

---

### Post by XDevHald on 2005-09-06
[QUOTE=tamarku]Really, THANKS!!  This is great.  Do you have any idea when Breezy will be ready for General Release?[/QUOTE]
 The end of September or mid October is really the best time to upgrade, as posted above, it's not time to do so just yet.

---

### Post by rafakl on 2005-09-06
15 October, also there will be a WAN party!!!

---

