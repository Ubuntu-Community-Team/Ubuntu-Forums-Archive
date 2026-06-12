---
title: "Newbie Installation Help for Tuxcards"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by floppy on 2005-08-08
Tuxcards is an interesting package that I'd like to install. However, it's not in any of the repositories used by Synaptic. I admit to a fair degree of ignorance about how to get it installed, despite reading some explanations about installations. Can someone please help me get Tuxcards installed and into Gnome? I probably need step-by-step help.

Home page for Tuxcards: [http://www.tuxcards.de/index.html](http://www.tuxcards.de/index.html)
Download page: [http://www.tuxcards.de/requirements.html](http://www.tuxcards.de/requirements.html)

Download page has "a statically linked binary tar.gz" and "a deb package for Debian". I've downloaded both into my /home, but how do I proceed?

Thanks for any and all help!

---

### Post by dave9191 on 2005-08-08
Hi, 

put the .deb package into your home dir, open a terminal and type "sudo dpkg -i tuxcards_1.2-1_i386.deb" (adujust the name of the file to the one you downloaded if different). It will ask you for your password and unless it throws up some errors, it should install. Then you can start it by typing tuxcards into the terminal I guess :)

Dave

---

### Post by floppy on 2005-08-08
Well, it seems to have installed, but it's not happy. Here's the error I get:
tuxcards: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Plus, of course, it'd not only be nice to have it work, but it'd be nice to have it in the Gnome menus.

Thanks for the help so far!

---

### Post by dave9191 on 2005-08-08
You get that error when you try to run it?

And it looks like a kde (well a qt which is used in kde) libary that its trying to use. Try "sudo apt-get install libqt3-mt-dev". As for adding it to the gnome menu, you will have to add that yourself if it isnt there. 

Dave

---

### Post by floppy on 2005-08-08
Dave,

Thanks for your help. Please remember I really AM a newbie. I have no clue what a "qt" is, for example. And adding the package to Gnome was part of my question, too. I know I'll have to add it, but I don't know how. Also, the package you mentioned didn't suffice, or perhaps I messed something up.

Sorry I'm so thick-headed,
floppy

---

### Post by dave9191 on 2005-08-08
You're far from thick-headed :) I was just saying that qt is part of kde, and you have gnome instead of kde. So you will have to install some stuff. qt is a graphical libary for drawing windows, menus, buttons and others on the screen. Gnome uses GTK. By the look of things, tuxcards uses qt to draw things. 

Now lets check that you dont really have that file that it needs. First "sudo updatedb", then when that finishes "locate libqt-mt.so.3" and with luck it will tell you where the file is. If it doesnt find anything, then we will have to find out what other packages you need to install. 

Dave

---

### Post by floppy on 2005-08-09
Dave,

Thanks for your guidance. A friend took pity on me and assisted my installation. He used the "statically linked binary", which apparently eliminated the necessity to download any additional libraries or packages. The files were moved to appropriate places and the Gnome menu was modified using the technique listed in the Wiki for Hoary. Everything worked except the icon, and that's fine with me!

Case solved. Thanks again,
floppy

---

### Post by dave9191 on 2005-08-09
cool, glad you got it working in the end :)

Dave

---

### Post by jhuff on 2005-10-22
[quote=floppy]Dave,

Thanks for your guidance. A friend took pity on me and assisted my installation. He used the "statically linked binary", which apparently eliminated the necessity to download any additional libraries or packages. The files were moved to appropriate places and the Gnome menu was modified using the technique listed in the Wiki for Hoary. Everything worked except the icon, and that's fine with me!

Case solved. Thanks again,
floppy[/quote]

I'm also trying to install tuxcards.  Could you explain how to use the "statically linked binary".

---

