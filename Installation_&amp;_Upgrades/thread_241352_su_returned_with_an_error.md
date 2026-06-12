---
title: "su returned with an error"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by xunq on 2006-08-22
hi i putted up my wifi realtek card up and after want i download opera
for linux but i cant save the file in system settings/user&groups make i a little changes that i can under my login make everything save files etc. after ther in the root figure xunq@vigor10
but whats this login in to my rooter](*,)  
i will make changes in settings but i become a failure:su returned with an error
i a total fresh newbie and i wan use kubuntu

pleaz help me

ps:why is my internet so slow under kubuntu?:confused:
Thnx

sorry for my poor english i from slowakia:(

---

### Post by Paul41 on 2006-08-22
In Ubuntu you use sudo instead of su.

---

### Post by xunq on 2006-08-22
i typed in run command sudo -i and become this:

sudo: unable to lookup Vigor10 via gethostbyname()
next problem with time and i cannot login as administrator
:confused:

---

### Post by Paul41 on 2006-08-22
Use sudo with each command you want to run as root, so for example:
```
sudo apt-get update
```

---

### Post by xunq on 2006-08-22
nothing help i will better instal kubuntu for new
i dont know what i maked whit my stupid head](*,)

---

### Post by xunq on 2006-08-22
the point is i reboot in rescue mod i login and startx i have a root access to everything but my user name xun is added to admin group in the command line figure root@vigor10 this is my rooter and when i boot normal login with my xun name i dont have access to nothing

question: how can i add my name "xun" really to admin group and have access to everything ?:confused: 

help pleaz help to me lama :frown:

---

### Post by Paul41 on 2006-08-22
Does this help?

[http://www.ubuntuforums.org/archive/index.php/t-9890.html](http://www.ubuntuforums.org/archive/index.php/t-9890.html)

---

### Post by abalone on 2006-09-19
I'm having the same problem.

I believe it started after mis-adjusting the system time. It's happened before. Can't remember what I did to fix it, or if it fixed itself.

kdesu pops up a dialog box saying "Su returned with an error." No details. kdesu is used extensively by KDE - for example to adjust time and date. The "Administrator Mode" button on some control panels gives the same error.

I could still sudo for a while, though, and saw that my regular user account **was** in the admin group, **and** in sudoers.

Some ten minutes later, though, I'm getting this:
blah@bleh:~$ sudo whatever
sudo: timestamp too far in the future: Sep 19 10:07:58 2006
(I set my system time several hours back.)

Well. I'll see what changing the time in recovery mode will accomplish.

Anyway, it's no attempt to violate the Ubuntu sudo dogma; it's something going rather wrong in ordinary desktop use.

---

