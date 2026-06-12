---
title: "No Menu Bar"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2010-11-18
After applying the most recent set of updates, I no longer have the menu bar. So I can't do anything!

HELP!

---

### Post by sikander3786 on 2010-11-19
Which version of Ubuntu is it? And Netbook or Desktop?

And what do you mean by menu bar? Gnome-panels...?

---

### Post by vchapman on 2010-11-19
> **sikander3786 said:**
> Which version of Ubuntu is it? And Netbook or Desktop?

And what do you mean by menu bar? Gnome-panels...?

10.10

Its on a notebook, but it is the 64 bit desktop version

I guess I mean the Gnome panels

The bar at the bottom of the screen has also disappeared

---

### Post by sikander3786 on 2010-11-20
Try deleting the existing config for your panels. Go to Terminal and,

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

If you can't get to the Terminal for any reason, press Ctrl + Alt + F1 to get to the tty1, put the commands and then press Ctrl + Alt + F7 to get back to the desktop.

---

### Post by vchapman on 2010-11-20
> **sikander3786 said:**
> Try deleting the existing config for your panels. Go to Terminal and,

```
rm -rf ~/.gconf/apps/panel
``````
pkill gnome-panel
```If you can't get to the Terminal for any reason, press Ctrl + Alt + F1 to get to the tty1, put the commands and then press Ctrl + Alt + F7 to get back to the desktop.


 What do I do next

---

### Post by vchapman on 2010-11-20
> **sikander3786 said:**
> Try deleting the existing config for your panels. Go to Terminal and,

```
rm -rf ~/.gconf/apps/panel
``````
pkill gnome-panel
```If you can't get to the Terminal for any reason, press Ctrl + Alt + F1 to get to the tty1, put the commands and then press Ctrl + Alt + F7 to get back to the desktop.


 What do I do next

---

### Post by vchapman on 2010-11-20
> **sikander3786 said:**
> Try deleting the existing config for your panels. Go to Terminal and,

```
rm -rf ~/.gconf/apps/panel
``````
pkill gnome-panel
```If you can't get to the Terminal for any reason, press Ctrl + Alt + F1 to get to the tty1, put the commands and then press Ctrl + Alt + F7 to get back to the desktop.


 What do I do next

---

### Post by sikander3786 on 2010-11-20
> **vchapman said:**
> What do I do next
Reboot and see if the panels appear?

---

### Post by sikander3786 on 2010-11-20
<snip>

---

### Post by vchapman on 2010-11-21
> **sikander3786 said:**
> Reboot and see if the panels appear?


I did this:

sudo apt-get install gnome-panel

and things got restored.

---

### Post by sikander3786 on 2010-11-21
> **vchapman said:**
> I did this:

sudo apt-get install gnome-panel

and things got restored.
It means that the gnome-panels were removed some how in the latest updates.

While updating, please keep an eye on what is going to be installed, upgraded or removed. You'll know that way and if you find anything offensive, you can see the forums about what happened to other members after applying those updates.

Glad to know it sorted. You can now mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

