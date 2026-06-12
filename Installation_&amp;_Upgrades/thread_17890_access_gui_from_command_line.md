---
title: "access gui from command line"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by matssys on 2005-03-03
I am very new to linux and  have just installed version 4.1. It successfuly dual boots with the option of xp or ubuntu. when I select ubuntu I get the command line and can login ok here. How do I get to a GUI version? Did I miss something in the installation and do I hav eto run the installation process again?

I hope someone can please assist.

---

### Post by gungaden on 2005-03-09
A normal installation of Warty (4.1) should bring up the Gnome GUI application upon startup. It seems that you would be well-served to re-install and carefully monitor the installation.

---

### Post by raitchison on 2005-03-09
I'm experiencing the exact same problem.  I reinstalled _twice_ and watched the install pretty carefully.  I didn't notice anything out of the ordinary.

So if the GUI doesn't start automatically after install is there a way to start it manually?  Who knows maybe when I try it might throw an error to indcate why it didn't start automatically.

---

### Post by vladimir on 2005-03-11
I had a similar problem but on Mandrake, so my advice might not be relevant.

To launch the graphic server, try typing startx 
then look in your /etc/inittab file
you might have a line 

id:3:initdefault: 

that should actually be 

id:5:initdefault: 

HTH
Vlad

---

