---
title: "Install dependency problem"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by dachelb on 2006-05-08
I recently installed Ubuntu on an old P2 (450 MHZ. 256 MB RAM) that was running mandrake 10 until glibc got broken.  The installation (formatted / /usr and /home so there was no remaining mandrake stuff) was somewhat painful in that it took a very long time (several hours) and rebooted several times and continually downloaded packages.

In the end it got installed and it seems to be working.  The problem is that when I boot up the system it *still* thinks that it needs to install more things but is stuck in a dependency hell.  It complains that mysql-common (installed by 4.0.24-10ubuntu2.1) conflicts with mysql-common4.1 (needed by 4.1.12-1ubuntu3.2). 

I can simply CTRL-ALT-F7 to get to the gnome login screen and everything there seems normal but there are several tasks running that seem to be involved in this 'update' process.

I've tried removing both mysql-common and mysql-common4.1 but it makes no difference.  If I try to kill the tasks that seem to be related to this dependency issue they just re-spawn and I'm thrown back to the text mode install screen.

Any ideas?  This box is basically being used as a home file/print server.

Thanks

---

### Post by louis_nichols on 2006-05-08
What version of Ubuntu are you using? Did you try:

```
sudo apt-get install -f
```

EDIT: sorry, my head was somewhere. I meant **version **of Ubuntu. Distro was in another thread. :)

---

### Post by dachelb on 2006-05-08
I'm using 5.10.

---

### Post by louis_nichols on 2006-05-08
try using:

sudo apt-get install -f

---

### Post by dachelb on 2006-05-08
apt-get makes no difference.  Still does the same thing.

---

### Post by louis_nichols on 2006-05-08
well... the f switch of apt-get was supposed to fix broken packages... Sorry it didn't work!

---

