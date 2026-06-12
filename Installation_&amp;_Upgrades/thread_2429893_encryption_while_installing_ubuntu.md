---
title: "encryption while installing ubuntu"
date: 2019-10-24
forum: Installation &amp; Upgrades
---

### Post by roy13242 on 2019-10-24
hy guys 
so i wont to install ubuntu and encrypt my ssd drive that i'm installing ubuntu in it and i wont to know if the encryption will encrypt the whole drive 
like the root partition, data partition and i read that the boot partition will not be encrypted so can you tell me if its true or not and if not 
what the encryption option is encrypting ?

---

### Post by slickymaster on 2019-10-24
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by uRock on 2019-10-24
If you select to install using LVM encryption, then it encrypts all of the ubuntu partitions.

---

### Post by roy13242 on 2019-10-24
i can't mark both boxes off encryption ? the LVM encryotion do both options ? 
and what is the diffrerent between them

---

### Post by roy13242 on 2019-10-24
> **uRock said:**
> If you select to install using LVM encryption, then it encrypts all of the ubuntu partitions.

i can't mark both boxes off encryption ? the LVM encryotion do both options ? 
and what is the diffrerent between them

---

### Post by uRock on 2019-10-24
You have to have both checked. If you mark to just do LVM, then it will just create the partitions. I apologize for not clarifying that in my earlier post.

---

### Post by roy13242 on 2019-10-25
> **uRock said:**
> You have to have both checked. If you mark to just do LVM, then it will just create the partitions. I apologize for not clarifying that in my earlier post.

O.K  thanks for the help 
can you also tell me why in this article they show different method and it look more complicated ( i saw this method in more articles like this )  : 
[https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-19-04-b50bfc65182a](https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-19-04-b50bfc65182a) 
there is any different in between them ?

---

### Post by uRock on 2019-10-25
That may be something one has to do when dual booting. I haven't dual booted for several years and when I did my system was too weak to handle encryption and be snappy. If not needed for a dual boot, then I honestly have no clue why someone would have to go that round about way of doing it.

---

