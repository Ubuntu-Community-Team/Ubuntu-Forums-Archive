---
title: "Partitioning"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by lhigg on 2009-11-27
Ok, I have been using ubuntu for almost a year now, but when I upgraded to 9.10 (via wubi, as always) I got the annoying grub shell thing. I couldn't get back to my system, thankfully, I have a backup of my files. So I decided to do a live CD. It works fine until I reach the part with the partitioning. The program will not let me partition the system. So I tried making partitions in windows itself, and I can't find a program that will let me resize the partitions, I've tried Acronis' partition suite, and even THAT won't partition my drive, does anyone know a way to fix this?

---

### Post by phillw on 2009-11-27
> **lhigg said:**
> Ok, I have been using ubuntu for almost a year now, but when I upgraded to 9.10 (via wubi, as always) I got the annoying grub shell thing. I couldn't get back to my system, thankfully, I have a backup of my files. So I decided to do a live CD. It works fine until I reach the part with the partitioning. The program will not let me partition the system. So I tried making partitions in windows itself, and I can't find a program that will let me resize the partitions, I've tried Acronis' partition suite, and even THAT won't partition my drive, does anyone know a way to fix this?


I'd uise a GParted LiveCD from here  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
(A good tutrial on Gparted is here --> [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted))

You can also slice from within Windows -->  [http://www.bleepingcomputer.com/tutorials/tutorial116.html](http://www.bleepingcomputer.com/tutorials/tutorial116.html)

One of them should slice your disk for you.

Regards,

Phill.

---

### Post by audiomick on 2009-11-27
The partitions cannot be changed if they are mounted, indicated by a key symbol next to the name, I think, but I can't imagine that this would be the case when the installer is running.

I have frequently seen the suggestion to try the alternate CD instead of the live CD. Apparently there is a different partitioning program on it that works better for some people. The installer is text based, but very easy to deal with.

---

### Post by darkod on 2009-11-27
Your whole HDD is probably taken by windows, and wubi is inside it. The partitioner during install can not always shrink the windows partition to make space for ubuntu. First of all it depends how much free unused space you have on your windows partitions. It can't create more free space than there already is because that would mean destroying data.
So...
1. Since you decided to do a proper install (smart move), remove wubi with Add/Remove programs in windows. That will also delete the space used by wubi depending how much you assigned to it.
2. Defragment your drive in windows, it will help with the shrink.
3. Use Gparted as Phill suggested, much better tool than windows tools (in XP you can't even resize partition without third party software).
4. Start Windows few times and see if it's working OK. At first boot if it asks to do any disk checks let it finish. Boot few more times to make sure it's working. The shrinking can sometimes corrupt windows and if you install ubuntu without checking windows first later you might think ubuntu did something to it.
5. Boot with ubuntu cd, select Install Ubuntu and choose the option to use the free unpartitioned space you just created, or just create the partition manually if you prefer. Personally I always create them manually.

---

### Post by lhigg on 2009-11-27
Thank you guys so much. Gparted worked PERFECTLY. Now I just need to run my live CD. It turns out there was a chkdsk error in my Windows, something Gparted told me, and no other programs did. I fixed that and partitioning worked. Hopefully, my next post/edit will be from my true-installed ubuntu!

---

### Post by lhigg on 2009-11-27
AND IT WORKED! Thank you all so much. I now have a full ubuntu partition!

---

### Post by darkod on 2009-11-27
No problem. Enjoy it now. :)

---

