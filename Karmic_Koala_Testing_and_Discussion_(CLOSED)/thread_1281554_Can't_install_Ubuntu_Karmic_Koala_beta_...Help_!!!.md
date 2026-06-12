---
title: "Can't install Ubuntu Karmic Koala beta ...Help !!!"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by e-Gee on 2009-10-03
First I tried to install ubuntu from live cd but I could not because after booting gives me system out of reange even in safe mode  then I tried the alternate cd but it freezes on starting up partitioning I never have problems with that before (Intrepid, Jaunty) . 



Graphics card is nvidia 7300, Procesor Amd Athlon 3000.

---

### Post by nhasian on 2009-10-03
a few questions for you:

1) when you boot off the liveCD and select "try without making any changes to your hard drive" do you get to a usable desktop?

2) when burning the karmic ISO, did you use the slowest burn speed on a CD?  (do not use dvd media)

3) is the "out of range" message displayed by your monitor?  or in the terminal?

---

### Post by e-Gee on 2009-10-03
1. I tried that and no I can't
2. Yes I always use the slowest speed on cd / dvd creator but I burn it on DVD 
3. Yes "out of range" message is  displayed by my monitor

---

### Post by miegiel on 2009-10-03
No idea what's going wrong, but a *out of range* monitor warning means the display resolution and/or refresh rate is set to high for the monitor.

---

### Post by e-Gee on 2009-10-03
I think that too but I have no idea what to do about it. Tomorow I will borrow another monitor and see if it will be bether.

---

### Post by psyke83 on 2009-10-03
On the CD boot menu, there is an option to start in safe graphics mode. Try that.

---

### Post by e-Gee on 2009-10-04
That I tried first and   "out of range" on screen is all I got ....       I solved the problem by installing fresh copy of Jaunty and then without installing anything I upgarde from Karmic Koala alternate CD after rebooting I got    "out of range" again but from comand line I installed nvidia drivers and add them to xconf.

sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig

And now I have Ubuntu Karmic Koala 9.10 beta and I am very happy  because of that  :guitar:

---

