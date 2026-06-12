---
title: "Installing Printer drivers in Wine"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2011-09-12
I installed the drivers for my printer "canon mg6130" in ubuntu 11.04, but am having trouble with the scanner: it doesn't scan with sane.
Anyway I was wondering, would installing a diff version of the drivers in Wine along with a windows based scanning app, mess things Up?

Are Wine based app handle separately from the one installed in pure Ubuntu, or will thy clash?

If they clash, my only other option is to install Win in virtual box and do the heavy duty scan frond there.

Help

---

### Post by mastablasta on 2011-09-12
you could probably install the drivers but that won't help you.
 
yes everything in wine is basically some sort of virtualisation. it is kept in the wine folder.
 
if printer is supposed to work wiht linux it woul dbe better to find a different programme to scan or set it up propperly.

---

### Post by Kaizoku001 on 2011-09-12
> **mastablasta said:**
> 
 
if printer is supposed to work wiht linux it woul dbe better to find a different programme to scan or set it up propperly.

That actually is what I'm trying to figure out how do do in another post. Unfortunately it has to date, no answers. Shocking I know. But patience is a virtue.:P

---

### Post by demonipuch on 2011-09-12
Instead of using sane, you could use scangearmp (scanner application for Canon multifonction printers)
Howto install scangearmp :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install scangearmp-mg6100series
```

Hope it helped

---

### Post by raja.genupula on 2011-09-12
man actually i read in post that you cant able to run windows drivers through wine . the guy who suggested this point , he said a word that wine not a compiler or something , i didn't remember that word . i am sure about the point .


[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

may be this thing gonna help you a bit

---

### Post by Kaizoku001 on 2011-09-12
@[demonipuch]("http://ubuntuforums.org/member.php?u=1162387")

thank for the reply
unfortunately Scangear makes you name and save each files as you scan them. really annoying when you have 100s of pages to go through. Xsane used to name them automatically. kind of like a batch scanning.

@raja.genupula

Thanks for the link. will check it out tomorrow.

---

### Post by raja.genupula on 2011-09-12
you're welcome

---

