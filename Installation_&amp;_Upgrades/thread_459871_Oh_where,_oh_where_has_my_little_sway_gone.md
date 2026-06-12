---
title: "Oh where, oh where has my little sway gone?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by ariehz on 2007-05-31
I would say that I am a semi-sophisticated end-user, in so far as the BigBlueBog is concerned, but am altogether a noob in Linux.  
In trying to install Feisty I was unable to configure the size of /swap.  The disk is an old 12.7GB that I thought would suit for an excursion into penguin country.  Both the cd live and the alternate cd gave swap only 588mb; I wanted more.  
In the end only by first partitioning the disk and formating, (ext3), with Paragon Partition Manager was I then able to create a /swap partition of 2gb.
My question is:  what did I miss.  I would have thought that the Alternate install would allow me to configure the swap partition...what did I do wrong ???
thanks,
ariehz

---

### Post by southernman on 2007-05-31
Sounds as if you selected to use "guided" partitioning... correct?

Just elect to do a manual thing. If you will only have Ubuntu on this HDD I would set it up like this:

 / (about 3gb)
 /home (about 7.5 gb)
swap area (1 gb or only double the amount of ram in your system.

---

### Post by ariehz on 2007-05-31
Thanks for the quick response.
I did try with manual.. no luck.
I was going to go "alll the way"  with /home, /usr, /var, etc, etc.
If not, can I suppose that those partitions will be virtualized in the 3gb /root ?
thanks again southernman

---

