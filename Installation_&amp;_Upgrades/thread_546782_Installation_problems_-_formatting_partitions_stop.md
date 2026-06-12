---
title: "Installation problems - formatting partitions stops at 5%"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Marianne_S on 2007-09-09
I am new to ubuntu and i am not a very technical person, so who ever helps me with this needs to dumb it down as much as possible. 

I tried to install ubuntu. i chose guided - entire disc - and when it started formatting the partitions it stopped at 5% of the first partition. After waiting for hours i rebooted my computer - which i fear i shouldn't have done. When i try to install it again it stoppes at 5% .

this is the computer i have:  [https://www.komplett.no/k/ki.aspx?sku=336528&view=detailed](https://www.komplett.no/k/ki.aspx?sku=336528&view=detailed)

what can i do to fix this? i hope i havent broken my computer :(

---

### Post by Pumalite on 2007-09-09
Use Gparted (the stand alone, burn to CD, boot from it program): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)

Make one large partition out of your hard drive. Format ext3 and then install>Guided>Use Entire Disk

---

### Post by Marianne_S on 2007-09-09
I'm sorry but that wasnt dumb enough for me.

The stand alone?

do i need to rezise the partitions? 

uh  I am very confused and lost. 

Thank you for trying to help me

---

### Post by Pumalite on 2007-09-09
The installer does the partitioning for you after you have prepared your drive with Gparted. Ubuntu cannot install on 'unallocated' space.

---

### Post by Marianne_S on 2007-09-09
uh ok. can i do this when i have no functioning operating system?

---

### Post by Pumalite on 2007-09-09
You are going to have to go to a friend to download the Gparted iso and burn to a CD. Then you can go to your computer and boot from it.

---

### Post by Marianne_S on 2007-09-09
thank you :D

---

### Post by Pumalite on 2007-09-09
You are welcome. Good luck.

---

### Post by hessiess on 2007-09-09
the ubuntu live cd has gnome partition editor on it. system-administration-gparted.

delete any existing partitions

salect unalocated in the list, click on new, leve options defalt and click ok, then apply

---

### Post by Marianne_S on 2007-09-10
I followed heisseiss instructions. but there were a swap partition i couldnt delete. so i talked to a friend who suggested i should do the partitions manually. first delete the ones that were there than make one root one swap and one big one called home. He also suggested that since i had problems with  the ext3 format that i should do them (root + home) in reisersf. however when i tried to make the last - home - partition i get the error message "can't have the end before the start" 


i am adding pictures cos i'm not good at explaining:

1:
[http://farm2.static.flickr.com/1348/1351394953_eeaf79cecc.jpg](http://farm2.static.flickr.com/1348/1351394953_eeaf79cecc.jpg)

2:
[http://farm2.static.flickr.com/1230/1351394991_89b912c947.jpg](http://farm2.static.flickr.com/1230/1351394991_89b912c947.jpg)

3:
[http://farm2.static.flickr.com/1007/1351394961_ca15fc9fa4.jpg](http://farm2.static.flickr.com/1007/1351394961_ca15fc9fa4.jpg)

4:
[http://farm2.static.flickr.com/1089/1351394997_e4fff5f74a.jpg](http://farm2.static.flickr.com/1089/1351394997_e4fff5f74a.jpg)

5: 
[http://farm2.static.flickr.com/1344/1351394979_ab1edcbd3f_o.png](http://farm2.static.flickr.com/1344/1351394979_ab1edcbd3f_o.png)

(this is taken the second time i tried, so the sizes of the files are a bit different)

any suggestions what the problem is?
and how to solve it?

---

### Post by Marianne_S on 2007-09-10
Update: i found this : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787)

and after talking to my friend again i made the root partition bigger - so the home partition wasnt bigger than 180 gb - and that worked . i have installed ubuntu succesfully - finally. 

yippie :D

---

