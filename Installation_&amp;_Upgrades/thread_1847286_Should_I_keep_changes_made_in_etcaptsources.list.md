---
title: "Should I keep changes made in /etc/apt/sources.list?"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2011-09-20
In order to install acroread (currently known as adobe reader) I had to uncomment a few lines in the file /etc/apt/sources.list (since multiverse repository contains acroread). When installation is completed, should I revert to previous sourecs.list file or should I keep the changes done? My guess is that I should, otherwise what is the purpose of keeping backup of this file before making changes? Does the choice matter as far as updates are concerned?

Second doubt: I found at system>administration>software sources that multiverse repository was chcked but I failed to install acroread with apt-get even after using command sudo apt-get update. Why did this happen?

Third question: I refused to set acroread as default pdf reader. In case I change my mind later, how do I make acroread default pdf reader?

---

### Post by mörgæs on 2011-09-21
1) If you add a repository for installing something, you should keep it open in order to get updates.

2) Can't explain.

3) If you right-click on a PDF file you can select default application for opening.

---

### Post by jerrrys on 2011-09-21
Number 2 :

acroread is in 10o4, but I don't see it in 11.10

Edit a woops

---

### Post by vinterkind on 2011-09-22
Hi,

1) i agree with mörgæs. And keep an eye on /etc/apt/sources.list.d/*.list !

2) if you manually changed the file it could be. But if you invoke apt-get update you should see all the activated repositories. If it still isn't there it may be missing in that repo.

3) everything said. Or invoke it as shell command. acroread vs. evince ;)

cheerio,

---

### Post by vinterkind on 2011-09-26
did anything happen here ?
or is it solved ? If so, please mark it as such. ;)

cheers

---

