---
title: "Desktp background and icons not showing"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-10-29
Hi!

Since I upgraded my work PC to Karmic yesterday, Nautilus is no longer showing the desktop background and icons. Nautilus is running and, for example, the desktop contextual menu is showing when I right-click the desktop, but the desktop itself is solid black and no icons are showing (there are some files on the desktop).

I looked in gconf, and apps/nautilus/preferences/show_desktop is set to true.

I've tested Karmic on my personal desktop since alpha1, and on my laptop since about alpha3, and I didn't have anything like that.

Any suggestion on what to look for to fix this?

---

### Post by tawmas on 2009-10-29
Turns out the password prompt for unlocking the desktop isn't showing either. I can unlock the screen by typing the password and pressing return, and the mouse pointer turns to an I-beam when hovering the spot where the input widget should show.

---

### Post by Aero-Z on 2009-10-29
I've had similar problem. Only that I could see desktop background but no icons and right-click menu not working also.

---

### Post by tawmas on 2009-10-29
> **Aero-Z said:**
> I've had similar problem. Only that I could see desktop background but no icons and right-click menu not working also.

And what did you do to fix that?

---

### Post by hesser on 2009-10-29
Do you happen to have an ATI card and use the open source driver?

---

### Post by tawmas on 2009-10-29
> **hesser said:**
> Do you happen to have an ATI card and use the open source driver?

Yes to both questions. The video card is identified by lspci as:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

---

### Post by hesser on 2009-10-29
Take a look at this thread. It is a bug that I encountered myself as well. 
[https://bugs.launchpad.net/bugs/444139](https://bugs.launchpad.net/bugs/444139)
If you encounter font corruption, take a look at post #19 in the same bug report.

Good luck

---

### Post by Aero-Z on 2009-10-29
> **tawmas said:**
> And what did you do to fix that?
Nothing. The problem still comes up from time to time.
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by tawmas on 2009-10-29
> **hesser said:**
> Take a look at this thread. It is a bug that I encountered myself as well. 
[https://bugs.launchpad.net/bugs/444139](https://bugs.launchpad.net/bugs/444139)
If you encounter font corruption, take a look at post #19 in the same bug report.

Good luck

hesser, I think I have that bug as well. As a temporary workaround, I disabled compiz and enabled metacity compositing, which used to be too slow under 9.04 but seems workable so far with 9.10.

I'll look into the DKMS workaround as soon as I'm a little less busy.

Thank you a lot!

---

