---
title: "Compiz on Geforce 4 cards."
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Keeguon on 2008-10-30
Hey,

I think you all know that the drivers for Geforce 4 are currently broken in the mainstream repositories but nVidia just released a Beta driver (96.43.09) so here is how to use it...

First of all download the driver like this:
```

cd Desktop/
mkdir nVidia
cd nVidia/
wget ftp://download.nvidia.com/XFree86/Linux-x86/96.43.09/NVIDIA-Linux-x86-96.43.09-pkg1.run
```

Then switch to the terminal view by pressing CTRL + ALT + F1 and do as follow:
```

sudo /etc/init.d/gdm stop
cd Desktop/nVidia/
sudo sh ./NVIDIA-Linux-x86-96.43.09-pkg1.run
```

Follow the instructions, basically select Yes each time you are prompted to do so. Then the screen will return to the terminal then type in:
```

sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --disable-glx-root-clipping -d 24
sudo /etc/init.d/gdm start
```

Compiz should now work on your computer!

[COLOR="Red"]**_P.S.:_ This is a Beta driver so if you're not sure of what you're doing just do nothing!**[/COLOR]

---

### Post by jerrylamos on 2008-10-30
My experience with my 4 Pc's is COMPIZ is broken by "playing tricks" with graphics hardware and drivers, and when COMPIZ goes it locks the computer up tight.  Frozen.  All just for "eye candy".  And since the pc is "locked up" it can't point the finger at the cause resulting in mysterious hangs.

There's such a pile of different hardware and drivers out there that the compiz philosophy can't work for all of them all of the time.  One of my PC's is to get "fixed" in the release code by putting it on a "blacklist" so compiz will not turn on for it.  Suits me.  Runs faster that way.

Since I don't know anything I'll predict COMPIZ is going to cause a WHOLE PILE of "Ubuntu doesn't work" problems when 8.10 goes out.  Scan over the posts to this forum.  No, I don't have any statistics.  I hope this doesn't give Ubuntu a bad rep.

Rational fix: make COMPIZ OFF BY DEFAULT.

Then at least 8.10 will run and when someone turns on visual effects they'll know where to put the blame.

Cheers, Jerry

---

### Post by Elfy on 2008-10-30
mmm - anyone seen this before?

The driver appears to install ok - but all windows appear the same, the 'scribble' goes when mouse is dragged over and then returns when screenis refreshed.

Not running compiz at all.

---

