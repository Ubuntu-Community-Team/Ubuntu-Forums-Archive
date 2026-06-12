---
title: "Installation problems"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by Akazuk on 2011-07-06
Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.


Last night i kinda started installing a couple of things but i had some electricity problems and my pc restarted. Well  .... since then i cannot install anything because of this error. Can anyone help me ? Pwlease ? :)

---

### Post by zvacet on 2011-07-06
Try type in terminal

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by Akazuk on 2011-07-06
Thanks ! It worked :D I'll give you a beer if i ever see you... \\:D/

Aaandd ... another thing ... 
On this pc i have both ubuntu and windows xp sp2.
I installed ubuntu using windows os. I had windows in drive C.... and installed ubuntu in E in which i also had some files which seem unaccesible from ubuntu ... i don't even find them with search ... can i acces them from ubuntu ?

---

### Post by Akazuk on 2011-07-08
Noone ?

---

### Post by dino99 on 2011-07-08
here is how to make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

wubi installation is only for headaches

---

### Post by Rubi1200 on 2011-07-08
Hi and welcome to the forums Akazuk :)

which version of Wubi did you install?

Open a Nautilus File Browser and click on "File System" in the left  pane. Now open the "host" folder. That's your Windows C: drive. Other drives should be listed in the "media" folder.

---

