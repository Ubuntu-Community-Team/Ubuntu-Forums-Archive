---
title: "partitioning"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by abdolah on 2012-03-09
hello
i have installed dual windows 7 and ubuntu ,ubuntu is  on drive D to use 15G of it ( drive size if beyond 70G) , now when I am in ubuntu it shows me all partitions, but it does not show me other files and folders on drive D except for 15 G of itself.
how i can access other files also?

---

### Post by sudodus on 2012-03-09
Have you installed dual boot with linux partitions or have you a wubi install? If wubi, the windows data should be found at
```
/host
```
If you have dual boot, you can run the following commands and post the output in a reply.
```
sudo fdisk -lu
```
```
df
```

---

### Post by pavi_elex on 2012-03-09
They will be here:
```
Places >> Computer >> File System (Icon) >> Host (Folder)
```

Suppose you have installed it in** C:\>** drive
**Desktop:**  Users >> (Your Username) >> Desktop
 **My Documents:** Users >> (Your Username) >> Documents
 **Program Files:** Program Files or Program Files(x86) under your Host folder

---

