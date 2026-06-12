---
title: "pls help stuck at partitioning"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Strike_105x on 2008-01-12
Hi i have an 80 Gb hdd SATA and an Maxtor 40 GB IDE my problem is i selected manual instalation and i dont know how to partition them (i dont want dual boot with XP) so what i want to do is make an 13 Gb partition for Ubuntu 7.10 and a swap space 3 Gb. is it enough Hdd space for the OS ? and the rest of partition i want to convert them in something that works good with ubuntu i dont know what should i chose for extension nether anything else i tried and searched but didnt find a guide for this pls help

---

### Post by ubutufan on 2008-01-12
Ok let's start from basics. Where would you like to install? On the 80GB or the 40GB disk?

The last part of your question I do not understand. Please explain what you have in mind

---

### Post by Strike_105x on 2008-01-12
i Whould like to install it on the 80 Gb because its faster and i want to partition the 80 Gb to 13 gb for Ubuntu (i thought its enough tell me if it needs more) 3 Gb for swap (it says there it needs a 256 partition for swap oO) and the rest of theHDD for my data (and i will like these to be in a format thats suited to Ubuntu like in XP for example its suited to work in ntfs partitions)

---

### Post by Partyboi2 on 2008-01-12
3 gig for /swap seems a little high. How much ram do you have in the machine?

---

### Post by Strike_105x on 2008-01-12
1 Gb DDR 400 i puted 3 Gb because i didnt want it to be to little :)) This is mi first time trying to run another OS that was not made by microsoft sry if i say something stupid but i dont really know much about ubuntu

---

### Post by Partyboi2 on 2008-01-12
> **Strike_105x said:**
> 1 Gb DDR 400 i puted 3 Gb because i didnt want it to be to little :)) This is mi first time trying to run another OS that was not made by microsoft sry if i say something stupid but i dont really know much about ubuntu
First bit of advice. No question is stupid, we all at some point started where you are at :)

as for your swap I would suggest 1 gig
the /root partition needs to be around 5 gig
and /home can be what is left. Ubuntu can read ntfs file systems, so if you use the rest of the hdd for what you called "data" If you  formatted it as ntfs, windows and xp could both use that space.
But make sure when you create the ubuntu partitions that you format /root /home  as ext3

---

### Post by ubutufan on 2008-01-12
Where do you have your xp partition?
You should be careful not to erase it

---

### Post by Strike_105x on 2008-01-12
Ok did something like that so i made 5 gb partiton ext3 and at mount point i righted: "/root" after that i made an 1 gb partition at this one i selected swap (from the same menu were Ext3 was) and the rest of the hdd is ntfs (i have no intension on installing an windows XP so if there's another tipe like ext3 for example more suitable tell me pls) and i tiped in the mount point: "/home" is it ok like this ? also at the mount point should i also tipe something for the 40 GB HDD ?

PS for ubutufan : i've deleted my XP install before trying to install ubuntu (it was 2 bugged anyway) if i can handle to learn to work in ubuntu/linux i'm kissing microsoft bb :))

---

### Post by Partyboi2 on 2008-01-12
From what you have posted my understanding is that the 40 gig is where windows is? So don't need to touch that partition (which shows up as ntfs in the partition tool)
I am a alittle unclear about what you have done so lets see if this is correct
You have created a partition that is 5gig for /root and have set the mount point as /
You have created 1 gig for /swap
you have created 9 gig for /home 
and the rest of the space another partition as ntfs for data?

---

### Post by Strike_105x on 2008-01-12
Ok this is what i have done until now made 15 giga partition for ubuntu (made it a little bigger maybe i'm gona have some files stored here 2) 1 giga for swap at least i think so and the rest of the hdd 65 gb ,which is for documents movies music games etc, i dont know to what to convert it (thats why i keeped asking could i put that 2 at ext3) and the 40 gb hdd i lefted like it was but I DO NOT HAVE windows xp installed on it as a matter of fact i dont have it installed on my computer at all i deleted before trying to put ubuntu (and all my files on the Hdd have been backed up on DVD's so i'm not worried of any data lost) 
To make things easier i posted a pic with what i've done so far : [http://img530.imageshack.us/my.php?image=screenshotmo5.png](http://img530.imageshack.us/my.php?image=screenshotmo5.png)

So the remaining questions are:
1. Is it ok like this ? for the swap and the Ubuntu partition
2. What can i convert my 65 partition to? (can i put it ext3 since Ubuntu uses that ? )

---

### Post by erfahren on 2008-01-12
don't type in "/root" for root - if it makes you type it in (instead drop-down list of selections) just type in a slash " / "

format the /home to ext3 as well  (if you're not planning on accessing it from WinXP) - that's the default file system for Ubuntu

other than that it looks ok

---

### Post by Strike_105x on 2008-01-12
thank you verry much for your help :) hope i'm going top enjoy ubuntu :)

---

### Post by Strike_105x on 2008-01-12
Hi got a new problem keep getting an error at 94% unable to install Grub in (hd0) [http://img242.imageshack.us/my.php?image=screenshot1tk0.png](http://img242.imageshack.us/my.php?image=screenshot1tk0.png)
does anybody know what the problem is ?

---

### Post by Partyboi2 on 2008-01-12
Try reinstalling grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

