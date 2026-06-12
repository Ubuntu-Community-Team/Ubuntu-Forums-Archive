---
title: "Lucid some apps look like Win98?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kreuger on 2010-03-31
For some reason, after upgrading to Lucid a lot of my applications have a Windows 98 look to them and they seem to ignore my theme. An example is the HPLIP Gui as you can see [here]("http://img63.imageshack.us/img63/9900/hplip.png")

---

### Post by cariboo on 2010-03-31
Check to see what theme you are using, I had the same problem on one of my systems, reselecting Ambiance solved the problem.

---

### Post by Kreuger on 2010-04-01
> **cariboo907 said:**
> Check to see what theme you are using, I had the same problem on one of my systems, reselecting Ambiance solved the problem.

Made no difference. I'm using Aurora-Midnight. I tried switching to Clearlooks and it made no difference

---

### Post by metallica1788 on 2010-04-01
the only reason i can think of is that somehow the themes are only installed on a user level and not in de common '/usr/share/themes' location. If you run a program with sudo rights and the themes arent in he /usr/share/themes folder, the system will choose a default theme.

---

### Post by forcecore on 2010-04-01
This is common when using custom themes, developers should replace something better for default than Win98 theme. I do not worry so much because 95% apps in use is user level.

---

### Post by psyke83 on 2010-04-01
> **forcecore said:**
> This is common when using custom themes, developers should replace something better for default than Win98 theme. I do not worry so much because 95% apps in use is user level.

???

Anyway... metallica1788's reply is the correct answer. Any themes located in ~/.themes/ will not be available to any applications which run under sudo/root privileges (e.g., Synaptic).

---

### Post by Kreuger on 2010-04-01
> **psyke83 said:**
> ???

Anyway... metallica1788's reply is the correct answer. Any themes located in ~/.themes/ will not be available to any applications which run under sudo/root privileges (e.g., Synaptic).

It's a theme made by Linux Mint's team (I think, thats where I found it). It works fine in Synaptic (as I ran gtk-theme-switch to set it as root too). Its just some apps that are like that though. I have it in both locations too (I did that just incase)

---

### Post by psyke83 on 2010-04-01
> **Kreuger said:**
> It's a theme made by Linux Mint's team (I think, thats where I found it). It works fine in Synaptic (as I ran gtk-theme-switch to set it as root too). Its just some apps that are like that though. I have it in both locations too (I did that just incase)

It appears that HPLIP GUI is a QT3 application. QT4 applications can use GTK styles through [QGtkStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle") (that page is outdated - it is now integrated into QT4 by default), but the same is not true for QT3 applications.

Although you can't use the GTK styles for QT3 applications, you can use other QT3 styles (configurable through qt3-qtconfig). For more information, see: [http://wm-eddie.info/?p=129](http://wm-eddie.info/?p=129)

---

### Post by pferraro on 2010-04-01
> **psyke83 said:**
> It appears that HPLIP GUI is a QT3 application.

Nope - hplip-gui is a QT4 app.  The theme can be changed via the qt4-qtconfig package.

---

### Post by castrojo on 2010-04-01
This sometimes happens when gnome-settings-daemon crashes, try logging out and back in.

---

### Post by Kreuger on 2010-04-05
> **pferraro said:**
> Nope - hplip-gui is a QT4 app.  The theme can be changed via the qt4-qtconfig package.

Well it's not just QT apps (at least that I can recall). I'm trying to remember specific programs that do this. Maybe it is just my QT stuff. But isnt KTorrent also QT based? It appears fine.

---

### Post by louis--taylor on 2010-04-05
This happens to me with every window with root permissions (synaptic etc.)

---

### Post by psyke83 on 2010-04-05
> **louis--taylor said:**
> This happens to me with every window with root permissions (synaptic etc.)

Your problem is explained earlier in the thread.

---

### Post by louis--taylor on 2010-04-05
> Your problem is explained earlier in the thread.
Sorry!

---

### Post by Longinus00 on 2010-04-05
X apps will look pretty ugly.

---

