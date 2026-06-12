---
title: "Vuze, update to 4.5.0.4"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by gavdari on 2010-09-12
I recently downloaded the source from vuze.com and I was able to run it using ./azureus. but the launchers on my menus and dock is pointed toward the previous version of vuze. when I uninstall the old one, then the launcher is disappeared from the menu. but all the time I can run vuze 4.5.0.4 through terminal. what should I do to build it through the system?

---

### Post by Origin_Unknown on 2010-09-12
I'd like to know this aswell - I want to be able to use a port number in the +50000 range but the one installed from the software center does not allow it

---

### Post by cybercookie72 on 2010-10-09
Greetings, 

Not sure about building it through the system...as I am still sort of noobish.  

but can't you add it to the applications menu?

by right clicking on the applications menu -> Edit Menus

then click + New Item

the following are the stuff that vuze was installed with when I used the software center....

type : Application
name : Vuze
command : azureus %f
comment : Download and share files using the BitTorrent P2P network


hope this helps...now I am of to un-install vuze so i can figure out how to install 4.5.10 :)

---

### Post by rinaldow on 2010-10-22
> **cybercookie72 said:**
> Greetings, 

Not sure about building it through the system...as I am still sort of noobish.  

but can't you add it to the applications menu?

by right clicking on the applications menu -> Edit Menus

then click + New Item

the following are the stuff that vuze was installed with when I used the software center....

type : Application
name : Vuze
command : azureus %f
comment : Download and share files using the BitTorrent P2P network


hope this helps...now I am of to un-install vuze so i can figure out how to install 4.5.10 :)

The command tbrough terminal is sudo if u want to include advanced settings, coz then u r providing urself admin rights.

if u wanna access it graphically you need to go to the menu like cybercookie said, and then in stead of adding a new one you can search for the location of your new installed vuze.
If you cant find it while browsing, try pressing ctrl+h so u can see the hidden files.

then the command would be: ***/.azureus or something similar.
the only thing you need to do is make sure that the term "gksudo" is put in front so that the command will look like "gksudo ***/.azureus"
the stars are meant to be imaginary/ in relation with the path u stored vuze.

Good Luck!

---

