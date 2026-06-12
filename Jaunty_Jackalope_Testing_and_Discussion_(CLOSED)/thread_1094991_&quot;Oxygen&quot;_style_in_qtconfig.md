---
title: "&quot;Oxygen&quot; style in qtconfig"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by t.alex on 2009-03-13
Hi,

does anyone know why "oxygen" doesn't appear in "Select gui style" in qtconfig-qt4? 

i currently have these packages installed:

```

dpkg -l|grep oxygen
ii  kde-icons-oxygen                          4:4.2.1-0ubuntu1                                Oxygen icon theme for KDE 4
ii  oxygen-cursor-theme                       0.0.2008-07-07-svn824849-1ubuntu1               Oxygen Mouse Cursor Theme

```

Thanks!

---

### Post by Sand &amp; Mercury on 2009-03-13
You are probably missing the package that contains the oxygen theme. Installing kde-core with aptitude would give that to you, but that will install KDE itself along with the artwork you're after... unfortunately I'm not sure which lone package has the oxygen theme. It would probably have either KDE or Kubuntu in its name somewhere, anyway.

---

### Post by jfernyhough on 2009-03-13
For me, selecting "Desktop Style" activates Oxygen. It may be down to installing the KDE4 desktop to test.

---

### Post by asimon on 2009-03-13
The Oxygen widget style is included in the package *kdebase-runtime*, so make sure you have that installed.

---

### Post by t.alex on 2009-03-13
Hi,
it doesn't seem to work :confused:
i've installed kde-core and kdebase-runtime but oxygen style still doesn't show up in the list

Any clues?

---

### Post by jfernyhough on 2009-03-13
Does "Desktop Settings" show up?

And just to make sure, you are running qt4-qtconfig (not qt3-qtconfig)?

---

### Post by t.alex on 2009-03-13
"Desktop-settings (default)" seems to have exactly the same effect as "GTK+"

and yes, i am running "qtconfig-qt4" (i also have a "qtconfig", which actually points again to "qtconfig-qt4")

Thanks!

---

### Post by jfernyhough on 2009-03-13
Huh. There must be a bug in here somewhere. I remember reading a post along the lines that qt4 appearance settings had no effect in qt4 apps. I just tried the GTK+ setting, opened Konquerer and it's using Oxygen instead. Oxygen itself does not appear in my list. Weird.

---

### Post by t.alex on 2009-03-13
i know i had the same problem in intrepid. "oxygen" style appeared  in qtconfig after i installed kubuntu-desktop (i wanted to see how kde 4.2 works). So i guess i'm still missing a package ?!

---

