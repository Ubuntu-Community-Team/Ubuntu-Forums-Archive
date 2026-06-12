---
title: "Has the font issue been addressed?"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by -Outcast- on 2008-10-02
Has font rendering been addressed and solved in Ibex? 

Font rendering had been my biggest bane in Ubuntu and Linux?

---

### Post by RAOF on 2008-10-02
Yes.  Not only do fonts look crisp and clean, but there's now a keyboard shortcut to make them get up and dance the fandango.

---

### Post by caryb on 2008-10-02
lol! I don't understand the font thing? I had to boot to vista on my laptop (dual boot Kubuntu) & I was shocked how crappy FF was in windowz. Not bad 2 years & only the 2nd time in windows:D


Cary

---

### Post by plun on 2008-10-02
> **RAOF said:**
> Yes.  Not only do fonts look crisp and clean, but there's now a keyboard shortcut to make them get up and dance the fandango.

Yup...:D

If you are doing this the "old fashioned way", what should settings be ?

```
sudo dpkg-reconfigure fontconfig-config

sudo dpkg-reconfigure fontconfig
```


Native, Always, No bitmapped fonts , No or Yes for bitmapped fonts ??


The GUI is also a little unclear with options and details. (prefs>appearance)

If you chooses details you loose your overall setting....


ttf-liberation plays nevertheless Fandango...:D

EDIT

Shortcut...  ??

---

### Post by psyke83 on 2008-10-02
> **plun said:**
> Yup...:D

If you are doing this the "old fashioned way", what should settings be ?

```
sudo dpkg-reconfigure fontconfig-config

sudo dpkg-reconfigure fontconfig
```


Native, Always, No bitmapped fonts , No or Yes for bitmapped fonts ??


The GUI is also a little unclear with options and details. (prefs>appearance)

If you chooses details you loose your overall setting....


ttf-liberation plays nevertheless Fandango...:D

EDIT

Shortcut...  ??

I don't think it's necessary to touch the fontconfig-config configuration anymore. All you need do is the enable "Subpixel smoothing (LCDs)" preset in Gnome Appearance Properties (equivalent to subpixel smoothing & slight hinting), which will use the "improved" rendering that was originally based on David Turner's patches.

---

### Post by Daelyn on 2008-10-02
> **raof said:**
> yes.  Not only do fonts look crisp and clean, but there's now a keyboard shortcut to make them get up and dance the fandango.

lmao!

---

### Post by plun on 2008-10-02
> **psyke83 said:**
> I don't think it's necessary to touch the fontconfig-config configuration anymore. All you need do is the enable "Subpixel smoothing (LCDs)" preset in Gnome Appearance Properties (equivalent to subpixel smoothing & slight hinting), which will use the "improved" rendering that was originally based on David Turner's patches.

I have been using this since "mlind" started his threads. (and his
secret repo :D)

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670) 

Something is "corrupting" the screen now and I knows that "Ubulette" has changed Cairo a couple of times.

Also if you are using the GUI you disables all functions if you checks details. (GUI checkboxes). 

ttf-liberation has always been perfect for me and my screen.

---

### Post by ktp on 2008-10-02
Font rendering is nice now...one of the first things I notice when I upgraded.

---

### Post by MacUntu on 2008-10-02
Why do I never have these problems? Dammit!

---

### Post by rbmorse on 2008-10-02
That's OK. I'm having a new one with the beta...something in is causing printed text on my LaserJet (postscript) to have certain characters render as boxes.  Graphics are OK, and output from things like OpenOffice or the GIMP work fine, but text from the text editor and similar applications are affected. 

All this is OK in 8,04, but I haven't localized the fault in 8.10, yet.

---

### Post by klange on 2008-10-02
> **RAOF said:**
> Yes.  Not only do fonts look crisp and clean, but there's now a keyboard shortcut to make them get up and dance the fandango.
You know, I'm sitting here and I wonder: Is it possible for a patch to be made to pango to do something of this sort?

---

