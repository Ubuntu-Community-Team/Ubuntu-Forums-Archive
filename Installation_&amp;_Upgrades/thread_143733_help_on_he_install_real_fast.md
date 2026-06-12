---
title: "help on he install real fast"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by pestypest on 2006-03-13
ok i fallowed this guide [https://wiki.ubuntu.com/WindowsDualB...ght=%28boot%29](https://wiki.ubuntu.com/WindowsDualB...ght=%28boot%29)  when i got to the part where it asked me to partion i did what it said and did it manually. i am confused as to which one i choose to partion there is a drive that says  SCSI2 (0,0,0) (sda) - 100.0GB ATA  then next line down
 #1 primrary 100.0GB :)  ntfs  /media/sda1.   i need to know which one to partion so i dont kill doze in the process.   any help would be great. Thanks

---

### Post by byen on 2006-03-13
oops nevermind. The reply below seems more sensible!

---

### Post by jannol on 2006-03-13
If you only have one partition as it seems, the first line tells what disk it is and then what partitions there are on it.

You can look here [http://linux.jannol.com/ubuntu/partition_setup/](http://linux.jannol.com/ubuntu/partition_setup/)
where there are a bunch of screenshots of an example how to resize and make your partitions and at the bottom there is a demo of the same example. Maybe you find that helpful.

---

### Post by pestypest on 2006-03-13
[QUOTE=byen]The one with NTFS would be the one which has Windows on it! Does it not show the free and available space beside the HD Drive? I say that "#1 primary 100.0GB  ntfs /media/sda1." is windows (xp?) because Windows XP uses ntfs as its filesystem... but which format is the other drive? I would like to make sure that that is not NTFS as well...cuz then...we might wanna look into this further!!![/QUOTE]
 i only have one drive installed.

---

### Post by byen on 2006-03-13
Sorry...I just realized that...I would suggest the links that jannol has given you. The images will give you an idea as to how to proceed!

---

### Post by pestypest on 2006-03-13
[QUOTE=byen]Sorry...I just realized that...I would suggest the links that jannol has given you. The images will give you an idea as to how to proceed![/QUOTE]
 ok im looking at the pics and i am understandig on which dirve to partion. in the GUIDE i linked in my first post. it said to enter in which number in GB's for the partion i tri that and it says to small.  It also says i need to use 59% free which i did the defrag and said i had 40% free when done. any suggestions?

---

### Post by jannol on 2006-03-13
I'm not sure what you did but I think you need to put eg GB letters when entering the size or MB

eg. 40000 MB is approx 40 GB

or

eg

40 GB that is 40 GB

Sounds like you didn't and ended up with a lot of free unused space, I am not sure how to guide you but if you did wrong you could delete the newly made partition that is not NTFS.

Also, always always make sure you have backups of all your important stuff incase something goes wrong.

---

### Post by pestypest on 2006-03-13
[QUOTE=jannol]I'm not sure what you did but I think you need to put eg GB letters when entering the size or MB

eg. 40000 MB is approx 40 GB

or

eg

40 GB that is 40 GB

Sounds like you didn't and ended up with a lot of free unused space, I am not sure how to guide you but if you did wrong you could delete the newly made partition that is not NTFS.

Also, always always make sure you have backups of all your important stuff incase something goes wrong.[/QUOTE]
i made sure it looked like it should using GB says GB in the partion disks screen im on now. it sounds like it wants to use all my free space on the HD? another question is should i try the first ATA dirve the i explained? because i a few more options when i chose that one.

---

### Post by jannol on 2006-03-13
what options do you have and what does you partitions look like at the moment?

---

### Post by byen on 2006-03-13
I am a little stumped here... Now...does it show the amount of free space?
What if you use the select amount of space and choose an option for it to be partitioned (use "end" to be safe ) in terms of MB? say like:
>Create New Partition
>New Partition size xxxxMB

It will format a part of the remaining patition to create a new one depending on what you have asked.

EDIT: Could you tell us what you see on the screen at this moment?

---

### Post by pestypest on 2006-03-14
ok WOOT i got it installed with the help of JANNOL thanks man.

---

### Post by jannol on 2006-03-14
I forgot one detail at first when resizing, it asks for new size of c and not how much you wanna free, also there might been some other issue but anyways, great that you got it installed pestypest

---

