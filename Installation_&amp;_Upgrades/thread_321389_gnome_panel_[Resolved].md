---
title: "gnome panel [Resolved]"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by billybag on 2006-12-18
i just installed ubuntu edgy from disk and everything worked fine until i updated it. now upon restart my panel does not display buttons for the open windows and my themes do not work. instead i get a message saying "The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly." metacity is installed and gconf2 is installed. i reinstalled them to make sure.

any ideas?

---

### Post by aysiu on 2006-12-18
What happens if you paste these commands in the terminal and then log out and log back in again? ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
```

---

### Post by billybag on 2006-12-18
> **aysiu said:**
> What happens if you paste these commands in the terminal and then log out and log back in again? ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
```
still nothing. this is really weird

---

### Post by aysiu on 2006-12-18
Can you try this, then?

Log out.

Press Control-Alt-F1

Log in again.

Type these commands in the terminal: ```
mv ~/.gconf.old ~/.gconf
mv ~/.gconfd.old ~/.gconfd
sudo aptitude update
sudo aptitude reinstall ubuntu-desktop
exit
``` Press Control-Alt-F7 and log back in again. No difference?

---

### Post by billybag on 2006-12-18
> **aysiu said:**
> Can you try this, then?

Log out.

Press Control-Alt-F1

Log in again.

Type these commands in the terminal: ```
mv ~/.gconf.old ~/.gconf
mv ~/.gconfd.old ~/.gconfd
sudo aptitude update
sudo aptitude reinstall ubuntu-desktop
exit
``` Press Control-Alt-F7 and log back in again. No difference?
no difference. in the actual /.gconf folder, though, it only contains a  desktop folder and an apps folder. shouldn't their be more?

---

### Post by aysiu on 2006-12-18
Nope. Mine has only *apps, desktop,* and *system* folders in it.

---

### Post by billybag on 2006-12-18
hmmm. *scratches head* i have no idea what could be wrong then. it is really annoying not being able to switch between windows.

---

### Post by aysiu on 2006-12-18
Can you try creating a new test user and seeing if that test user runs into the same problem? Then we can know whether it has something to do with Metacity not being installed properly or your user-specific configuration being corrupted somehow.

---

### Post by billybag on 2006-12-18
> **aysiu said:**
> Can you try creating a new test user and seeing if that test user runs into the same problem? Then we can know whether it has something to do with Metacity not being installed properly or your user-specific configuration being corrupted somehow.
same problem :(

---

### Post by aysiu on 2006-12-18
Well, I did a Google search on your error, and this is the closest to any solution that I could find. Hope it works.
[http://www.mail-archive.com/gconf-list@gnome.org/msg00127.html](http://www.mail-archive.com/gconf-list@gnome.org/msg00127.html)

---

### Post by billybag on 2006-12-18
> **aysiu said:**
> Well, I did a Google search on your error, and this is the closest to any solution that I could find. Hope it works.
[http://www.mail-archive.com/gconf-list@gnome.org/msg00127.html](http://www.mail-archive.com/gconf-list@gnome.org/msg00127.html)
no dice however, he is having thew same exact problem as i am

---

### Post by billybag on 2006-12-19
i fixed the problem and i figured i would share what i did in case anyone else has the same problem.

i simply used Synaptic Package Manager to completely remove gconfig2 and metacity. i let it remove everything, even ubuntu-desktop. when it was done -  i just reinstalled ubuntu desktop and restarted my computer. it took a while for the desktop to load, but when it did... everything was in working order.

---

