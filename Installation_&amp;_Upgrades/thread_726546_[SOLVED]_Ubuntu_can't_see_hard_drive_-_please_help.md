---
title: "[SOLVED] Ubuntu can't see hard drive - please help"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by darth.k on 2008-03-16
I asked this question in another thread but i'm not getting much of a reply.

Unbuntu live cd and alternate cd can't see my hard drive when I try to install it just gives me a blank list.  Now when I first tried the cd it saw my hard drive fine.  In preparation for the install I made 3 partitions with gparted; 1 for windows xp pro which I am currently using, one for ubuntu and one for swap.  However when I tried to install the hard drive had vanished, it couldn't see it.  XP still works fine and I have since removed the partitons, but it just wont see the hard drive anymore.

I really want to use unbuntu so could someone please offer some advice.  I must have caused some sort of glitch because it saw the disk before I partitioned.

If I reinstalled windows would that help?

hard drive info : Western Digital Caviar SE16 320GB SATA-II

Thanks

---

### Post by Existentialist on 2008-03-16
Have you checked in BIOS to see if the hd is being recognized?

---

### Post by mono.maryam on 2008-03-17
Hi, I have merely the same problem !
I have an Win XP on my PC, and I'm trying to install Ubuntu, but the Partitioner does not detect my hard drive ! It is a Sata II Maxtor 250GB HDD !
If it's necessary I can Fdisk my whole hard drive, first install Ubuntu, and then XP ! Will it help ?

---

### Post by Tomatz on 2008-03-17
Copy and paste the contents of /etc/fstab (in your next post) and type in a terminal  "sudo fdisk -l" (w/o quotes)  and copy and paste the output.

---

### Post by darth.k on 2008-03-17
there is no /etc/fstab directory on the live cd i have, when I type that command in the terminal nothing happens, just goes to the next line.

bios see's hard drive fine and xp is working perfectly so the har drive is ok...

---

### Post by PmDematagoda on 2008-03-17
Please post the outputs of:-
```
cat /etc/mtab
```
and
```
sudo fdisk -l
```
l being simple L not number 1.

---

### Post by Tomatz on 2008-03-17
> **darth.k said:**
> there is no /etc/fstab directory on the live cd i have, when I type that command in the terminal nothing happens, just goes to the next line.

bios see's hard drive fine and xp is working perfectly so the har drive is ok...
Sorry i really should read posts correctly before replying. I just skimmed through and assumed that your problem was post installation.

---

### Post by darth.k on 2008-03-17
Thanls for the reply anyway.  I managed to sort it myself.

I switched my hard disk to the primary sata port on my main board, which previously housed my dvd rw.  This seemed to do the trick, although i'm not sure why.

So for the other people having this problem just switch sata ports and see if you have any luck.

---

### Post by Tomatz on 2008-03-17
Cool! glad its sorted

---

