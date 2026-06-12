---
title: "pidgin plugin pack"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by taxi taxi! on 2007-09-16
I've been trying to install the pidgin plugin pack. it wont work with the command and i cant find it in my synaptic package manager. 
so i downloaded this .tar file from the internet and extracted that into a folder. but now i have no clue  on how to install it...i'm still a bit new to ubuntu. 
i haven't been able to find any help yet. seems like most people are just able to install it with the command line. 
Ah and same goes for pidgin guifications. Can't find that anywhere either.

allright, hope someone can help me.
thanks!

---

### Post by applegrew on 2007-09-16
First as I remember the guification plugin that is available from Synaptic is probably corrupted. Anyway the best way to install Pidgin in Ubuntu is get the deb from getdeb.net. The direct urls to pidgin, pidgin-data and guification are [http://www.getdeb.net/download.php?release=1307&fpos=0](http://www.getdeb.net/download.php?release=1307&fpos=0) and [http://www.getdeb.net/download.php?release=1307&fpos=1](http://www.getdeb.net/download.php?release=1307&fpos=1) and [http://www.getdeb.net/download.php?release=837&fpos=0](http://www.getdeb.net/download.php?release=837&fpos=0) respectively.

install them by
```
sudo dpkg -i package-name
```
You will need to install pidgin-data 1st then pidgin then the guification one. Donno if this is exactly the type of help you sought for. Anyway cheers.

---

### Post by applegrew on 2007-09-16
Just a add-on note. replace package-name by the actual package name.

---

### Post by taxi taxi! on 2007-09-17
allright thanks. I got the pidgin guifications to work now. this getdeb site is pretty nice! 
i'm not sure what pidgin data is though? is it the same as the pidgin plugin pack? Or is there an easy way to install the plugin pack?

---

### Post by applegrew on 2007-09-17
pidgin-data conatins all platform indepenednt files of pidgin, not plugins, like the sound files and the icons files, etc.

---

### Post by kevdog on 2007-09-24
Here is how to install all the plugins (that I know about -- Im sure there might be more -- but these instructions include the purple plugin pack and otr)

[http://ubuntuforums.org/showthread.php?t=558197](http://ubuntuforums.org/showthread.php?t=558197)

---

