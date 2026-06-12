---
title: "Error Please Need Help Asap"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by ImTheOne on 2007-05-03
Ok i have Feisty Fawn and i installed it yesterday everything was working perfectly all day yesterday and all day today until just now, i try to install updates, i have beryl but i dont think that is messing it up...the error message i get reads:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
But when i type that is the thing that says run 'dpkg --configure -a' to correct the problem.  it says i must have a Superuser account but i am the superuser on the computer so im not exactly sure what to do, im kinda new to Linux and in still learning so im not too experienced.
Thanx for the help

---

### Post by tcarradine on 2007-05-03
you'll need to run the command as a superuser like it says. try:

sudo dpkg --configure -a

from the terminal. 

Tim

---

### Post by ImTheOne on 2007-05-03
Thanx bro it worked it said i had a broken dependency package and i repaired and it fixed it thanx again man if i could give u karma i would :)

---

### Post by tcarradine on 2007-05-03
no problem! 

checkout [http://www.xkcd.com/c149.html](http://www.xkcd.com/c149.html) when you have a second.

Tim

---

