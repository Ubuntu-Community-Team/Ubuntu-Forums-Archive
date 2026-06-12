---
title: "How Do I..???"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by Grayman on 2005-09-07
I'm confused (which is something that happens alot since I installed Linux). I wanted to install educational games for my children on my laptop, so I used the following:

sudo apt-get install junior-math (and later junior-arcade)

That went fine, it asked my password, installed the programs. My question...where did it put them and how do I access them? I dont see any new icons in the games menu like when I installed GCompris and Chess. I can create a custom launcher for these apps if I just know what command line starts them. Thanx

Gray

---

### Post by John.Michael.Kane on 2005-09-07
Try looking here /usr/share/pixmaps/ for the icons 
as to the runing of the programs to check that they work  gksudo <program name>
you can use smeg to add the program to your menu


hope this helps

---

### Post by rafakl on 2005-09-07
Or you can try start the program by simply putting his name in the console:

junior-math

and press enter.

Many software dont install themselves in the program groups.

---

### Post by Stormy Eyes on 2005-09-07
If an app does not create an entry in the GNOME menu, then you should make an account at [bugzilla.ubuntu.com](bugzilla.ubuntu.com) and report the app as defective. All apps packaged for Ubuntu should make entries in the GNOME menu.

---

### Post by Grayman on 2005-09-07
Thanks for all the replies. Junior-Math is the only one I seem to be having trouble with.  For whatever reason it will not run even though I've installed it. typing 'junior-math' & countless variations in terminal window doesn't start it. Oh well...I will keep playing.

---

### Post by Stormy Eyes on 2005-09-07
Just type 'j' and then hit the TAB key in the terminal. See how many possibilities come up. If there are a lot, the shell will ask if you want to see them all.

---

### Post by Grayman on 2005-09-07
I also am unable to install smeg. I have all the repositories checked in Synaptic Package Manager, but when I 

sudo apt-get install smeg

I get E: Couldn't find package smeg


what am I doing wrong?

Gray

---

### Post by rafakl on 2005-09-07
I installed it too (cryptography for kids!!) and i cant find the executable files too :(

---

