---
title: "Does 6.06.1 Have a GUI?"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Chip21054 on 2008-02-27
Stupid question, I am sure, but after installing 6.06.1 I boot to a text based login and then to a command prompt.  I have tried entering commands such as startx, xinit, initx, and gdm.  All return a reply from bash- that says command not found.  So, my question is, shouldn't I be expecting something more than a command line prompt?

If yes, will you please tell me how to get the "something more."  I feel like I am close, but am at a loss for what to do next, other than go take a linux command class.

Chip

---

### Post by Pumalite on 2008-02-27
If you installed the Server Edition; there is no GUI. If you want a GUI:
sudo aptitude install ubuntu-desktop

---

### Post by zvacet on 2008-02-27
If you installed servewr version then in terminal 

```
sudo nano /etc/apt/sources.list
```

add this line

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

crrl+o and Enter ctrl+x

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Chip21054 on 2008-02-27
Is 6.06.1 a server edition?  I intended to download the desktop version.  How can I tell what I have?

---

### Post by Pumalite on 2008-02-27
If you don't have a GUI after a successful installation; you have the Server Edition.

---

### Post by Chip21054 on 2008-02-27
There's no command to tell what version is installed?  I just don't think I installed the server version, and I don't want to redo the steps it took to get to the point where I am, and end up at the point where I am, again.

BTW, have searched and reviewed 20 or 30 threads looking for answer, and note your response on many of the threads.  So you are obviously a friend to the newbies and I don't want make you mad by challenging your statement, but I just don't think I installed the server version.  

~~Chip

---

### Post by Pumalite on 2008-02-27
Try:
startx

---

### Post by Chip21054 on 2008-02-27
startx yields a response from bash- such as command not found.

---

### Post by dstew on 2008-02-27
Sounds like you have the server version. However, it is also called Base Install by some installers.

---

