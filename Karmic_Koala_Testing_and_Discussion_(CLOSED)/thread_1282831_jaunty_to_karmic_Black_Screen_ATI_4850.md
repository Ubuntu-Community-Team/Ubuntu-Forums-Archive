---
title: "jaunty to karmic Black Screen ATI 4850"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zFrenchman on 2009-10-04
I have used ubuntu for quite a while but i still am very ignorant when it comes to navigating around ubuntu. This is mainly to the graphical problems i have been having with my ati card and jaunty. After many reinstallations and trial and error, i have finnaly been able to understand how to fix my graphics driver problem and enable compiz etc. 
     Now as soon as i am able to start learning my way around jaunty(9.04)because now my graphics card works flawlessly, i thought upgrading to karmic(9.10) would keep my system stable along with hopefully some other improvements(hoping it might fix by suspend problem). After the upgrade all i get is a monochrome ubuntu loader and then a black screen. HELP. 
     i dont want to have to do another reinstall because i have a lot of programs and themes etc that i dont want to lose and frankly i am getting tired of ubuntu failing on me all the time. What are my options? Is there some type of reverting command i can do from the shell prompt with networking or is re-installing my only hope?

---

### Post by miegiel on 2009-10-04
1st of all, (until karmic is officially released) post problems with karmic in the [_karmic subforum_]("http://ubuntuforums.org/forumdisplay.php?f=359")

Regarding your problem, can you get into a terminal (*Ctrl+Alt+F2* or *Alt+F2*) or boot in recovery mode? If you can try updating and upgrading.
```
sudo apt-get update
sudo apt-get upgrade
```
If that doesn't help try renaming */etc/X11/xorg.conf*. In karmic you shouldn't need the file anymore, but if it still exists (as a leftover from jaunty) it can mess up X.
```
sudo mv -v /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by zFrenchman on 2009-10-07
thank you so much, the second suggestion you gave to me worked and now i am enjoying karmic, i has disabled my previous ati drivers (i believe) but ill work on that as i did under jaunty. i will also keep in mind about your first suggestion as to where to place my questions in the forum.

---

### Post by rsvr85 on 2009-10-12
> **miegiel said:**
> 1st of all, post problems with karmic in the [_karmic subforum_]("http://ubuntuforums.org/forumdisplay.php?f=359")

Regarding your problem, can you get into a terminal (*Ctrl+Alt+F2* or *Alt+F2*) or boot in recovery mode? If you can try updating and upgrading.
```
sudo apt-get update
sudo apt-get upgrade
```
If that doesn't help try renaming */etc/X11/xorg.conf*. In karmic you shouldn't need the file anymore, but if it still exists (as a leftover from jaunty) it can mess up X.
```
sudo mv -v /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Worked for me too, thanks miegiel :D

---

### Post by miegiel on 2009-10-12
You're welcome :)

---

