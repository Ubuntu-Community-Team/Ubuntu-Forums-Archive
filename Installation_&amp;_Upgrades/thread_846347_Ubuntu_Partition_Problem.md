---
title: "Ubuntu Partition Problem"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by lotrkev on 2008-07-01
After installing Ubuntu Hardy, whenever I try to install the partition (after you select your timezone), it gives an error message that it won't work. It says that the error is "Exit 10" or something. When I click continue anyway, it goes to the login screen and it wont let me login; it supposedly logs in but then goes right back to the login screen. When I look on my hard drive in windows, there is space taken up by ubuntu, so I think the partition might have worked. If this problem can't be fixed, how do I get rid of ubuntu from the hard drive?

---

### Post by mikewhatever on 2008-07-01
Can you please elaborate on what do you do to 'install a partition', I am not quite sure what it means. Also, is it a blank HDD?

---

### Post by lotrkev on 2008-07-01
The hard drive is not blank (I am running windows too), but there is plenty of room; and what I mean by "installing the partition" is that when you install Ubuntu on a new computer, and boot it up, a setup screen comes up (where you tell it your city time zone), saying it is "setting up" or "installing" the partition, I can't remember which.

---

### Post by mikewhatever on 2008-07-01
Here is a link to graphical installation [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall). It looks like setting the time zone screen appears quite a bit before you have to deal with partitions. Perhaps, following that guide will help, anyway, I've never seen the kind of error you got. Hopefully someone else might come up with a solution.

---

### Post by upchucky on 2008-07-01
apparently exit code 10 is a script error when packages fail to install
check the cd you are using and your internet connection, perhaps the network is not getting set up before it tried to get packages, try to set time zone later if it will let you.

---

