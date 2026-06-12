---
title: "Partitioning Fails During Install"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by mrgnash on 2005-11-15
I have a 20GB drive, with approx. 10GB free... during install I specify that Ubuntu should use 6GB of the free space, but it returns an error saying that it 'failed to create enough free space for install.' Any idea what's going on here?

---

### Post by Kyral on 2005-11-15
Is the 10GB Free as in unpartitioned or free as in not being used by XP?

(Stupid question, but its the only thing I can think of)

---

### Post by mrgnash on 2005-11-15
Free as in not being used by XP.

---

### Post by Herman on 2005-11-15
G'day, mrgnash,nice to see more Aussies around! I 'm not sure if this is your exact problem or not, but the other day I had something similar to that happenning on a test install. It was caused by me neglecting to type in the 'GB' after the '6.0', where I was specifying the size I wanted for the partition. Maybe the installer took that to mean 'MB', which would have been too small. (Definitely!:D ). Anyway, I got a lovley red screen! (he-he). :D  (Herman).

---

### Post by mrgnash on 2005-11-15
[QUOTE=Herman]G'day, mrgnash,nice to see more Aussies around! I 'm not sure if this is your exact problem or not, but the other day I had something similar to that happenning on a test install. It was caused by me neglecting to type in the 'GB' after the '6.0', where I was specifying the size I wanted for the partition. Maybe the installer took that to mean 'MB', which would have been too small. (Definitely!:D ). Anyway, I got a lovley red screen! (he-he). :D  (Herman).[/QUOTE]

Hey Herman, I knew there had to had to be more of us lurking around here somewhere ;) Oh and you're with the 'good folks' at Bigpond too LOL

Well I left the 'GB' there when I edited the amount of space I wanted to use, so I don't think that's it.. I even tried it a second time by specifying "30%," but I too was hit with a red screen :( 

Could it just be my hard-drive? It's fairly old and I remember having some sort of problem with Partition Magic when attempting to resize my NTFS partition as well... plus, I installed Ubuntu dual boot on my laptop without a hiccup so...

---

### Post by Herman on 2005-11-15
If your hard drive is failing it will give you some warnings usually, well that's what happened when one old hard-drive of mine went out anyway. Especially when I had Windows booted, it kept doing a scan-disk all the time, and this became more frequent as time went on,  until it finally wouldn't even boot and all I could do was run a live CD! I have to go now, my boss has plenty of work in mind for me, (sorry).'Spot ya' some other time! Good luck with it! (Herman):D

---

### Post by mrgnash on 2005-11-15
Oh well. Thanks for your help anyway guys, it's no biggie anyway as I'll be moving soon and leaving my desktop behind :P

cheers -Gnash

---

### Post by wrtrdood on 2005-11-15
[QUOTE=mrgnash]Free as in not **being used by XP**.[/QUOTE]

This sounds like it is already designated as a partition.  If the drive is already fully partitioned the tool will complain that it cannot add another.  Makes sense, really.  In this case you must first select the unused partition and delete it (since you want it smaller).  Then you will have some space to create the new partition.  Don't forget to add a small swap partition too.  

It's probably complaining because you're trying to add another partition but there's no place to put it.  To create a new partition, it must be in unpartitioned space.

---

### Post by missmoondog on 2005-11-15
"It's probably complaining because you're trying to add another partition but there's no place to put it. To create a new partition, it must be in unpartitioned space."

i bet that's it. exactly what i did a couple times! duh!

---

### Post by Biased turkey on 2005-11-15
if in console mode you type:
sudo fdisk /dev/hda
then type:
p

You'll really see what's on your disk

then to quit just type:
q

---

### Post by mrgnash on 2005-11-15
> This sounds like it is already designated as a partition. If the drive is already fully partitioned the tool will complain that it cannot add another. Makes sense, really. In this case you must first select the unused partition and delete it (since you want it smaller). Then you will have some space to create the new partition. Don't forget to add a small swap partition too. 

It's probably complaining because you're trying to add another partition but there's no place to put it. To create a new partition, it must be in unpartitioned space.

Well I don't know, the drive is just one big NTFS partition and from my understanding the auto-partition jigger on Breezy is just meant to shrink that partition and create a new one for Ubuntu :-S

---

### Post by Kyral on 2005-11-15
Its better to use the LiveCD and GParted to shrink the NTFS beforehand

---

### Post by mrgnash on 2005-11-15
Ubuntu runs so slowly off my CD drive that doing anything with the Live CD on my desktop is not really an option. I made another attempt just then to resize from the 'manually edit partition table' - this time it didn't even display an error message, it just dumped me back at menu with no changes made (i.e no freed up space.)

---

