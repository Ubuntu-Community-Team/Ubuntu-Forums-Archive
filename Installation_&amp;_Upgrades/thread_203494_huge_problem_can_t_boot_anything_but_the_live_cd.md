---
title: "huge problem: can t boot anything but the live cd"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by KurtF1 on 2006-06-25
i finally managed to boot ubuntu live cd with the irqpoll parameter, install it to the hd and then had a problem... when i boot the machine it can t boot!! it said error 22 the first time, then i tried with another installation and now it s error 17... help me! i can t even boot windows now!!! 

ps. i created the partition for linux at the end of an hd, may it be the problem? if it is, then just tell me how to get my mbr back, cause i can t create partition anywhere else :(

---

### Post by loserboy on 2006-06-25
i know somone has a better idea than me.
but if you're running xp, and all you want back is your mbr, then the way i did it was:
get your xp cd, boot on it, choose repair,  type "fixmbr"
now you have windows back assuming thats all that was wrong.

but only use this if noone else has a better idea.

also making the partitions at the end is fine or at least it is for me and its on an official howto

---

### Post by KurtF1 on 2006-06-25
[QUOTE=loserboy]i know somone has a better idea than me.
but if you're running xp, and all you want back is your mbr, then the way i did it was:
get your xp cd, boot on it, choose repair,  type "fixmbr"
now you have windows back assuming thats all that was wrong.

but only use this if noone else has a better idea.

also making the partitions at the end is fine or at least it is for me and its on an official howto[/QUOTE]
lol that's exatly what i just did and it worked fine (i'm on winxp now)
thanks anyway

ps. if i use the live version, may i be able to save files anywhere? i mean, i qould use linux just for some exams i have to do at university, so i basically need to compile some files and use a program named grass (which needs some disk space)

---

### Post by loserboy on 2006-06-26
heh heh well i almost helped somone

As far as i know anything you do on the live cd only goes into ram, also since you dont have a drive formated as ext2 or fat32 then you wont be able to write to anything by default, (can't write to ntfs without messin with stuff)

are you using the gparted that comes with the livecd or doing the partitioning in win?

---

