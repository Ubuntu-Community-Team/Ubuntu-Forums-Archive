---
title: "Partition Limits"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by markcynt on 2008-02-13
I have 3 partitions on **2 hard drives arranged as 1 (JBOD****)**. 2 partitions have XP Pro 1 has Vista Ultimate. I heard that I can only have 4 partions per hard drive. Will this prevent me from adding Ubuntu to my system? 

Thanks
 Mark

---

### Post by housam on 2008-02-13
You can have only 4 primary partitions for a single HDD. but you can change one of them to an extended partition which can be devided to many logical partitions using the Gparted tool ). so, you can install ubuntu on any 2 of them ( one for the root ( / ) and the other one for the swap ) you can also asign a third for ( /home).

---

### Post by markcynt on 2008-02-13
Can I use Acronis to accomplish this? How many partitions does the ubuntu install use?

Thanks
Mark

---

### Post by housam on 2008-02-13
> **markcynt said:**
> Can I use Acronis to accomplish this? How many partitions does the ubuntu install use?

Thanks
Mark

I don't Know about Acronis. Use Gparted tool ( on the live CD ) it is very good in resizing and formating the partitions.

Ubuntu can be installed on only 2 partitions ( one for the root ( / ) and the other for the swap )

---

### Post by markcynt on 2008-02-13
Okay, sounds good. So I will need to make an extended partiton and that will have at least 2 partitions inside?

Thanks
Mark

P.S. I am a novice at best. I can work with software but I can't work with command lines unless instructions are very specific.

---

### Post by markcynt on 2008-02-13
Okay I made the live gparted cd. Now how do I use it? Do I run it in windows or boot to the cd?

Thanks
Mark

---

### Post by housam on 2008-02-13
> **markcynt said:**
> Okay I made the live gparted cd. Now how do I use it? Do I run it in windows or boot to the cd?

Thanks
Mark

You have to boot from Gparted live cd .

---

### Post by markcynt on 2008-02-13
Remember I'm a Windows user. What is "/home" in a partition? Is it a backup partition?

Thanks
Mark

---

### Post by housam on 2008-02-13
> **markcynt said:**
> Remember I'm a Windows user. What is "/home" in a partition? Is it a backup partition?

Thanks
Mark

A /home partition is what you can store your data on it. you can also use a fat32 partition instead  as a separate data storage partition and it is accessable from ubuntu and windows.

---

### Post by housam on 2008-02-13
You can also read this guide to know about partitioning for linux.
[[COLOR="Red"]http://www.linux.com/base/ldp/howto/Partition/requirements.html#number]("http://www.linux.com/base/ldp/howto/Partition/requirements.html#number")[/COLOR]

---

