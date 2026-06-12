---
title: "downgrade ubuntu 13.04"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by mrkaplan on 2013-09-29
hello
I am not a big fan of Ubuntu 13.04 GUI . On top of that ;  it is not able to run my scanner . 
I ve seen most users have no drivers problem with 12.04 releases and older.  So, im considering downgrading to a system that runs Mate desktop or similar ( classic looking ) -  and hopefully will run printer and scanner .  
need advice on : 
- can i downgrade ubuntu, or should i completely delete  and overwrite it  
- what distribution would be suited : Im not sure which ones run Mate desktop
thanks

---

### Post by sudodus on 2013-09-29
You cannot go from a newer version to an older one (or it is extremely difficult), so it is better to backup your personal data and reinstall instead of trying that.

I would also say that ***Ubuntu 12.04 LTS is well polished and debugged***, and if you do not need drivers for very new hardware, it is the best option for a production platform (a computer that should work in a reliable way).

But there are also other GUIs or ***desktop environments***, that might serve you well in 13.04. You can install them and select the one you like at the log in screen (click the round symbol near where you enter the password if you have standard Ubuntu).

```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop
```

You can also download the corresponding iso file, make a boot CD/DVD/USB drive and try it live without installing anything.

---

### Post by Gyokuro on 2013-09-29
Downgrading is not supported and you are much faster to install 12.04 and it's a LTS release so you can try 13.10 after it's release and check whether your problems got solved or not and stick with it until the next LTS 14.04 get released. However maybe you should fill out bug reports so that your problems get fixed in 13.04? I do not recommend you anything but the best will be that you try Mint and check whether you like it but as Mint is Ubuntu based and comes with Cinnamon and the last Mint is based on Ubuntu 13.04 you should get your problem with this release too - Minit 13 is based on Ubuntu 12.04 (LTS release) and maybe you should try this release. However at the moment I will not recommend LMDE (Linux Mint Debian Edition) as it breaks sometimes and in case you do not like to tinker with a distribution and are not fit with Debian it's the wrong distribution for you (IMHO).

---

### Post by mrkaplan on 2013-09-29
i finally understood how to switch desktop in Ubuntu . so i think i'll try ubuntu 12.04 and see if it fixes my issues . I like the functionalities of ubuntu w unity desktop  ( gnome 3 in my welcome screen)  :  launch bar and Ubuntu menu are quite convenient.  just think graphics is a bit too high contrast, specially the dark border of windows .

---

