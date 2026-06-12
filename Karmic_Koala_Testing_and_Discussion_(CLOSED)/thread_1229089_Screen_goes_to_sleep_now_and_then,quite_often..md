---
title: "Screen goes to sleep now and then,quite often."
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-08-01
Hi folks

Anyone else seen this problem?

As if the screensaver is going to activate.

---

### Post by AlanR8 on 2009-08-01
If you mean the screen just goes black for a second or so every now and then.......yes!

---

### Post by DougieFresh4U on 2009-08-01
Does this seem like your problem?

[http://ubuntuforums.org/showthread.php?t=1156928](http://ubuntuforums.org/showthread.php?t=1156928)

---

### Post by dinxter on 2009-08-01
not sure if this is the problem you are having, but recently an update to DeviceKit-power unset the power management values in system->preferences->power management. if those values are unset then re-choosing your preferences should cure the problem

---

### Post by rajeev1204 on 2009-08-01
> **AlanR8 said:**
> If you mean the screen just goes black for a second or so every now and then.......yes!


Yes exactly !

And the system is not idle when this happens, iam surfing or doing something.Its strange.It happens for a second or two.Then comes back to normal.

---

### Post by gnomeuser on 2009-08-01
[http://blogs.gnome.org/hughsie/2009/07/30/accidental-blanking-and-gnome-power-manager/](http://blogs.gnome.org/hughsie/2009/07/30/accidental-blanking-and-gnome-power-manager/)

---

### Post by kingborel on 2009-08-01
> **rajeev1204 said:**
> Yes exactly !

And the system is not idle when this happens, iam surfing or doing something.Its strange.It happens for a second or two.Then comes back to normal.

Ok, good, so it's not just me that it's happening to :-?

---

### Post by ktp on 2009-08-01
> **kingborel said:**
> Ok, good, so it's not just me that it's happening to :-?

I thought I was going crazy...I guess not.

---

### Post by autocrosser on 2009-08-01
Yes--It's flat annoying when it happens--I can be doing almost anything & the screen will black for 2~5 seconds......I had thought it was the nVidia driver until i started hearing people with other hardware with it too.....Hope that Gnome gets it sorted out soon.....

---

### Post by kyleabaker on 2009-08-01
This has been happening on mine as well, but very rarely.

---

### Post by psyke83 on 2009-08-02
> **gnomeuser said:**
> [http://blogs.gnome.org/hughsie/2009/07/30/accidental-blanking-and-gnome-power-manager/](http://blogs.gnome.org/hughsie/2009/07/30/accidental-blanking-and-gnome-power-manager/)

This may also be the result of pipe underruns for users of Intel graphics chipsets. I don't have any bug reports handy (I lost my bookmarks), but a search of bugs.freedesktop.org will show some results.

---

### Post by JohnJackson on 2009-08-14
[http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/]("http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/")

---

### Post by taavikko on 2009-08-14
This might also be: [https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/397839](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/397839)

---

### Post by JohnJackson on 2009-08-17
A description of the problem if anyone is interested: [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/]("http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/")

---

### Post by rajeev1204 on 2009-09-17
THis is still happening for me ,not as before,but when i quit playing a game for example.

Anyone else?

---

