---
title: "Can't Install - Problem with Disk Partition"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by vijayraj on 2006-04-15
I am installing ubuntu on my emachine that previously was runnign Win98. When I try to istall ubuntu, when I get to the Partition Disk screen (AFter the firewire Ethernet one). It show Partition DIsk and question marks. When I pressed continue or go back, it saya, unimplemented function. What do I do?](*,)

---

### Post by thunderduck3141 on 2006-04-15
how many hard drives do you have, what models? what size
how old is ur emachine (ughhh)
what prossecor, memory, ect.

---

### Post by vijayraj on 2006-04-23
I have one 5gig eOne with an intel celeron

---

### Post by ntsb on 2006-04-23
I think you need 3 partitions. 
"/swap, /boot, /"

and sizes are like that:
/boot -100mb
/swap - equal to your RAM
/         - whole disk, not including /boot and /swap

---

### Post by Sef on 2006-04-26
you don't need a /boot.

Just hit enter when you get to the partition manager.  The default is / and swap.

> When I pressed continue or go back, it saya, unimplemented function. What do I do?

It seems like that it is having problems reading your hard disk.  I would download GParted and set up the partitions with that.  

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

