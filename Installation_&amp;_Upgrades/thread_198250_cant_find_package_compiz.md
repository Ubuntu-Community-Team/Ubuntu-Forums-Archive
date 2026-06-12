---
title: "cant find package compiz"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by osiris999 on 2006-06-16
im trying to install compiz/xgl with this guide [http://www.ubuntuforums.org/showthread.php?t=131267&highlight=install+compiz](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=install+compiz)

everything seems to be right till i try to install xgl. when i put in    

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

it says 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz


this is a fresh install so what could be wrong?

---

### Post by bluevoodoo1 on 2006-06-16
It's in the universe repository. 
Look here.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

or here, for help on how to enable them.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by osiris999 on 2006-06-16
[QUOTE=bluevoodoo1]It's in the universe repository. 
Look here.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

or here, for help on how to enable them.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]


ok it worked but i cant seem to do anything. stupid question but what does log on as gdm mean?

---

### Post by osiris999 on 2006-06-17
[QUOTE=osiris999]ok it worked but i cant seem to do anything. stupid question but what does log on as gdm mean?[/QUOTE]


ok i found the problem and everything is working fine.

---

