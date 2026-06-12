---
title: "Bad Update :("
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Phentis on 2010-04-09
Good Day!

Today I tried to update my Ubuntu 10.04 to Beta2. The first bad thing was that it told me, that only partial update is possible. I agreed.

After the update everything was okay, until I reboot. After the reboot, I have interface problems:
1) The mouse "arrow" is now a "black cross"
2) The windows top-line has disappeared (name of the window, buttons "minimize", "maximize", "close")
... and many other appearance problems :( Sorry, I can't even make a screenshot.

What can be the problem and the solution?

Thanks in advance!

---

### Post by lisati on 2010-04-09
Moved to  Lucid Lynx Testing and Discussion

---

### Post by mörgæs on 2010-04-09
Partial updates are dangerous:

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by descendent87 on 2010-04-09
Sounds like gnome-compiz has been removed, read here [http://ubuntuforums.org/showthread.php?t=1450282/](http://ubuntuforums.org/showthread.php?t=1450282/)

---

### Post by sonicb00m on 2010-04-09
sudo apt-get install compiz-gnome

---

### Post by sdowney717 on 2010-04-09
just keep updating, it will fix itself when they get all the pieces of the software puzzle right.

You can open a terminal and type in

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Phentis on 2010-04-10
Thanks, but I've already re-installed Ubuntu.

Will not accept any partial updates in the future :)

Thanks everybody for your answers!

---

### Post by sonicb00m on 2010-04-10
i dont think the partial update was the problem in this case. I did a full dist-upgrade and still had the trouble with gnome compiz.

---

