---
title: "No updates BUT wants to remove 16 pkgs"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-04-22
Yes there are no new updates but it wants to remove 16 packages. 
I think I will abort and hang on or is it safe?
Also, what is the {u} after each package?
```
Initializing package states... Done
The following packages will be REMOVED:
  libphonon4{u} libqt4-dbus{u} libqt4-designer{u} libqt4-network{u} libqt4-opengl{u} libqt4-qt3support{u} 
  libqt4-script{u} libqt4-sql{u} libqt4-sql-mysql{u} libqt4-webkit{u} libqt4-xml{u} libqtcore4{u} 
  libqtgui4{u} phonon{u} phonon-backend-gstreamer{u} qt4-qtconfig{u} 
0 packages upgraded, 0 newly installed, 16 to remove and 0 not upgraded.

```

---

### Post by taavikko on 2009-04-22
> **DougieFresh4U said:**
> Yes there are no new updates but it wants to remove 16 packages. 
I think I will abort and hang on or is it safe?
Also, what is the {u} after each package?


{u} stands for that he package has been unpacked but not configured.

If you're running GNOME, it would be safe to remove those.
Only Qt-libraries and phonon (KDE's sound system)

---

### Post by DougieFresh4U on 2009-04-22
> **taavikko said:**
> {u} stands for that he package has been unpacked but not configured.

If you're running GNOME, it would be safe to remove those.
Only Qt-libraries and phonon (KDE's sound system)

Yes, I do use GNOME, but I also have **amarok 1.4** which I will not give up. So will removing those packages harm? I could always reinstall them.

---

### Post by Bucky Ball on 2009-04-22
Get rid of 'em. You can also run:

sudo apt-get autoremove

... to remove disassociated odds and ends that may be lurking, taking up disk space.

---

### Post by taavikko on 2009-04-22
Most of those pkg's have been pulled by amarok I think.
1.4 isn't available in the official repo's isn't it? so there might be a glitch in ppa version and it's dependencies...

You can easily check what are the dependencies by running
```
apt-cache depends package
```
or reverse dependencies,
```
apt-cache rdepends package
```

I would try to reinstall amarok and see if the problem persists.

---

### Post by DougieFresh4U on 2009-04-22
Thanks for all the replies.
I removed them and amarok 1.4 seems to play ok for now

---

### Post by Bucky Ball on 2009-04-22
In Synaptics you can check for broken packages. If you've broken anything (unlikely) it would no doubt show up. You can also fix them there. Details along the bottom left of the GUI.

---

### Post by dualscreenman on 2009-04-22
Removing those shouldn't hurt Amarok 1.4. Those are all Qt4 libraries/related packages. Amarok 1.4 is a Qt3/KDE3 application, so it doesn't use them.

---

### Post by DougieFresh4U on 2009-04-22
> **dualscreenman said:**
> Removing those shouldn't hurt Amarok 1.4. Those are all Qt4 libraries/related packages. Amarok 1.4 is a Qt3/KDE3 application, so it doesn't use them.

Thanks, removed and all is good with 'amarok 1.4'

---

