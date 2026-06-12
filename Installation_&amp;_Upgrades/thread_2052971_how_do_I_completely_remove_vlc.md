---
title: "how do I completely remove vlc"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by emmathompson on 2012-09-04
pls. I'd like to completely remove vlc 2.0.3 from my machine, since I changed its skin to an alienware skin I found on videolan webpage, everytime I tried to use it, it runs & quits in less than a second. 
Pls. advice on how to proceed.

---

### Post by MG&amp;TL on 2012-09-04
> **emmathompson said:**
> pls. I'd like to completely remove vlc 2.0.3 from my machine, since I changed its skin to an alienware skin I found on videolan webpage, everytime I tried to use it, it runs & quits in less than a second. 
Pls. advice on how to proceed.


You'll probably need to purge the package (remove its configuration files as well as the actual program). You can do that by opening a terminal (purple box, find it in dash), and typing:

```
sudo apt-get purge vlc
```

EDIT: Duh, thanks elfy!

---

### Post by Elfy on 2012-09-04
Purging the package will not remove any user specific configurations - and it is entirely possible that is your problem.

You'll have to look in your user files and remove vlc from there.

```
nautilus ~/.config/vlc
```

run from a terminal should open in the vlc folder - check for this skin there.

---

### Post by emmathompson on 2012-09-04
thanks elfy, it worked.
If you don't mind, would you pls. give me some tips, pointers to anything that'd make me a better Linux user. I'm awed at the ease at which it got done.

---

### Post by Elfy on 2012-09-04
well to be honest 5 years ago I had not had much to do with linux - I found reading things here and on various wiki's helped as did helping people when and where I could

also - fixing things when they break 

there is a manual here for 'using' ubuntu [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

check out [googlubuntu]("http://www.googlubuntu.com/") as a search engine

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

