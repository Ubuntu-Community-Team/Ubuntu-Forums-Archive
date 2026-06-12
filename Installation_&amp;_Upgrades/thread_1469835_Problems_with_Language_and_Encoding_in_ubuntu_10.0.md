---
title: "Problems with Language and Encoding in ubuntu 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by msaleiro on 2010-05-02
Hi all!

I have just upgraded my ubuntu to 10.04 with 2.6.32-21 kernel and I'm experiencing some problems with languages and encoding. My previous ubuntu was in portuguese and after the update it changed to english. I tried to change it in System -> Administration -> Language Support but everything remained written in english. 

The other problem is that in gnome the keyboard layout and encoding are correct but in console I can't write some characters such as the ones related to accentuation (`'~^...) I've searched for solutions and tried lots of them but none of them worked. Everytime I open a console i also get the following message: "bash: warning: setlocale: LC_ALL: cannot change locale (pt_PT)"

Can anyone give me some suggestions on how to solve any of theese problems?

Thanks in advance

---

### Post by dino99 on 2010-05-02
seem to be some broken symlinks from previous release

- into synaptic: remove/purge the languages packages installed then reinstall theses needed

- check for locales and localepurge too

sudo dpkg --configure -a
sudo apt-get install -f

install gconf-cleaner and use it

---

### Post by mciancio on 2010-05-05
Same problem: can't set Italian Language.

---

### Post by msaleiro on 2010-05-13
I tried to fix it, couldn't do it.. spent half an hour reinstalling ubuntu 10.04. Everything ok now.

---

