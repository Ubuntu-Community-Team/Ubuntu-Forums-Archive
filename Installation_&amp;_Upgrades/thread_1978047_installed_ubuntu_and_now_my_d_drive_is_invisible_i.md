---
title: "installed ubuntu and now my d drive is invisible in windows"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by sethvibhu7 on 2012-05-11
i recently installed ubuntu with my windows but in different drive
(infect different hard disks) 

in c drive(80 gb) there were windows and 
in d drive(500 gb) i installed ubuntu 

now when i boot in windows i cant see d drive which had all my data
(around 300 gb)
and when i boot in ubuntu i can see the 500 gb hard disk but not its content 

please help me 
and also help in retrieving my data

---

### Post by sethvibhu7 on 2012-05-11
any one plz help i m on the verge of losing 300 gb data

---

### Post by nothingspecial on 2012-05-11
Please do not bump your thread more often than every 24 hours or so.

Are you sure you didn't format the entire drive when you installed Ubuntu?

What, exactly did you do during the installation. Is this a wubi install or a full one.

---

### Post by sethvibhu7 on 2012-05-11
i installed it using the option install within windows only

and m not sure about formatting 
but yea it did asked me to make partition in 500 gb hard disk then i chose to make 75 gb partition in 500 gb hard disk

---

### Post by wilee-nilee on 2012-05-11
> **sethvibhu7 said:**
> i installed it using the option install within windows only

and m not sure about formatting 
but yea it did asked me to make partition in 500 gb hard disk then i chose to make 75 gb partition in 500 gb hard disk

Run on a ubuntu live cd this command and post it. If you have erased anything you have to stop using that HD if you want to recover anything.

```
sudo fdisk -l
```This l is a small L

---

### Post by darkod on 2012-05-11
> **sethvibhu7 said:**
> i installed it using the option install within windows only

and m not sure about formatting 
but yea it did asked me to make partition in 500 gb hard disk then i chose to make 75 gb partition in 500 gb hard disk

To make a partition or it asked you how much space you want to allocate to wubi? There is a difference.

If it only allocates 75GB it will create a folder with that size, it will not create new partitions.

In any case, as wilee said, run the cd in live mode (if you don't have ubuntu cd make one), and post the result of the command he posted.

---

### Post by Rubi1200 on 2012-05-11
Hi,
you should go with the suggestions made by wilee-nilee and darkod before doing anything else.

If you do get a LiveCD/USB going then I also recommend you run the boot info script and post the results here.

There is a link at the bottom of my post with instructions.

Thanks.

---

