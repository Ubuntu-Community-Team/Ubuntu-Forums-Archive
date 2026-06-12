---
title: "asus p5gdc deluxe"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by copycat on 2006-08-21
After working with Dapper for some weeks on my portable, I want to install it on my client her pc. The motherboard is a p5gdc deluxe with the latest bios.
Dapper is always giving I/O errors while booting up.  (b/w screen)  Something about translating error..etc. The pc works fine on XP so there are no errors on the disk.  I disabled already the raid option. I changed the IDE settings from enhanced to compatible but the the pc doesn't find the sata HD.  Even when it is on p-ata and s-ata it only finds the DVD/CD-R and no disk.

---

### Post by copycat on 2006-08-22
Found the solution.

Just press control-c when you see "Enterprise Volume Management System" while starting up.  I hope the further install will work now. :) 

grtz,
Copycat

---

### Post by copycat on 2006-08-22
Update...the livecd boots fine...I can see the 2 ntfs partitions on the 200Gb Maxtor.  Starting the install works fine untill we need ot select the disk to format (5'th step).  I'm waiting for 10 minutes now an nothing is changing.  Am I the only one with this problem?  I really want to install Dapper on that PC.

 Linux rulez :-)

---

### Post by borobudur on 2006-08-23
It looks like it's a missing driver for the Enhanced IDE. I have the same problem with a P5LD2 Asus Motherboard. I found this post in the asus forum:

[Post in Asus Forum]("http://vip.asus.com/forum/view.aspx?id=20060809150143191&board_id=1&model=P5LD2&page=1&SLanguage=en-us")

I can use the IDE slots not the EIDE. 
Please tell me if you found a solution.
borobudur

---

