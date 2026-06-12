---
title: "removing the GUI from Ubuntu desktop"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by poguemahone on 2010-09-19
I originally installed Xubuntu Desktop so that I could manage my fileserver with the GUI (through FreeNX).  Now that I have gotten more confortable with Linux, I manage the fileserver entirely from the terminal and ssh.

I feel like I could trim down the fileserver and free up some memory and CPU cycles.  Additionally, I don't really like having receive the firefox updates, etc.

Is there a way I can eliminate the GUI from my fileserver?

---

### Post by NiGhtMarEs0nWax on 2010-09-19
sudo apt-get remove xubuntu-desktop

after that, run

sudo apt-get autoremove

you can remove firefox the same way you removed the xubuntu-desktop

---

### Post by K.Mandla on 2010-09-19
There's also a nifty little program called [debfoster]("http://packages.ubuntu.com/search?keywords=debfoster") that will skip through the packages you have installed and ask if you want to remove them. That might be more comprehensive, or pick out a few packages you didn't know were in there.

---

