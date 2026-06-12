---
title: "Compiling SVN &amp; checkinstall: same procedure sometimes works, sometimes not!?!"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-12-23
Hy guys!

I've got some weird experience when trying to compile from SVN here...

I do exactly the same steps each time, but the outcome will be unpredictable! Basically, I do the checkout to my folder, then 'sh autogen.sh', works fine. Then './configure' - no problem. Then I do 'make' - runs pretty well. After this, I do 'sudo checkinstall' and specify 'no' for docs, and re-enter the package-version to overwrite the long list contained there and confirm. 

Installation will run and give a LOT of weird output like 'creating... /usr/local/share/xxxxxx - no such file or folder' - regardless, if the installation works out or not. In the end, files get temporarily stored and moved; usually only the last two lines will show success or whether the installation was not successful and everything gets deleted again....

The ONLY thing I can think of being the cause of this weird behaviour is, that maybe the 'sudo'-time passes away too fast, so that the checkinstall-script will run out of permission at the very end of the installation... what do you think? Any ideas?

perixx

---

### Post by perixx on 2007-12-24
Anybody got some ideas? :-s

---

### Post by zvacet on 2007-12-24
Why don´t you just run** sudo make install** ?

---

### Post by perixx on 2007-12-25
Well, because I want to have an easily removable installation at first and I wanna kind of create my own repository where I can offer weekly .deb SVN-versions of the program in question...

perixx

---

