---
title: "AMSN - instllation folder"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by qzem on 2008-02-16
I have installed the latest amsn on ubuntu. I got it from official amsn website. Now i don't know in which directory was it installed. Can somebody help me. I would like to make a shortcut on my desktop. Now I can only run it from terminal and when i close terminal the amsn closes al well. And it bothers me. I've searched it in /home/usr/share/amsn, but here is no amsn folder. Is it possible that is hidden?

---

### Post by xyphur on 2008-02-16
Did you compile it from SVN? sounds to me like you need to do the following:

sudo make install

...from the folder where it currently resides. You can locate the aMSN executable by typing 'locate amsn' at the terminal. It'll most likely be somewhere in your /home folder. Once installed, it symlinks the executable to /usr/bin/amsn and then places a shortcut in the Internet submenu.

Of course, your mileage may vary depending on how you initially installed aMSN. Also, aMSN has a forum as well, and you'd likely get better answers dealing with installation of their software there. Not to say that you won't get help here of course, but I'm only going on how I got my copy installed via SVN snapshot (latest available build).

Best of luck! :)

---

