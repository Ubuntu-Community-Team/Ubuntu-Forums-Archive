---
title: "Nero 7"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Alyce on 2008-06-13
I need some help installing Nero 7. I'm pretty new to Linux, so if someone could talk to me like I'm 5, that'd be super sweet.

---

### Post by jrusso2 on 2008-06-13
Thats a Windows program and its not likely to work on Linux.

I would get the nerolinux if I had to have Nero.

---

### Post by Alyce on 2008-06-13
I heard a rumour that I could type a command line somewhere.... But I don't know where I would get the command line, or where I would type it, so....

---

### Post by jrusso2 on 2008-06-13
You can try installing it with wine

First you have to install Wine

sudo apt-get install wine
 
then you would run wine name.exe with that being the name of nero and see if the install runs.  but I doubt it will work with such a complex program that has a burner and other things that require drivers.

---

### Post by linkunderscore on 2008-06-13
DON'T TRY IT WITH WINE FIRST. (no offense jrusso)

You seem REALLY new to linux and wine can be confusing or frustrating (especially if it doesn't work correct the first time) for a new linux user. 

I'd suggest using one of the linux based Nero-like substitutes. For example you could use gnomebaker by typing (you can copy and paste):
```
sudo apt-get install gnomebaker
```

(BTW you get to the command prompt by going to applications->accessories (ithink)-> Terminal) 

It will prompt you for your password. So type that and then it should download and install it for you. 

You could also try another program called k3b

```
sudo apt-get install k3b
```

Once they are done doing their thing you should be able to find them in the Applications Menu.

---

### Post by Pumalite on 2008-06-13
k3b beats them all.

---

### Post by wpshooter on 2008-06-13
> **Alyce said:**
> I heard a rumour that I could type a command line somewhere.... But I don't know where I would get the command line, or where I would type it, so....

Alyce:

I would suggest that you go to add/remove programs section of Ubuntu and do a search for K3B and install that program.  I am quite sure that it will serve you just as well as NERO did under Windows.

I however, would not recommend the Gnomebaker program that someone else suggested.  I think you would be about as confused try figure out how to use it as you would trying to figure out how to get NERO to run under WINE.

If you need any further help in getting K3B installed and how to use it let us know.

Good luck.

---

### Post by mullens101 on 2008-06-13
I have NeroLinux ... If you're used to Nero, spend the $35 (I think) and get NeroLinux, it's worth every penny and has the exact same interface as you're used to.  K3B requires a bunch of KDE libraries if you're using Gnome ... it's nice but not as good as Nero (IMHO).  Brassero looks to have potential but is not ready for prime time (again, IMHO)

---

### Post by Alyce on 2008-06-17
So.. .here's me learning bit by bit... I don't have to use Nero software with this burner? I can use something already Linux compatible and eaiser to install? How do I get my system to recognize the burner? Someone mentioned that I just need to install the drivers, and I can use any Linux software...

Thanks for all the help, and for not poking fun at my ignorance!!

---

### Post by Pumalite on 2008-06-17
What did you end up using?

---

