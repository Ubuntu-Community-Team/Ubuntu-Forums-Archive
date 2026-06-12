---
title: "[SOLVED] Permission Denied (I am getting a persecution complex ;))"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-05-22
I am trying to install alien.
This is what I get:
bash: alien: command not found
peter@Shop:~$ aptitude install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I seem to be forever running into this permission denied. I am the oly person on this computer and the one who installed it. Why am I not authorized????

---

### Post by tamoneya on 2008-05-22
you need to preceed the command with sudo.```
sudo aptitude install alien
```

---

### Post by Stolea on 2008-05-22
Thanks, I am now slightly less paranoid :)
Qusetion:
I Windoze I place all downloads in a directory called "Downloads" and I have subdirectories like "Programs" Internet" Utils"
Where is the correct place to keep downloads on a Linux system? and how does aptitude or apt-get know where to find a downloaded driver or application?

---

### Post by Pumalite on 2008-05-22
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

---

