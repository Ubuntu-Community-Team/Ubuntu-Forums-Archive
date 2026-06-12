---
title: "can i install without formatting"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by toben7l on 2005-08-22
can i install Ubuntu on my HD on my laptop without formatting it? i'm running WinXP Home Second Edition on a Compaq Presario 2100 laptop right now, but i don't have enough space on my second HD or enough CD-R's to perform a backup

---

### Post by jasmuz on 2005-08-22
You dont necesarily need to format the existing partition, but you MUST resize it to make enough space for the root partition (minimal 2gb) and swap partition (2x your ram).

---

### Post by bored2k on 2005-08-22
[QUOTE=jasmuz](...) and swap partition (2x your ram).[/QUOTE]
Not entirely true nor necessary. My swap is only about 30% bigger than my ram amount and I've never encountered any problems with it.

---

### Post by 0vermind on 2005-08-22
I had this problem with my Windows 2000 computer, I fixed it with a type of partioning call "resizing partions". The programs take free space from one partion and makes it avaible to create a new partion. I used this tool called [Bootit NextGen](http://terabyteunlimited.com/bootitng.html). It makes a boot disk to bootup. Then, just click resize and lower down your hardrive about 1.9-2.1 GB (or 400 MB for server). Create a new partion and walla, a partion for Ubuntu Linux.

Al you have to do after this is boot up Ubuntu CD and install it on the partion (it will say 2.1 GB Free Space or whaterver the amount of space you gave it).

Hope this help you,
0vermind

---

### Post by toben7l on 2005-08-22
thanks for the help. appreciate it :)

---

