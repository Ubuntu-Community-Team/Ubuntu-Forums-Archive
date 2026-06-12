---
title: "upgrade from hoary to breezy"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by porsher_puddles on 2005-12-05
i'm a newbiei have had hoary running for awhile now and after initial problems just about everything is fine now.This morning i got my breezy cds arrived in the post, i'm on dial up so downloading it was not really an option.
my question is can i install breezy over the top of hoary ie like win 98 upgrade to win me and leave my files intact, or do i have to srub the whole thing and start again, which i'm nervous of as it took me so long to get it right before

---

### Post by aysiu on 2005-12-05
I'm not 100% sure this could work, but you could try ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
``` Delete everything and replace it with this line ```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
``` Then save and ```
sudo apt-get update
sudo apt-get dist-upgrade
```

Translation:
1. Back up your current sources.list just in case this doesn't work.
2. Make the sources.list point to only the Breezy CD and no online sources.
3. Update the sources.list
4. Upgrade to Breezy

---

### Post by funkydan2 on 2005-12-05
or even more easily, pop the CD in, open up a terminal and run
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade

(You can put a # at the start of the line that references the Hoary CDROM if you like since I doubt it will be of any use once you upgrade.)

(Or use apt-get rather than aptitude if you prefer.)

I also remember reading somewhere that the upgrade process is "automatic" if you're running gnome in hoary and you put a breezy install CD in, but I may be dreaming.

---

### Post by cilynx on 2005-12-05
On a test box, I was running hoard and simply put in a breezy CD.  The CD autoran and asked if I wanted to upgrade to breezy.  I said yes.  It did it.  Just a thought...

---

### Post by porsher_puddles on 2005-12-06
i would just like to thank you guys the upgrade went fine, and i still have all my files and everything working !!!. i always print out these sucess stories i have from these forums so i don't ask the same questions again.
by the way breezy looks great !!!

---

### Post by frodon on 2005-12-06
I advice to follow these instructions, it worked nice for most of us here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

---

