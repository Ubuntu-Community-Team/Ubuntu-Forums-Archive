---
title: "getting started"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by tbeal441 on 2006-06-10
Yes ive just recently decided to try out linux ubuntu on my second pc. i went through the whole install process and deleted windows off the partition and installed linux and when it rebooted every thing went just fine and then i got a prompt for user name i entered the one i created in the install and then password and i did the same and then it just gave me a new prompt after i signed in. my question is how do i get to the desktop in this operating system? i am new to linux and just heard so many great things about it and would like to give it a try so i would appreciate any help that can be provided. is there something else im spose to type in to get to the desktop?

---

### Post by aysiu on 2006-06-10
Theoretically, you should have already gotten a desktop, unless you did a server install, which is kind of hard to do by accident.

So right now, you get a login, and if you log in, you get a white prompt on a black screen that says ```
tbeal@ubuntu:~$
``` right? If so, type these commands, and you should be good. ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

