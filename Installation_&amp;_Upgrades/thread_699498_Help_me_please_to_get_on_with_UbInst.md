---
title: "Help me please to get on with UbInst"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by NewDummie on 2008-02-17
Starting to install Gutsy on laptop (ASUS). 
Allready have WinXP on C,D drives, NTFS. 
Want to install Ubuntu on F of G, FAT32. 
Using DVD unleashed at a moment. Stuck at the beginning. After setting up languages I was offered to choose partition. I dont need to use entire drive wich consist of C,D,F,G (as above). I want to have it on F. And I wanted to do it mannualy  -  I couldnt. 
What should I do, press, type etc. Help.

---

### Post by Pumalite on 2008-02-17
If you can boot a Live CD, post:
sudo fdisk -lu

---

### Post by NewDummie on 2008-02-17
Dear Guru,
this is only lists all details of my hard rdive but I need to post
something will help to point Ubuntu itself where to go, where to start laying on. Sorry Im very new to all these but want to be able to get on...

---

### Post by cybergalvez on 2008-02-17
> **NewDummie said:**
> Dear Guru,
this is only lists all details of my hard rdive but I need to post
something will help to point Ubuntu itself where to go, where to start laying on. Sorry Im very new to all these but want to be able to get on...
[http://www.google.com/webhp?hl=en](http://www.google.com/webhp?hl=en)
When you get to the section where you have to partition  your drives select manual, delete the fat32 partitions and then create two new ones, you will need a swap partition and a root partition mounted as swap and "/" respectively. Once the partitions are created everything should go as planned.  
Jose

---

### Post by Pumalite on 2008-02-17
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Tutorials:
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

Welcome.

---

### Post by NewDummie on 2008-02-20
Thanks leds. All works. Will try to go deeper (mad), to tune the OS...

---

### Post by Pumalite on 2008-02-20
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by NewDummie on 2008-02-21
Hi everyone.
Why I cant create any file in /etc being supervisor? Ubuntu...

---

### Post by Partyboi2 on 2008-02-21
what happens if you open nautilus as root.
Press Alt+F2 then type
```
gksudo nautilus
```

---

### Post by NewDummie on 2008-03-04
Cant manage wifi. Permanently ON.  Laptop - ASUS A6T. 
Id like not to have it on by default when system starts also. help...

---

