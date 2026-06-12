---
title: "Ubuntu and windows 98 se / xp home"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by shawn_selig on 2005-11-16
hello... i just got my ubuntu cd's in the mail yesterday.... and i need some help setting it up..... so far i got a 10 gb partitioned drive with :
  partion 1 - fat 32 - windows 98 se installed- 803mb(capacity)
  partion 2 - ntfs - windows xp home - 8.75gb(capacity)

       my computer is a amd k-6 (540 MHz), and 304 Mb of ram.  i have tired the live cd and everything run good.  i want to install ubuntu on my fat 32 partioned drive with 98 and only have ubuntu on that partion... i don't want o lose any data on my xp partition.. someone please help me out in setting this up, thanks,

---

### Post by aysiu on 2005-11-16
803 MB is a bit meager for a Ubuntu install. My Ubuntu installation is 3.9 GB.

---

### Post by shawn_selig on 2005-11-16
is there anyway i can resize my partion 1 for more disk space without losing any files on my xp?

---

### Post by Kapre on 2005-11-16
[QUOTE=shawn_selig]hello... i just got my ubuntu cd's in the mail yesterday.... and i need some help setting it up..... so far i got a 10 gb partitioned drive with :
  partion 1 - fat 32 - windows 98 se installed- 803mb(capacity)
  partion 2 - ntfs - windows xp home - 8.75gb(capacity)

       my computer is a amd k-6 (540 MHz), and 304 Mb of ram.  i have tired the live cd and everything run good.  i want to install ubuntu on my fat 32 partioned drive with 98 and only have ubuntu on that partion... i don't want o lose any data on my xp partition.. someone please help me out in setting this up, thanks,[/QUOTE]

shawn - The basic install of ubuntu (GNOME Desktop) would require at least 1.4 gig. But if you want a smaller version, you can also have it on your present setup (803 MB) using Xubuntu (Ubuntu with XFCE Desktop).

But if you're WinXP partition is not yet full (please advise the remaining unused portion of your NTFS drive) maybe you can get another 2 or 2.5 Gigs from it so you can have the GNOME desktop (which is the one shown on your LiveCD). You c

K

EDIT:  Aysiu beat me to it by just a couple of second..Thanks. ;)

---

### Post by shawn_selig on 2005-11-16
"But if you're WinXP partition is not yet full (please advise the remaining unused portion of your NTFS drive) maybe you can get another 2 or 2.5 Gigs from it so "


    first i would like to say thanks for the fast reply.... is there anyway to change the xp partition without deleting ro losing data for ubuntu?

---

### Post by aysiu on 2005-11-16
[QUOTE=shawn_selig]is there anyway i can resize my partion 1 for more disk space without losing any files on my xp?[/QUOTE] Yes. Defragment your NTFS and follow [these directions](http://users.bigpond.net.au/hermanzone/).

---

### Post by shawn_selig on 2005-11-16
so i resize the partion? or what do i do? wihtout loosing xp

---

### Post by Kapre on 2005-11-16
[QUOTE=shawn_selig]"But if you're WinXP partition is not yet full (please advise the remaining unused portion of your NTFS drive) maybe you can get another 2 or 2.5 Gigs from it so "


    first i would like to say thanks for the fast reply.... is there anyway to change the xp partition without deleting ro losing data for ubuntu?[/QUOTE]

yes there is. You just have to use partitioning software (e/g Partition Magic, QTParted, Gparted). QTParted is on liveCds such as Knoppix and Mepis and Gparted is in Ubuntu Livecd (this I'm not sure). Just back-up all your important files (this is the numero uno, number 1 priority) and then defrag the drive (at least 3 times) and then use the Livecd and run the partitioning program.

I would suggest reading more on the forum about this partitioning.

K

EDIT: I'm damn slow....

---

### Post by shawn_selig on 2005-11-16
thnask, i tired to install and while i was doing it i kept on getting thouhgtts about windows.... anyways.. i'll keep my 2 patrions for 98 and xp ... for no on i'll just run the live cd.. oh and by the way.. i'm running the ubuntu 5.10 live cd as i type this reply.! thansk agin.

---

### Post by aysiu on 2005-11-16
You know, a lot of people just rush into an install or a dual-boot, but I highly recommend using a live CD for a while. It's a good way to get familiar with the interface and "the Linux way" of doing things before you take the plunge.

---

