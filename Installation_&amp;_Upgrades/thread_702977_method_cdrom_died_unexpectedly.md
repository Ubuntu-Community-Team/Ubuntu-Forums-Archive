---
title: "method cdrom died unexpectedly"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by fiorinija on 2008-02-20
here's what im doing...

sudo apt-get install xubuntu-desktop

then i insert the cd into the drive, it reads to about 4% and then it says this

E: Method cdrom has died unexpectedly!

Anyone have ANY idea of what this means? why does it keep saying that. I can't find any place on the internet that can tell me why this happens.

---

### Post by corevette on 2008-02-20
so i'm taking you want xubuntu and you have ubuntu at the moment
if you have internet...you don't need to install through the cd

just go to System -> Administrative -> Software Sources
and uncheck the ubuntu cd
then reload/update the repositories

and then do 
```
sudo apt-get install xubuntu-desktop
```

---

### Post by zvacet on 2008-02-21
You need alternate CD to do that.

---

### Post by fiorinija on 2008-02-21
actually when i installed xubuntu for some reason it didnt give me the xubuntu desktop, so im trying to get the desktop from the terminal mode it gives me when xubuntu starts

---

### Post by zvacet on 2008-02-21
In terminal type** startx** and if you have xubuntu desktop installed it will start to work.Maybe it is good idea to check [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and check CD for errors(you have that ption when you boot CD).

---

