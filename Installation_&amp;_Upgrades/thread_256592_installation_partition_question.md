---
title: "installation partition question"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by dracule on 2006-09-13
this is how i have my partition on my xp computer with a system recovery partition:

/dev/sda1 ntfs boot
/dev/sda2 fat32 (i am pretty sure that this is my system recovery)
/dev/sda3 ntfs (i dont know what this is because it is only 1gb)



so how should i go about installing ubuntu? the problem i face is that i have to make 2 more partitions (root and swap) but you can only have 4 primary partitions on there. this is what i was thinking:

/dev/sda1
Extended Partition
             partition 1 for root
             swap
/dev/sda2
/dev/sda3



thats the only way i can think of doing it. Have any of you had a laptop/computer from HP with the recovery partition?

BTW, If I bought a extended accident forgiveness plan at Best Buy, will this void the warranty?

---

### Post by az on 2006-09-13
> **dracule said:**
>  but you can only have 4 primary partitions on there. this is what i was thinking:

/dev/sda1
Extended Partition
             partition 1 for root
             swap
/dev/sda2
/dev/sda3



thats the only way i can think of doing it. Have any of you had a laptop/computer from HP with the recovery partition??

Do not partition the drive yourself - let the partitioner which is integrated in the installer do it.  There is no reason why you need to worry about primary or secondary partitions.

All you need tell it is what size to shrink your windows partition down to.


> **dracule said:**
> 
BTW, If I bought a extended accident forgiveness plan at Best Buy, will this void the warranty?

Good question.  Partitioning your drive is normal use.  However, having a recovery partition to reinstall your windows OS is not a good idea if you want to dual or triple boot your box.

I would phone the vendor from which you bought the thing and ask for another recovery solution - usually, they will immediatly send you a windows install CD so that you can reinstall the OS you bought with the computer in the event you bork your partitions.

So your warranty it fine (it is actually ridiculous to think that the backup/recovery solution they provide for you can take away your freedom to do what you want with your computer...  That's why they usually will give you another one at no cost)

---

### Post by dracule on 2006-09-13
When i click "use largest continious space" it says cannot partition drive.

---

### Post by az on 2006-09-13
> **dracule said:**
> When i click "use largest continious space" it says cannot partition drive.

Pick the option to resize an existing partition.  You probably have a very small amount of free space somewhere.

---

### Post by dracule on 2006-09-13
gparted always crashes when i try to resize.

---

### Post by az on 2006-09-13
> **dracule said:**
> gparted always crashes when i try to resize.

Are you using the most recent version (6.06-1)?

---

