---
title: "format/partition help"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by verlooy on 2007-02-03
Hi, Im fairly new with linux, i recently just bought ubuntu, well got a book on it that came with a cd. Now, im trying to install it on my master drive, i got 2 drives, 1 80gb drive and 1 40gb drive. The 40gb drive has windows xp on it, i hear that if you got xp on it you should put it on slave so that when you install ubuntu on the master you can just switch to xp on the boot. 
SO, i got 2 drives hooked up, 80gb with no partitions on it set as master, and the 40gb set as slave with xp on it. I tryed automatically formatting my 80gb with ubuntu and it always freezes on 74%, so then i tryed manualing doing it. Using ntfs on /dev/hdb1 then putting partition #1 on etc and partition #2 as linux swap, then after clicking forward  i used 

/media/hdb1  20gb partition 1
/boot 100mb partition 2 
swap 640mb partition 3
/ 20gb partition 4

After clicking forward it tells me something about not being able to send system files on fat32 or ntfs

note, i never made 2 #partitions on etc i think i was so pose to?

---

### Post by taurus on 2007-02-03
You cannot install Ubuntu on ntfs or fat32 filesystem.  You need to format it to ext3 (which is a default) so try that and see what happens.

---

### Post by verlooy on 2007-02-03
lol ya your probally right, im so stupid, ill try it after work\

Do you think it will get rid of the error that i get at 74% when it installs? Because i was getting that when i was automatically installing ubuntu

---

### Post by verlooy on 2007-02-03
well i got my manual install to work this time, but now it freezes at 33% lol. SO i donno what i should do now i feel like ive tryed everything, its a brand new western digital hd , i dont know much about linux , but i do no i manualy installed it correctly and it doesnt work by doin that or automatically it keeps freezing at a certain point usually 74% on auto and 33% doing it manually

---

### Post by taurus on 2007-02-03
Did you check the integrity of your ISO image before you burned it?  And how fast did you burn it anyway?  Make sure you burned it at a slow speed like 4x.  Also, did you run the check CD option at the first screen?

---

### Post by verlooy on 2007-02-03
the check said it was fine, but i donno i got it from the book lol so i dont think there is anything wrong with it. Thats why i really wanna get this thing formatted on my hd because i got a book on ubuntu, i donno the cd looks fine with no scratches on it

---

### Post by verlooy on 2007-02-03
eh i got it working now thanx tho, im so happy

---

