---
title: "help backing up system to load on new hard drive"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by petee1979 on 2008-08-10
Hi All

i am running kubuntu 8.04, i am about to get a new harddrive in my laptop and dont really want to load ubuntu from scratch then download all the stuff i have on here again, is there a way i can back this up to dvds or something then put it back to the new drive so i am up and running as i am now?

thanks for any help
Pete.

---

### Post by Pumalite on 2008-08-10
This might help:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by ajgreeny on 2008-08-10
You may need to edit the /etc/fstab file in your restored backup to get it to boot, however, as I think the formatting of the new drive will probably give it a new UUID, and now Ubuntu works on UUIDs and not /dev/sd* as it used to.  I may be wrong about the need, but forewarned is forearmed.

---

### Post by logos34 on 2008-08-10
well, let's put it this way: if you were to simply do **cp -a **then you'd need to edit menu.lst and fstab to adjust the UUIDs....but if you copy the partitions using partimage, G4L, Clonezilla, dd command, Gparted (copying/moving option), or whatnot, then the UUIDs would be copied along with the partitions, so no need to worry about it, except maybe write grub to mbr of the destination drive

---

### Post by ajgreeny on 2008-08-10
Thanks logos34, I was uncertain about that, but it's good to know.
However, not knowing about clonezilla, etc, I assumed you needed to format the destination disk before you use the program, so would that not change it to a new UUID, or does the restoration of the clone with clonezilla do the formatting and give it the right UUID?

---

### Post by logos34 on 2008-08-10
> **ajgreeny said:**
> Thanks logos34, I was uncertain about that, but it's good to know.
However, not knowing about clonezilla, etc, I assumed you needed to format the destination disk before you use the program, so would that not change it to a new UUID, or does the restoration of the clone with clonezilla do the formatting and give it the right UUID?


when you clone a partition or an entire disk EVERYTHING is copied--UUIDs included.  Basically you just indicate the destination drive--no need to format it because the copied partition(s) will overwrite whatever is there (or not there in the case of unallocated space).

---

### Post by petee1979 on 2008-08-10
hi 

thanks for your help i loaded the website up and it tells me everything i need

thanks again 

Pete.

---

### Post by bouncingmolar on 2008-08-10
> **logos34 said:**
> when you clone a partition or an entire disk EVERYTHING is copied--UUIDs included.  

So if you copy your partition using gparted does that mean two partitions will have exactly the same UUID? How do I get grub to tell them apart?

---

### Post by logos34 on 2008-08-10
> **bouncingmolar said:**
> So if you copy your partition using gparted does that mean two partitions will have exactly the same UUID? How do I get grub to tell them apart?

I don't know why you'd want to keep two copies around, but if you do you'd need to change the UUID on one of them:

sudo tune2fs -U random /dev/sd??

---

### Post by bouncingmolar on 2008-08-11
> **logos34 said:**
> if you do you'd need to change the UUID on one of them:

sudo tune2fs -U random /dev/sd??

Cheers that was the push i needed to solve my problem ([migrating to another partition]("http://ubuntuforums.org/showthread.php?t=886154"))

---

