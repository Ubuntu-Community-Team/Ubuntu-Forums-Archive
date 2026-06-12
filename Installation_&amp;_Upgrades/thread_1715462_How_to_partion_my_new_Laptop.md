---
title: "How to partion my new Laptop"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by zenawenliang on 2011-03-27
I have a Dell XPS M1330 it has a Duel Core 2.00 GHz and has 3Gbs Ram, I was wondering if I should chose manuel partioning or just chose wipe disk, I am just going to run ubuntu not windows anymore, its awful.

---

### Post by oboedad55 on 2011-03-27
> **zenawenliang said:**
> I have a Dell XPS M1330 it has a Duel Core 2.00 GHz and has 3Gbs Ram, I was wondering if I should chose manuel partioning or just chose wipe disk, I am just going to run ubuntu not windows anymore, its awful.

How big is the hard drive? You can let Ubuntu use the whole disk, or you could make a /root partition, /home, and a swap partition. You will get many different opinions on this sort of thing, but I think a swap partition of 3 gigs should be plenty.

---

### Post by zenawenliang on 2011-03-27
Its 260GBs Im thinkin of just chosin the option of using the whole hardrive during setup. Will it automatically setup the 3gb swap-linux partion?

---

### Post by Dutch70 on 2011-03-27
Are you a gamer? You may want to keep windows around until you get used to Ubuntu. A dual boot for people switching over is a smart move.

Not sure if it will automatically set 3GB for swap or not, but I doubt it. It's a good idea to partition your hdd before you do the install.

---

### Post by zenawenliang on 2011-03-27
I just got done with duel booting, and I decided that if I wanted to run games i would use wine

---

### Post by Dutch70 on 2011-03-27
Then I recommend creating 3 partitions.
1. Swap = the size of your physical RAM
2. "/" aka "root" = 10-20 GB
3 /home = the remainder of your hdd

You'll probably want to format "/" & /home to ext4

Edit: This link may help & btw, welcome to UF.
[[COLOR="Red"]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

The /home is not necessary, you can just use the first 2. However there are many benefits to having a /home partition & it is the preferred method by most.

---

### Post by colintivy on 2011-03-27
I don't know about formatting /home to ext4, I did this (with ext3) and it is causing me massive problems [which are posted elaswhere].Advice fom other forums is DO NOT format /home if on a separate partition.

---

### Post by Dutch70 on 2011-03-28
> **colintivy said:**
> I don't know about formatting /home to ext4, I did this (with ext3) and it is causing me massive problems [which are posted elaswhere].Advice fom other forums is DO NOT format /home if on a separate partition.

While I appreciate that your trying to help colintivy,
If you DO NOT format /home, ...you CAN NOT use /home!!!

As someone told you & the reason I didn't even mention it in your thread, is because formatting to ext3 has absolutely nothing to do with your problem. 
All you need to do is reset your mount point to look at your new /home.

The only reason you would not format /home on a separate partition is if you are re-installing Ubuntu to "/" ...and you have /home _already formatted_ with data on it that you don't want to lose.

---

