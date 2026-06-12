---
title: "Struggling with mounting additional HDD and display resolution"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by servelan on 2010-11-09
Hi, I'm good at following instructions but I'm not ubuntu-literate like some of you :) Basically I can c&p in terminal. 

So, I bought a new machine t'other day.. 4gb DDR3, 2T HDD, AMD athlon quad core, if you need the specs.. it came without an O/S which was fine, Ive been happily running ubuntu 9.04 on my old machine for a while and any bugs were sorted easily thanks to reading posts by the good people here.

I tried to install 10.04.. no joy, it did sweet F.A. Then tried 9.10.. the same. Booted off disk of 9.04 and eventually managed to install it on a 500gb drive, so now have two internal drives, with the 500gb being the main boot drive. upgraded to 9.10 along the way.

*much ubuntu forum reading later* and I managed to sort out the 2T drive.. now my main problems are:

1. I have to remount the 2T drive every time I boot.. I can't make it be there on start up. I don't use windows at all btw. I just want to 2T drive to be there, on my desktop, when I start.

2. I have a small 15" DELL tft monitor, which works fine with my old machine, only now the display always starts with a bad resolution, 800x600 I think which is all wrong for the screen and impossible to use as well as being hard to read, and I have to faff around changing it to 1068(?) by something as it doesn't like my nvidia card.

If anyone can please help a ditzy chick I'd be truly greatful xx

---

### Post by sikander3786 on 2010-11-11
Please post the output of

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
sudo blkid
```

And regarding resolution, we'll need this

```
lspci | grep VGA
```

For permanent mount of your drive, you need to add an entry into /etc/fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by servelan on 2011-01-11
thankyou x I actually just went back to my old computer for the time being

---

