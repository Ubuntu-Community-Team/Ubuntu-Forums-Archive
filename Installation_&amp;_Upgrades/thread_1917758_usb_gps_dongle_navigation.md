---
title: "usb gps dongle navigation"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by Martinizhr on 2012-01-30
Hy, can anyone help me with installing ANY navigation system on my laptop. I bought usb dongle gt-730f [http://www.canmore.com.tw/productshow.php?selectub=&product_number=11&secondkidnumber=1&secondkidname=GPS%20USB%20Dongle&mainkidnumber=1&mainkidname=](http://www.canmore.com.tw/productshow.php?selectub=&product_number=11&secondkidnumber=1&secondkidname=GPS%20USB%20Dongle&mainkidnumber=1&mainkidname=)

and I learned how to connect to it (using gpsd) but I can't find any good program to run it on. I have tried 
navi(instalation folder is empty and can't find navi.xml....)
foxrotGPS(works but I can't make route...)
and others...
I have problem of finding program to work in witch I can set a route and that it is navigating me in the city. Like garmin, but on laptop. Does anyone know anything that can help me please, It is making me nuts for over a week.

p.s. I'm using Ubuntu 11.10

---

### Post by Martinizhr on 2012-01-30
bump :)

---

### Post by clevetbs on 2012-07-10
I used virtual box installed windows and use iguiance gps software to navigate, I myself cant find a good gps program under linux. but there are cars out there with backend linux gps navigation system. i dont see why they cant port it for us lol.

---

### Post by Cheesehead on 2012-07-10
> **Martinizhr said:**
> Hy, can anyone help me with installing ANY navigation system on my laptop.

Have you looked in the Software Center?

```
$ apt-cache search gps | grep navig
**gpsdrive - Car navigation system**
gpsdrive-data - Car navigation system
**navit - Car navigation system with routing engine**
navit-data - Car navigation system with routing engine - data files
navit-graphics-gtk-drawing-area - Car navigation system with routing engine - GTK+ graphic plugin
navit-graphics-qt-qpainter - Car navigation system with routing engine - Qt graphic plugin
navit-gui-gtk - Car navigation system with routing engine - GTK+ GUI
navit-gui-internal - Car navigation system with routing engine - internal GUI
```

I found two in the Ubuntu repos: gpsdrive and navit.

---

