---
title: "Something Awesome Just Happened, GTK Apps PERFECTLY Match KDE4"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-03-15
I rebooted and noticed that all of the GTK apps now perfectly match KDE4's Qt. It was like this before, but now it actually looks great. Did something just get updated, or is there a bug in my favor?

---

### Post by vishalrao on 2009-03-16
Maybe its something to do with this? [https://lists.ubuntu.com/archives/jaunty-changes/2009-March/007220.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-March/007220.html)

---

### Post by krazyd on 2009-03-16
can you screenshot firefox?
please? :)

---

### Post by vishalrao on 2009-03-16
This just showed up: [http://jtechinda.blogspot.com/2009/03/gtk-apps-qtcurve-and-kubuntu-904.html](http://jtechinda.blogspot.com/2009/03/gtk-apps-qtcurve-and-kubuntu-904.html)

---

### Post by krazyd on 2009-03-16
yeah i read that .. looks good!

---

### Post by Technoviking on 2009-03-16
QT apps are also looking very nice under Gnome in Jaunty. Good work to the devs on this.

---

### Post by liorwohl on 2009-03-16
Arora look better then Firefox on Gnome :-P

---

### Post by Joe_Bishop on 2009-03-16
Wish these QT apps begin to render fonts properly :S

---

### Post by jlacroix on 2009-03-16
Yeah, I'm very amazed.

I have a question for those that chose to install both kubuntu-desktop and ubuntu-desktop, under GNOME does QT take over rendering instead of GTK? You'd know if it did because the KDE theme would be all over apps like Nautilus. Or, if some of the letters on the Nautilus file menu are cut off.

This was a bug over a year ago but I was just making sure that GNOME and KDE stayed separate, as they should.

---

### Post by markbuntu on 2009-03-16
GTK stays with gnome and QT with KDE as far as i can tell. The gtk apps do look better now in KDE though.

---

### Post by krazyd on 2009-03-16
> **jlacroix said:**
> I have a question for those that chose to install both kubuntu-desktop and ubuntu-desktop, under GNOME does QT take over rendering instead of GTK?No. Under Gnome, from QT 4.4 on (Jaunty includes 4.5), QT allows apps running under Gnome to actually use GTK for rendering. See here for more details: [http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/](http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/)

Unfortunately, GTK does not have a similar mechanism, which is why firefox, OpenOffice, Inkscape etc. don't really fit in on KDE4. This new qtcurve theme goes some way towards imitating the default KDE4 theme, but is not so good if you use a different theme in KDE4.

Still, it's an improvement on the situation in Intrepid. :D

---

### Post by jlacroix on 2009-03-16
> **krazyd said:**
> No. Under Gnome, from QT 4.4 on (Jaunty includes 4.5), QT allows apps running under Gnome to actually use GTK for rendering. See here for more details: [http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/](http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/)

Unfortunately, GTK does not have a similar mechanism, which is why firefox, OpenOffice, Inkscape etc. don't really fit in on KDE4. This new qtcurve theme goes some way towards imitating the default KDE4 theme, but is not so good if you use a different theme in KDE4.

Still, it's an improvement on the situation in Intrepid. :D

Heck yeah it's an improvement. This new feature is like an unexpected gift.

---

### Post by k@e on 2009-03-20
What is going on there? Somebody on the Qt dev blog said a while ago, that Qt font hinting will be fixed with Qt 4.5. This was good news because that has been bugging me for quite some time. With 4.5 having arrived in Jaunty few days ago, fonts of Qt apps looked exactly like fonts of Gtk apps and I was very happy with that change.

Now, very recently they started to look ugly again, i.e. they probably use an incorrect hinting setting. 

[[IMG]http://img24.imageshack.us/img24/6905/bildschirmfoto9.th.png[/IMG]](http://img24.imageshack.us/my.php?image=bildschirmfoto9.png)

---

