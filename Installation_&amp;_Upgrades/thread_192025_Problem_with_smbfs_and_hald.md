---
title: "Problem with smbfs and hald"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by pminetti on 2006-06-08
Hi!
after upgrade from 5.10 to 6.06 I have problems with these two things

on my fstab I have this line that works ok in 5.10

//cecilia/Documentos /mnt/cecilia smbfs rw,username=xxxxxxx,password=xxxxxx,users,dmask=777 0      0

but in new 6.06 when system boot, the hald stop several minute and then say OK
but when I want to connect to /mnt/cecilia there's no connection

if I comment the line in fstab, and I boot the system, when it reach hald, say ok 
then I edit my fstab, uncomment the line,  then sudo mount -a and all works ok, I can connect to /mnt/cecilia.

any idea?

---

