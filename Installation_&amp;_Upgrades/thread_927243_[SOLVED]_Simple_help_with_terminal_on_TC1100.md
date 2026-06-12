---
title: "[SOLVED] Simple help with terminal on TC1100"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by trksh22 on 2008-09-22
Ok, I am super new to this. 

**To sum it up, how do I save changes made in terminal?**

I am trying to get my pen and buttons to work on the TC1100. I am in the middle of editing xorg.conf in Terminal. The first time I edited the files it did not say to save ( I assumed it did it automatically) and nothing happened. I opened the file back up and it was the same as the original file. None of my changes saved. How do I get my changes to save?:confused:

TIA

---

### Post by kicksfanscom on 2008-09-22
Your site is very interesting and useful.  ------ Bob Richman ([Air Jordans](http://www.oknike.com/)).

---

### Post by Partyboi2 on 2008-09-25
What text editor are you using to make your changes? Try making the changes with nano
```
sudo nano /etc/X11/xorg.conf
``` then edit the file with your changes then to save Press 
```
Ctrl+o 
enter
Ctrl+x 

```

Or if you prefer a gui approach you can make the changes using gedit by pressing Alt+F2 and typing
```
gksudo gedit /etc/X11/xorg.conf
```

---

