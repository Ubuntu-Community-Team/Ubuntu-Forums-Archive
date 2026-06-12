---
title: "installing netbeans"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by browning_man9 on 2007-12-19
Hey! I am trying to install netbeans 6.0 and I'm getting a box with no text or anything in it. It's simply a gray window with nothing. After a search on the forum some other people had the same problem, but I don't know if they ever found a solution. Any ideas or suggestions? Thanks!

root@dave-ubuntu:/home/dave/NetBeans# ./netbeans-6.0-javaee-linux.sh
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring



I tried changing to some different themes, and that only gave a different error:

root@dave-ubuntu:/home/dave/NetBeans# ./netbeans-6.0-javaee-linux.sh
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: lexical error or unexpected token, expected valid token

---

### Post by nparik1 on 2007-12-20
Try with turning off all visual effects (System->Pref->Appereance Preferences->Visual Effects) and pick the default theme.  It still shows the error on the log but I can see the NB installer.

---

### Post by elio.mussi on 2008-01-11
Great. The solution proposed works. I still get the error message, but the window opens and the installation works.
After the installation, re-enabling the visual effect is just the matter of a click to re-select what I had set for my visual effect.

Thanks you all, guys:)

---

### Post by elio.mussi on 2008-01-11
But when you try using the IDE, you realize that the visual effects are to be disactivated.
grr...

---

