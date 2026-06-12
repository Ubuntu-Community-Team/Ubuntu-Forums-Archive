---
title: "Ubuntu 12.04 and windows"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by oygle on 2012-08-30
Hi,

Have upgraded from 10.04, and i don't like the way 12.04 'works' as a desktop.

There is no taskbar as before. The apps are not all set out neatly from top menus. If you have many Firefox windows open, you have to click the app icon twice to see other windows. If I'm in an app like KMail, I can't get to the other windows within KMail, unless I go click the KMail icon again, .. very much harder to drive.

Also, there is no CLI (but have since found a Ctrl-Alt-T brings it up), and there are many other apps 'missing, from within system admin or system/prefs. It was all "neat" before with all office apps together, all internet apps together,etc.

Now, I do see there are different desktops that can be used, like that shown at [http://modifyubuntu.com]("http://modifyubuntu.com") and
[http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html]("http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html")

Can someone please inform me which is the desktop to install/use, so that it has the same look/feel, and use of taskbar and windows, etc, as 10.04 operated.

Oygle

---

### Post by mastablasta on 2012-08-30
xfce (Xubuntu)
 
yu might laos give Kubutnu a try since you use Kmail.

---

### Post by oygle on 2012-08-30
Thanks. What about KDE4, seems I just need ..

```
sudo apt-get install kde-plasma-desktop
```

---

### Post by oygle on 2012-08-30
On the modify Ubuntu site, it says to clcik on the gear, yet when I did that, only 2 options - Ubuntu and Ubuntu 2D, none of the others ??

---

### Post by darkod on 2012-08-30
If you want an interface similar to the 10.04 (gnome) you can try gnome-panel. That's the package for the Gnome Classic interface, very similar to the previous interfaces.

Just do:
sudo apt-get install gnome-panel

and you should see option for Gnome Classic at your login page when you click the symbol next to the user. It also remembers the last login used so you don't have to click every time.

---

### Post by oygle on 2012-08-30
Thanks, I will try gnome-panel.

Oygle

---

### Post by mastablasta on 2012-08-31
> **oygle said:**
> On the modify Ubuntu site, it says to clcik on the gear, yet when I did that, only 2 options - Ubuntu and Ubuntu 2D, none of the others ??
 
not sure why that happens. 
 
perhpas not everything needed for it to appear there is included in that package.

---

### Post by oygle on 2012-08-31
> **mastablasta said:**
> not sure why that happens. 


I wasn't clicking the right icon, it does work okay.

---

