---
title: "help with an installation mistake"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by Llewxam on 2008-07-28
i managed to somehow install intrepid over my hardy and screwed up half of my system. nvidia and compiz are no longer working. i am desperately trying to restore my system to the way it was without having to lose any data whatsoever. spent way too much getting everything set up after i upgraded to hardy. 
so anyone, please, is there any possible way to set my system back to hardy?

---

### Post by scottuss on 2008-07-28
If you did sudo update-manager -d that forces a distro upgrade, which in itself as far as I know is not easily reversable

---

### Post by Elfy on 2008-07-28
This might help although it copuld be painful - make sure you have backups

[http://ubuntuforums.org/showthread.php?t=586064](http://ubuntuforums.org/showthread.php?t=586064)

---

### Post by Llewxam on 2008-07-28
no. didn't run that command. i was following a tutorial for my laptop to fix the battery life, sound a source line and added it to the list. from there i ran sudo apt-get update and that showed me a bunch of packages. having suffered from the locales bug while upgrading i let it run thinking it would install whichever packages would've been missed before. then i find myself with this.

---

### Post by Elfy on 2008-07-28
There is no easy way to go backwards and it might not work, but ronaccs thread might help.

If you have a seperate /home then a your confiug files will be preserved if you have to go backwards with a clean install.

If you have not reinstalled since you went to hardy then you should be able to see which files you have edited using bash history - assuming that they are unchanged you could copy the necessary files - reinstall hardy and then use the backed up files to get back where you were.

```
cat ~/.bash_history > ~/Desktop/bashtext
``` should put a text file on your desktop which you can read

```
cat ~/.bash_history | grep sudo > ~/Desktop/bashsudo
```should put a text file on your desktop which you can read containing sudo and gksudo only

---

