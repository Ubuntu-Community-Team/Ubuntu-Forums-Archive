---
title: "Moving Windows XP partition to different physical drive"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by nikdo on 2007-05-11
Hello everyone

I have a gateway comp that came with a 200gig HDD with windows xp preinstalled. 
Presently I dual boot - I have ubuntu on another 40gig HDD, and the 200Gig HDD has two partitions: one for windows, the other for data.

This is what I am attempting to do:

* move windows to a 3rd 30gig HDD from the 200gig HDD. This will become the 'c' drive
* wipe out windows partition on the 200gig HDD and expand the data partition to take whole of 200gig
* leave ubuntu on the 40gig HDD

What I am wondering is what tools would I use to copy the windows partition from the 200gig onto the new 30gig drive?

Note: I assume that once moved, there won't be much of a problem since windows will be on the 'c' drive, ubuntu stays the same and the data drive doesn't matter. I know I will have to edit GRUB so that it would point to the new 30gig drive with windows on it. Am I missing something here from the booting pint of view?

Thanks so much!

---

### Post by theicyj on 2007-05-11
You will have to copy all the files over. There will be some issues with booting into windows as you assumed, but, [http://www.computerhope.com/issues/ch000465.htm]("http://www.computerhope.com/issues/ch000465.htm") should help you get that issue fixed.

---

### Post by nikdo on 2007-05-11
being new at this, I would need help with what command or tool(s) I should use to copy the partition to the other drive.

thanks so much!

---

