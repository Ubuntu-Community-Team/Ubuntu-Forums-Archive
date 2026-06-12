---
title: "hard drive check interval"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by jvdbossc on 2012-12-15
I am building up a p 4 system with ubuntu 10.04, it works good and user is happy. (one week)

Though I *think* the hd is in failure, but can't proove smart say's it's ok. 

Therefore I would like to force the file system check more frequent, or maybe if it can be speed up'd every boot..  Is there a way?

---

### Post by mbohets on 2012-12-15
You can use this command to change the diskcheck interval.
[FONT=Arial, sans-serif][SIZE=1][FONT=arial][FONT=arial][SIZE=2]
sudo tune2fs -c 100 /dev/sda2

[SIZE=2]In this case the disk /dev/sda2 will be checke[SIZE=2]d after [/SIZE][/SIZE]100 [SIZE=2]b[SIZE=2]oots[/SIZE][/SIZE]

[/SIZE][/FONT][/FONT][/SIZE][/FONT]I did just the opposite, as you would like to do and put the value to 1000.

---

### Post by jvdbossc on 2012-12-16
Thanks, that works!  I've set it to 2.  He is a smoker, so I suggested to put the pc on and grab a coffee and have a smoke.  There something wrong with his system, but can't identify it for now.

---

