---
title: "Shrink my / partition"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by ArgentWarrior on 2014-03-16
I already have Ubuntu 14.04 installed on my laptop, but would it be safe to shrink it about 10gb if the vast majority of it is empty space? My drive only has two partitions right now:

/dev/sda1 mount point /
/dev/sda2 swap

---

### Post by 23dornot23d on 2014-03-16
Yes - usually not a problem ........  always make a backup of important data though ..... as if anything should go wrong while partitioning
power goes off or battery goes dead on a laptop .... etc ...... things will get messed up ..........

But .....

I do it regular and have quite a few partitions ......... often need to change things to grow or shrink partitions to suit situations that arise.

[IMG]http://i.minus.com/iJxuKQd5SvYew.png[/IMG]

---

### Post by Mark Phelps on 2014-03-16
Probably would be OK -- but run "sudo fdisk -lu" (lowercase L, not a one) in a terminal to list out your partitions.

Also, you would have to boot using a CD or USB and run Gparted from there, as you can't modify a partition while its mounted.

---

### Post by manngaurav on 2014-03-16
[ATTACH=CONFIG]251205[/ATTACH]


I want to partiton the 465gb and take out 100gb from it and create a seperate partition is it possible..? without messing up my ubuntu. It is the only OS installed

---

### Post by Mark Phelps on 2014-03-16
> **manngaurav said:**
> [ATTACH=CONFIG]251205[/ATTACH]


I want to partiton the 465gb and take out 100gb from it and create a seperate partition is it possible..? without messing up my ubuntu. It is the only OS installed

Please start your own thread.  It becomes very confusing when more than one problem is being addressed in the same thread and for different posters.

---

### Post by manngaurav on 2014-03-17
I posted it here because it seems to me the same problem that I am having , so there is no point in wasting others time by creating a same thread . Sorry ,

---

### Post by Mark Phelps on 2014-03-17
> so there is no point in wasting others time by creating a same thread

It's not a matter of wasting or saving time; it's a matter that two problems, although similar, are likely to require some differences in the details of their solutions.  And, combing those problems and solutions in one thread creates unnecessary confusion for all concerned.

---

