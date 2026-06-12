---
title: "List of installed packages from apt-get?"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by drx on 2006-03-16
I have two machines running Kubuntu and i am very happy with both. But because of several problems i already had to reinstall some times and while i always backup the complete /home i have no space to do that for the rest of the system. The only thing that is missing then are the installed packages, so for each re-install i have to remember what packages i used and run apt-get a thousand times until it is like before. Also quite a task to install it on a new computer with the same setup.

So, is there a way to make apt-get spew out a list of all currently installed packages into a text file that i can later feed back into it to install just these? I see it in all the graphical frontends, so it must somehow work.

Would really appreciate a hint, thanks,
drx

---

### Post by Teh Ethan on 2006-03-16
```
dpkg -l
```

---

### Post by drx on 2006-03-17
ThanXorz!!

---

### Post by bluevoodoo1 on 2006-03-18
[QUOTE=Teh Ethan]```
dpkg -l
```[/QUOTE]

Very good to know!

---

