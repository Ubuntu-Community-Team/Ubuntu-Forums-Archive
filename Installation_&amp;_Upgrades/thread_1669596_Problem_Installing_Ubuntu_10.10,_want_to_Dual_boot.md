---
title: "Problem Installing Ubuntu 10.10, want to Dual boot"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Mercurydrug on 2011-01-17
first, i'm totally new in ubuntu. i want to try this OS, because i want to explore more things. i'm a 2nd year college student, so, a great(simple enough for my current age ^_^ ) guide will really help :)

i'm having problems with managing the partitions in my laptop, 'coz ever since i was a windows user.

i have these partitions:
C: - (boot,page file, crash dump, **_primary partition_**) | capacity - 107.32gb

D: - (***primary partition***) | capacity - 82.01 gb (originally +30gb, i shrinked it using disk management in windows 7, allowing me to have 31.25gb UNALLOCATED)

RECOVERY (E:) - ***Primary partition*** | 12.20gb

System reserved - system, active, ***primary partition*** | 100MB

i want to know how im gonna be able to use my unallocated space to install ubuntu 10.10 i386, because i tried to run LiveUSB, and selected the unallocated space, but ubuntu partitioner says its UNUSABLE..

i wanna know what im missing here guys, i really need to have ubuntu 10.10, for my future life as an IT.. i've read that i can only have 4 partitions in a HD, so, how do i extend that unallocated space?

my laptop has 232.88 GB total HD space, dual core 2.0ghz, 2gb ram,

---

### Post by Quackers on 2011-01-17
Welcome to UF.
It appears that you already have the maximum of 4 primary partitions on your HDD.
In order to install another operating system it is not enough that you have unallocated space. You will need to delete a primary partition (preferrably one next to your unallocated space), then you can create an extended partition and have as many logical partitions as you want inside that extended partition.
One option could be to make the recovery dvd's (maybe even 2 copies) and then delete the recovery partition.

---

### Post by Mercurydrug on 2011-01-18
thank you sir. but, umm, i have no experience in extending partitions. what i did earlier is, extend my D: drive again, thus getting back those 30gb AGAIN, and, now, im lost to how am i to add extended partitions in that D: drive.

im sorry but, i couldn't find a guide with screenshots on how to do that. and, may i ask if, i install Ubuntu on that D: partition, will the C: partition be affected? because its on the same physical drive.. and will my files there be lost? its current used size is about 60gb, so, now i have at least 50gb, but i only want to use 30gb for ubuntu, because i havent got external HD yet..

thank you sir for your replies, its really appreciated..

---

### Post by Quackers on 2011-01-18
As your hard drive stands at the moment, you cannot create another partition of any kind. 
You cannot install Ubuntu on your D: partition.
You cannot install any operating system on that drive at the moment.
In order to install an operating system you will need to delete a partition. Completely! Losing all data on it (unless you back it up first)!
Then you can create a new extended partiton (with logical partitions inside it).

---

### Post by Mercurydrug on 2011-01-18
ok sir, thanks for the help. i will try this now.

---

### Post by Quackers on 2011-01-18
Take care :-) Any questions ask here. There are many here who can help you. It is MUCH better to ask than to make a mistake when partitioning!

---

