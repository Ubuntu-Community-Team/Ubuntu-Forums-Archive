---
title: "CD doesn't get burnt right..."
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2007-05-18
I'm trying to get the Xubuntu alternate install CD... So I downloaded the .iso, burnt it to a disc, and started the installation. After it formated the partitions it had to, it started actually installing. Then it threw tons of errors that packages were corrupted. So, I rebooted and checked the CD for errors. Of course, it had some. I ditched it. I downloaded the .iso again. I burnt it again. This time, even the disc checker won't start, saying that the kernel image is invalid or corrupted.

Why?? I used up the couple of blanks I had around the house but I hope to be receiving a few more later this evening, and I'll try to burn it from Windows, using Nero and see if that works.

I'm shocked, why can't I burn a .iso right? I just right-clicked it and chose "Open with CD/DVD Creator" and then burnt it at 37x and the CD states 52x so that should not be a problem. Then what is?

---

### Post by hessiess on 2007-05-18
alwase burn iso's as slow as posable! 4 or 8* is ok

---

### Post by Znupi on 2007-05-18
I used to burn iso's at 40x on Windows with absolutely no problem. And I burnt quite a lot. Why can't I do that on Ubuntu?

---

### Post by aysiu on 2007-05-18
This should help you:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Znupi on 2007-05-22
OK so I burnt the image again this time at 4.7x (which is the slowest speed I have available) and STILL, it says the kernel image is invalid or corrupt. Wtf?

---

### Post by aysiu on 2007-05-22
You also did the MD5Sum check?

---

### Post by Znupi on 2007-05-27
> **aysiu said:**
> You also did the MD5Sum check?
No, I had not run the MD5Sum.

But, I booted Windows, downloaded the .iso **again**, and burnt it using Nero at **40x** without any problems! I checked the CD for errors and there are none.

Why did Ubuntu make 3 bad copies? I really don't get it. I just played around with gconf-editor and noticed that **burnproof** was deactivated. Could that have been the cause? Maybe I should've used some other software? Like **k3b** or something?

---

