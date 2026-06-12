---
title: "Installed Server now want gnome.. = )"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by Eleaf on 2005-08-20
Ok.  I have very limited drive space so I decided to do a server install and then later install gnome without all the other packages and such on the Ubuntu Hoary install cd.

I'm using a ppc iBook.

I now need to know how to install gnome.  I've tried sudo apt-get install gnome and things like that but it keeps saying the package is not available.  Can you help me with the correct package name to get a working gnome desktop environment?  Thanks!

Your help is very appreciated.  =-)

---

### Post by adwait on 2005-08-21
I think this should do it:
```
sudo apt-get install ubuntu-desktop
```

Also, on my end, apt-get install gnome works too........so I guess you need to enable all the repositories with universe/multiverse.

---

### Post by Eleaf on 2005-08-21
Alright!  Thanks!  After uncommenting the universal apt source and updating, sudo apt-get install ubuntu-desktop and sudo apt-get install gnome works!  I don't want to do ubuntu desktop because that takes up way too much room but just the gnome one seems a little bit smaller.  It says after unpacking 708 megabytes will be taken up.  I'm wondering if there is a more bare version of gnome or maybe a different window manager that is also very good yet doesn't take up wayyyyy too much space?  I would also like to have gnome/kde application support with the window manager.  Any good recommendations?  Thanks a lot! =-D

---

### Post by Eleaf on 2005-08-21
Also, when looking through the package list to install apt-get install gnome, I noticed things like gnome and inkscape and others are included in the packages.  I would like to install these myself as I want and I just want a usable gnome-desktop environment without all these things.

Any suggestions on what to do?  Thanks! =D

---

### Post by Eleaf on 2005-08-21
[QUOTE=Eleaf]Also, when looking through the package list to install apt-get install gnome, I noticed things like gnome and inkscape and others are included in the packages.  I would like to install these myself as I want and I just want a usable gnome-desktop environment without all these things.

Any suggestions on what to do?  Thanks! =D[/QUOTE]

I'm sorry, I ment to say gimp there when I said gnome...

---

### Post by adwait on 2005-08-21
If you want a lighter window manager, you may want to try XFCE or IceWM.

---

