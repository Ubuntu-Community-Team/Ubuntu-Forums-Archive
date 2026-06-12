---
title: "Gpart not allowing me to partition my drive"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by daveamay on 2011-01-07
[http://i.imgur.com/FKWLQ.png](http://i.imgur.com/FKWLQ.png)
I'm in the dark as to why I can't partition my drive.

It's a 40 gb ssd with Ubuntu 10.10 installed. I want to create a partition to install windows 7. No 'unallocated' space appears as the guide suggests it should and none of the /dev/sdas would allow me to partition them.

---

### Post by psusi on 2011-01-07
You can't repartition the drive while you are running off of it.  You need to boot from the livecd.

---

### Post by daveamay on 2011-01-07
> **psusi said:**
> You can't repartition the drive while you are running off of it.  You need to boot from the livecd.

Makes sense, thanks!

---

### Post by Rubi1200 on 2011-01-08
Hi and welcome to the forums :)

The other thing you will also need to do from the LiveCD is to reinstall GRUB after installing Windows:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you need more help, please ask.

---

