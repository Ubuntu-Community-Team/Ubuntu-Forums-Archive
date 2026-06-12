---
title: "Unable to install Ubuntu"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Nightspear on 2007-04-12
I recently purchased a new pc, and I am having some trouble setting up a dual boot system with Ubuntu/Windows XP. When I am attempting to install it appears as all is going well, and then it hangs when a loading screen similar to the one below comes up (although it is at 0% with no text).
[http://i37.photobucket.com/albums/e53/nemesis4u/2.png](http://i37.photobucket.com/albums/e53/nemesis4u/2.png)

This problem occurs with both Dapper and Edgy. I have run the disc test on both discs but there are no errors. I tried the Alternate Install Disc, and I successfully got to the partition part, where I was unable to resize my windows partition to less than the maximum drive capacity (160 gb).

My Specs:
Asus M2V Motherboard
AMD Athlon 64 X2 4200+
160gb IDE hard drive
80gb SATA Drive (undetected for some reason, I have no idea why)

Any advice would be much appreciated.

---

### Post by raja on 2007-04-12
It is not clear from your post at which stage of the install you are having problems. Does the live cd boot up at all ? What happened with the alternate cd after you had resized the windows partition ?

---

### Post by Nightspear on 2007-04-12
I am able to attempt to install on the normal cd, it scrolls through some console things for a few minutes before my problem occurs. The alternate cd won't resize my windows partition at all, when ever i type in a value (such as 140gb) my hard drive hums for a bit and acts like its working, however when the partition manager comes back up it is still 160gb.

---

### Post by zvacet on 2007-04-13
Defragment windows few times before you resize it.Resize it with [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
After these steps go and install Ubuntu on the free space you left after resizing.

---

