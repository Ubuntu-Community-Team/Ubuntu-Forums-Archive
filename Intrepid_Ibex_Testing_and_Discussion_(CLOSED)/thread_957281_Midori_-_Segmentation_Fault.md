---
title: "Midori - Segmentation Fault"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by useResa on 2008-10-24
Today I noticed that besides the "A Web Browser" there was an indication of another browser in my Xubuntu Intrepid installation, called Midori (see attachment).

However, when I tried to open youtube.com the browser immediately crashed with a Segmentation Fault. 
When opening it from the terminal, this is the result:
```
rdrijsen@xubuntu-intrepid:~$ midori

** (midori:12317): WARNING **: Unhandled settings property 'zoom-step'
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: NP_Initialize
** Message: NP_Initialize succeeded
Segmentation fault
```
The warning always shows when opening the browser.
The messages start appearing when going to youtube.com and the next thing ... Segmentation Fault.

Does anyone know the reason for this?
Is the browser not capable of opening Flash sites?
TIA

---

### Post by Hairy_Palms on 2008-10-24
the version in the repos is fairly old, midoris under heavy development, i compile the latest git daily with a cron script.

```
git clone git://git.xfce.org/kalikiana/midori
cd midori/
./configure --prefix=/usr && make
sudo make install
cd ../
sudo rm -rf midori/
```

latest git is much improved on the repo version, still has some stability issues though

---

### Post by suoko on 2008-10-24
i always suggest checkinstall:

```
git clone git://git.xfce.org/kalikiana/midori
cd midori/
./configure --prefix=/usr && make
sudo checkinstall
cd ../
sudo rm -rf midori/
```

---

