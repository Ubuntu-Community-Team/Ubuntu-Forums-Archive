---
title: "do I need the build-essential package to install a nvidia driver?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by nintendude7cubed on 2008-11-30
This sounds like a whiny question and why shouldn't it be since i've been slaving away at trying to figure this out... I went to nvidia.com and got the linux driver i needed and since it was a .run file i knew to run it in the terminal............. it does nothing. So i think maybe its because its on my external harddrive.. nope.. thats not it... little help here..:confused::confused::confused:

---

### Post by Pumalite on 2008-11-30
You need build-essential:
sudo apt-get update
sudo apt-get install build-essential
Try the Hardware Drivers first.

---

### Post by nintendude7cubed on 2008-11-30
> **Pumalite said:**
> You need build-essential:
sudo apt-get update
sudo apt-get install build-essential
Try the Hardware Drivers first.

i don't mean to be a pain, but is there a way to get this package via windows (ubuntu doesn't have web access (trust me i've tried)) as a .deb file and install it that way?

---

### Post by Pumalite on 2008-11-30
You are going to need a connection to install your driver.

---

### Post by nintendude7cubed on 2008-11-30
> **Pumalite said:**
> You are going to need a connection to install your driver.

i have the .run file so can't i just run it like that and install it? otherwise why would the file even need to exist?

---

### Post by oldos2er on 2008-11-30
> **nintendude7cubed said:**
> i have the .run file so can't i just run it like that and install it? otherwise why would the file even need to exist?

 It may need to download dependencies (e.g. linux header source code) during install.

---

### Post by nintendude7cubed on 2008-12-01
> **oldos2er said:**
> It may need to download dependencies (e.g. linux header source code) during install.

I looked into that on the debian website and it just leads me to more and more dependencies... the buld essential package depends on like 4 files which also depend on a few each where eventually some cycle back to one you already have and its too difficult.. i wonder if it would be easier to ask about the cheapest wireless pci card thats compatible so i can just download stuff from ubuntu to make my live way easier, because i do have plenty of space in my computer as far as pci goes... whats another 10 or 15 bucks on newegg for a great os. Thanx anyway

---

### Post by oldos2er on 2008-12-01
Yes, if you can get an internet connection, you'd be good to go. They don't call it "dependency hell" for nothing.

---

### Post by taurus on 2008-12-01
Isn't the build-essential package and all the dependencies are on the installer CD?  Just insert the CD into the drive and run these commands from a terminal.

```
sudo apt-cdrom add
sudo apt-get update
suod apt-get install build-essential
```

---

### Post by oldos2er on 2008-12-01
build-essential is, but I don't know if linux-headers-* is.

---

