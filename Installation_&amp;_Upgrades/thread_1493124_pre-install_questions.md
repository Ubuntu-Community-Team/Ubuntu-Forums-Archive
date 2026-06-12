---
title: "pre-install questions"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2010-05-25
Its been years since I was last on Ubuntu and I want to avoid making the same mistakes I did when I 1st started..

so

Would it be difficult to install Ubuntu on this system?

> 
# • Intel(R) Core(TM) i3-350M Dual Core processor (2.26GHz, 3MB L2 Cache)
# • 2GB DDR3 System Memory (2 Dimm)
# • 250GB 7200RPM SATA Hard Drive
# • Intel(R) HD Graphics with 5-in-1 integrated Digital Media Reader and HDMI
Webcam + Microphone with 5-in-1 integrated Digital Media Reader and HDMI
Windows 7

HP G42t laptop


It has no video card as everything video wise is integrated into the i3... would I use intel drivers for this and would I be able to use cairo dock or docky and conky?

I plan on installing 4gigs to 8gig's of ram b/c its a 64bit system, what version do I download to cd?

Thanks in advance.

---

### Post by oldos2er on 2010-05-25
If I were you I'd use 64-bit Ubuntu. [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) click on 'Alternative download options' to get 64-bit.

---

### Post by darkod on 2010-05-25
There are some hiccups with Intel graphics. Check the model that's reported and try google for any issues.

Otherwise, you shouldn't expect any problems I guess.

When you create the cd, furst boot with it and use the Try Ubuntu mode. That should load it from the cd. It will show you any compatibility issues.

---

### Post by maddbaron on 2010-05-25
ok great...thanks
last question do I let Ubuntu partition my drive during the install or do I do it myself while in windows? 

I ask b/c I remember reading the board when Vista came out and reading there are some difficulties..granted this will be a win 7 system. I wanna be prepared for anything.

---

### Post by darkod on 2010-05-25
> **maddbaron said:**
> ok great...thanks
last question do I let Ubuntu partition my drive during the install or do I do it myself while in windows? 

I ask b/c I remember reading the board when Vista came out and reading there are some difficulties..granted this will be a win 7 system. I wanna be prepared for anything.

You can't partition a disk for linux in windows. Windows can create only ntfs partitions, so any partition you create as ntfs you would have to reformat (and maybe recreate) with the ubuntu installer so they can have different filesystem.

You can select during the install whether you want automated method (for example Use Largest Avalable free space which will install ubuntu into the unallocated space you left on a disk), or manually create partitions.

Shrink the win7 system partition with windows Disk Management, if it's taking the whole disk now, and then use the above option or manual partitioning which gives you more control over partition sizes.

---

### Post by maddbaron on 2010-05-29
Thanks...i read up some more and that laptop didn't seem right for me. It had some limitations with the lack of the graphics card I didn't want to risk b/c of my job. 

I ordered another one that's pretty perfect for me and with an ubuntu friendly processor and grahics card but it has a broadcom wireless card and its a lenovo, both of which I now read are not ubuntu friendly...I remember how much of a hastle I had to go through with my ubuntu set up from several years go with the broadcom card setup...so while i still have time to cancel this, is broadcom support in ubuntu better now or still a hell in the waiting? 

I did a search and see some are still having issues with it, kind of nervous if its a going to be unfixable.

---

### Post by darkod on 2010-05-30
> **maddbaron said:**
> Thanks...i read up some more and that laptop didn't seem right for me. It had some limitations with the lack of the graphics card I didn't want to risk b/c of my job. 

I ordered another one that's pretty perfect for me and with an ubuntu friendly processor and grahics card but it has a broadcom wireless card and its a lenovo, both of which I now read are not ubuntu friendly...I remember how much of a hastle I had to go through with my ubuntu set up from several years go with the broadcom card setup...so while i still have time to cancel this, is broadcom support in ubuntu better now or still a hell in the waiting? 

I did a search and see some are still having issues with it, kind of nervous if its a going to be unfixable.

I really can't help with that, but at the end of the day you shouldn't compare linux today and several years ago. :)
Also, remember that some people are still going to have problems applying even simple fixes. It doesn't mean you won't be able to make it work.

Since you are worried, do a more extensive search about the exact wireless chipset and how it works/doesn't today with ubuntu.

---

### Post by igtrnt on 2010-06-13
Hello,

I have same HP G42t. And I have no problems with Ubuntu 10.04-desktop, 64 bit except that sound is not working.

---

