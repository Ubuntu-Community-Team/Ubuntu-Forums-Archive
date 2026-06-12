---
title: "Laptop Keyboard/Mouse broken after upgrade"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lexaken on 2008-10-11
I recently upgraded my kernel (not sure exactly which one but the problem is persistent throughout the 3 on my bootloader) and now when Ubuntu boots to the login screen, I cannot type or use my trackpoint.

Keyboard works fine selecting during the bootloader.

Laptop: Lenovo T61
Using Ubuntu Intrepid, updated daily

I have tried using external mouse and keyboard but to no avail. The mouse worked for a bit but no longer. Keyboard/Mouse are both powered but not allowing input

---

### Post by Nysomin on 2008-10-11
I just ran into the same problem, but I don't have a laptop.  I've got a Logitech wireless USB keyboard and mouse set.  I have a few extra keyboards and mice, but I have yet to try them.  Funny thing, in the resuce mode the keyboard works, but once I hit the gdm I get no response.

---

### Post by lexaken on 2008-10-11
Yeah, rescue mode works fine for me as well

---

### Post by wgrant on 2008-10-11
Ensure that ubuntu-desktop and xserver-xorg-input-all are installed, and remember to watch which packages are being removed next time.

---

### Post by Nysomin on 2008-10-11
Well, I know that ubuntu-desktop was installed because that was one of the packages I was re-installing(another package had removed it, I forget why though)  and I'm not positive in xserver-input was installed, but I'm sure it wasn't removed.  Anyway, I had decided to download and do a clean install of the daily build and that has the same problem too.

Side note:  also when dpkg removed "obsolete" packages it removed cairo-dock for no real reason.........  not cool.

---

### Post by lexaken on 2008-10-11
Not exactly sure how I would go about doing that now.

---

### Post by Nysomin on 2008-10-11
easiest way is to use the recovery mode, drop to the root shell and apt-get them.
```

apt-get install ubuntu-desktop
and
apt-get install xserver-xorg-input-all

```if I'm not mistaken.

I'll try it myselft once I re-install ubuntu(decide to give openSuSE another shot, but it didn't work, again)

---

### Post by lexaken on 2008-10-13
I am unable to resolve the update servers in the root shell

Should I be connected via hardline for this? Im currently on wireless

---

### Post by lexaken on 2008-10-14
I attempted to update via wired connection but that failed as well

Subsequently, I tried to do a fresh install but the cd did not detect my network hardware (fresh daily cd). There seems to be a pretty big bug here no?

---

