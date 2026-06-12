---
title: "resize SWAP? needed?"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by UbuNoob001 on 2010-02-28
So I have Ubuntu 9.10, also I have a 2.16Ghz Dual Core Pentium. With 3GB of RAM. I will be using SAGEMATH for some math work, and i surf the internet, and I want to work with Python(eventually taking a class). I dont do gaming.

Ubuntu Install created only 1.6GB SWAP. If i want to resize this without reinstalling Ubuntu, and without loosing any files, how could i? Total beginner here.

Do you guys think this is important? Or can i just create a "swapfile" down the line if i use too much SWAP? (not sure how swapfile works but ive heard some people do it, rather than its own partition)

---

### Post by raymondh on 2010-02-28
> **UbuNoob001 said:**
> So I have Ubuntu 9.10, also I have a 2.16Ghz Dual Core Pentium. With 3GB of RAM. I will be using SAGEMATH for some math work, and i surf the internet, and I want to work with Python(eventually taking a class). I dont do gaming.

Ubuntu Install created only 1.6GB SWAP. If i want to resize this without reinstalling Ubuntu, and without loosing any files, how could i? Total beginner here.

Do you guys think this is important? Or can i just create a "swapfile" down the line if i use too much SWAP? (not sure how swapfile works but ive heard some people do it, rather than its own partition)

You can resize swap and the process is the same as resizing a partition.  You have to/can do it from a liveCD using the gparted program in live session.  In live session and in gparted, right click on the swap partition and select swapoff.  From thenon, you can get space from the neighboring partition and add it to the existing swap.  Note:  better get space from an 'empty' (non-colored) area of the partition .... you'll see what I mean when you open gparted.

Is swap important?  With your current usage, have you detected swap being used?  If not, then I don't think keeping swap at existing level will be a 'deal-breaker'.  It all depends on your usage and hibernating/suspend habits.

Yes, you can create a swapfile.  But it is also faster to read from memory (hd) than from a file.

If you decide to increase your swap and need a small guide, post back a visual of gparted.  That or the terminal results of

```
sudo fdisk -l
```

That'll help the forum visualize your HD.

Some reading/reference for you.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

PS.  I like to use a standalone,live, gparted CD instead of the ubuntu liveCD.

Raymond

---

### Post by oldfred on 2010-02-28
I would not change it. The installer probably saw an amount of space you were allocating and prorated it to 1.6. I typically recommend 2GB or the size of RAM if you want to hibernate. But you do not want the computer using swap as it is extremely slow compared to RAM. With 3GB of RAM you may never use swap or hardly use it if you are running several intensive applications.

If you do resize it, its UUID will change and you will have to edit fstab with the new UUID and reinstall grub to make sure you can boot.

---

### Post by RJARRRPCGP on 2010-02-28
> **UbuNoob001 said:**
> So I have Ubuntu 9.10, also I have a 2.16Ghz Dual Core Pentium. With 3GB of RAM. I will be using SAGEMATH for some math work, and i surf the internet, and I want to work with Python(eventually taking a class). I dont do gaming.

Ubuntu Install created only 1.6GB SWAP. If i want to resize this without reinstalling Ubuntu, and without loosing any files, how could i? Total beginner here.

Do you guys think this is important? 

Unnecessary. Your swap is already more than big enough. It's not Windows. lol. (Windows Vista and Windows 7 ends up easily using 768 MB of swap when just at the desktop lol) 

Most of the time, Ubuntu will use 0 KB of swap!

---

