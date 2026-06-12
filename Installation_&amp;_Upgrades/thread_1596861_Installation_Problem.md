---
title: "Installation Problem"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by agwatic on 2010-10-14
hope not bothering u :)
i got a 640-western hard drive and i made two primary partitions one for windows 7 which is already installed and the other for linux 
my problem starts where i tried to install ubuntu 10.10 in the other partitions but during installtion it reads the WHOLE HARD as ONE PARTITION and it is empty though i had alot of data separated on the whole partitions 
when i go to "computer" it ONLY shows me THE TWO PRIMARY PARTITIONS and also i can't make any process on my two primary partitions shown "computer"
help me ASAP please :)

---

### Post by oldfred on 2010-10-14
From liveCD in terminal (applications, Accessories, terminal) post this:

```
sudo fdisk -lu
```

---

