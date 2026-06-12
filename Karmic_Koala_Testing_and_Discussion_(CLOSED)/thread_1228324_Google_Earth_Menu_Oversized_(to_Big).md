---
title: "Google Earth Menu Oversized (to Big)"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kai Summers on 2009-07-31
OK so I have found lots of posts pertaining to small menu fonts with Google Earth. Here's the deal My menus are ridiculously oversized and the window its self spans onto multiple desktops. The version I tried first was the latest 5.x, this is where I first encountered the problem. So I thought I would try the older version 4.3 (I think).

**ubuntu ver:** 9.10

[B][SIZE=3]Actual Screenshots[/SIZE]
How I installed in terminal
[IMG]http://img220.imageshack.us/img220/1489/screenshotaag.png[/IMG]


When I open Google Earth[/B]
[IMG]http://img509.imageshack.us/img509/5815/screenshot2dhi.png[/IMG]

---

### Post by Kai Summers on 2009-08-01
Any ideas anyone??

---

### Post by shp on 2009-08-01
Well the earth is pretty big.

---

### Post by Kai Summers on 2009-08-01
> **shp said:**
> Well the earth is pretty big.

Not very helpful.

---

### Post by shp on 2009-08-01
Sorry couldn't resist.

Anyway my only suggestion would be reinstalling google earth again.

---

### Post by Kai Summers on 2009-08-02
> **shp said:**
> Sorry couldn't resist.

Anyway my only suggestion would be reinstalling google earth again.
I've already tried several times with both the latest version and the previous 4.3 - Cheers though!! 
I'm wondering if anyone can replicate this in Karmic Koala. Or is it something im missing??

---

### Post by fooman on 2009-08-02
try deleting the hidden google earth config file...close google earth if it is opened,   then open a terminal and type or copy/paste the following:

```
rm -rf ~/.googleearth/
```

then try it again.  hope that helps.

---

### Post by Kai Summers on 2009-08-03
> **fooman said:**
> try deleting the hidden google earth config file...close google earth if it is opened,   then open a terminal and type or copy/paste the following:

```
rm -rf ~/.googleearth/
```then try it again.  hope that helps.
Still no joy.:( Cheers for the suggestion!!!

Any other suggestions welcome and will be greatly appreciated. 
I remember GNOME having these oversized text problems years ago... But I don't understand why its only Google Earth, this leads me to believe the fault is with that app.

I had a similar problem with a release of BACKTRACK, the problem was almost identical in that the menus were oversized however this affected all menus within the distro, and only occured when you loaded the desktop. from the main BT terminal window. (This was fixed in a later release)

---

### Post by fooman on 2009-08-05
there is another hidden google config file in: ~/.config/

try this command:

```
rm -rf ~/.config/Google
```

then try google earth again.  hope that helps.

---

### Post by aalhamer on 2009-10-06
Dear All,

I have tried every suggestion and ended up in failure, the solution to my small font problem with google earth 5 was simply to change the settings of my QT4. I know it pissed me off too.

go to your desktop
Follow to and open System> Preferences> QT 4 Settings
click on the font tab and choose the desired size. I run a 1360 resolution 18 aria was perfect.

I hope this solves the problems of many.

---

