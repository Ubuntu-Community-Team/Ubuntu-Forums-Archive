---
title: "Jardinains 2 install help?"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by burntmonk on 2009-12-21
Hey all, I'm somewhat new to Ubuntu, and I'm trying to install a simple game from a .tar.gz package, but when i run ./configure i get 'configure: command not found.' I know installing from .tar files has been covered ad nasuem, but this is the only trouble i have. Sorry if i'm missing something obvious, but thanks ahead for the help. :)

---

### Post by bumanie on 2009-12-21
Make sure you have build-essential installed > sudo apt-get install build-essentialThen extract the tar.gz by right clicking and choosing 'extract here'. You can open the file and find the 'read me' or 'install' instructions which should tell you the rest of the process. Also you must change to the working directory where the extracted file is ie, if on your desktop, in terminal > cd ~/Desktopfollowed by enter then > cd <name of extracted file>followed by enter and then follow the installation instructions (usually ./configure --> enter ; make --> enter ; sudo make install --> enter).

---

