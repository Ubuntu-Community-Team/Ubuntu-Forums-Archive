---
title: "Dell Inspiron 6400...which Ubuntu?"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by kazzybee on 2007-02-08
[COLOR="Purple"][FONT="Comic Sans MS"][SIZE="5"]I have the Dell Inspiron 6400 laptop that came installed with Win XP. I have today, along with my Uni lecturer spent 3 hrs trying to install Ubuntu 6.0.6, Edgy 6.10 & 5.10 firstly from the live discs but we could get no wireless connections (the wireless is fine in Win XP), we then went for the full install but were stopped because there are already 4 partitions, 2 I understand as C & D drives, 1 I assume is recovery programs from Dell that is hidden, have no idea what the 4th partition is, but when we tried to install it stated only 4 partitions allowed......I then bottled out.
 
Can anyone assist please as the module for this semester has all to be done in Linux, so having it on my laptop will save hours & hours of driving.
 
Thanks
 
Kazzybee

PS Have had nothing back from Dell, as yet!:confused: [/SIZE][/FONT][/COLOR]

---

### Post by banditti on 2007-02-08
First, I like standard Ubuntu

Second, a couple of things to check: 

[http://ubuntuforums.org/showthread.php?t=274915&highlight=dell+6400](http://ubuntuforums.org/showthread.php?t=274915&highlight=dell+6400)

[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)


Hope that gets you going.  Shouldn't be too bad.

---

### Post by housam on 2007-02-08
Dell laptops  always comes with 2 hidden partitions , one as a recovery and the other as utilities.and they are small in size. 
You only permitted to have only 4 primary partitions in a HDD. so you have to delete one of the other partitions ( let say D ) . After deleting the partition ,you can transform it to an extended partition which can be divided to many logical partitions. then you can go for the install.
Use Gparted for partitioning. it is on the live CD.
Ubuntu needs at least 2 partitions: one for the root ( / ) ext3 format and the other is swap format for the swap partition.

---

