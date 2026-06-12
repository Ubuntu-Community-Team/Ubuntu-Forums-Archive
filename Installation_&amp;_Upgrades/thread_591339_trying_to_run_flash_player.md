---
title: "trying to run flash player"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by scuba_suit on 2007-10-25
i just got edubuntu up and running, i have to get the flash player, can't see youtube videos for example, i downloaded a player from the macromedia website, can someone tell me step by step how to install it? i'm so conditioned from using windows for so many years i feel like a caveman trying to figure out how to make the flash player work (at this point i'm getting my club out to maybe give it a little "tap" so that it can work)

---

### Post by wolfger on 2007-10-25
> **scuba_suit said:**
> i just got edubuntu up and running, i have to get the flash player, can't see youtube videos for example, i downloaded a player from the macromedia website, can someone tell me step by step how to install it?
I would go get the Macromedia player from the repository, not from the Macromedia website. Much easier to deal with, and plays YouTube just fine (you are using a 32-bit browser, not 64-bit, right?)
```
sudo apt-get install flashplugin-nonfree
```

If you are using a 64-bit browser, it doesn't matter where you get Macromedia Flash from, it won't work. There is no 64-bit version. Try Gnash instead.

---

### Post by oldos2er on 2007-10-25
Flash is in the Medibuntu repository, so you need to go into /etc/apt/sources.list and uncomment the lines referring to it: gksudo gedit /etc/apt/sources.list (in a terminal). After you've made the changes and saved, type sudo aptitude update in a terminal, then sudo aptitude install flashplugin-nonfree .

---

### Post by scuba_suit on 2007-10-25
cool thanx, but exactly how do i get a terminal? from the menu on the top? and is that the correct command line to use to install? yerah i dl'ed it from macromedia, it's sitting on the desktop, should i just erase it and start again? eventhough i have edubuntu now, i am loving it to death, i feel like the shackles of m$ has been lifted.... 

quick question: can i upgrade down the line to ubuntu: gutsy gibbon having edubuntu? or do i have to wait for the edubuntu version of gutsy to cone out (which i believe shouldn't be that far off, right?)

---

### Post by oldos2er on 2007-10-25
If you're using Gnome, from the menu on the top choose Applications, Accessories, Terminal. Or, hit Alt-F2 and type in 'gnome-terminal.' Same end result.

 I don't know when Edubuntu Gutsy will be out, sorry.

---

