---
title: "[SOLVED] 3 questions to ask about dual-booting with vista"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by jake_won on 2008-08-14
Hi, first post here although I've used this useful forum a lot.

I had a zv5000 (or something) HP laptop which was using XP a few months ago. It had 512mb ATI Radion 9100 IGP, some celeron processor and 40gb HD. Then I switched to Linux because I formatted the computer and when I tried to re-install XP, it would just shut off. I finally installed XP after numerous attempts although in the end, I scrapped it. Back then I was angry that I had to install Ubuntu but now I think it's a good thing that I did. Well, after 3 months of using it, configuring it so I can have all the apps anc compiz working, I ended up buying a new laptop lol...

I bought Gateway T-6386 that has Intel 2.0GHz Centrino/Intel X3100/4GB RAM/250GB HD/64bit vista for only $639 at BestBuy. Pretty sweet deal, I think.

Now, I wanna install hardy on it. But since I'll be going back to school soon, I thought I should keep vista and dual boot with 64bit ubuntu. 

I'm thinking of following this guide.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Q1. How much HD space is good for Ubuntu?? I usually store all my music/movie files on my 300GB external HDD (which has been running a bit low recently). With my old laptop, I was just using ubuntu only and if I recall, I had about 27GB of free space left with 3 months of using. With 250GB HDD, I have 167GB left with all the Vista stuff.

Q2. Would dual-booting vista64 with ubuntu64 slow down my computer? I already know the answer to this from various forums, but from my personal experience with the old HP laptop, it did. I remember both ubuntu and XP running  unusually slower and I had to scrap XP and just install ubuntu. But it could've been because my laptop was such a crappy piece of hardware.

Q3. I read somewhere that in order to write/access the windows partition, you need some kind of application? If so, what is a good one? Say, I write a report on ubuntu using O.O. and save it on Ubuntu partition, would I be able to access/write on it using Vista? Or vice versa? (What I wanna know is, if it's possible to freely write on whichever partition using whichever OS).

That was a long post and lot to read... But any kind of help would be much appreciated!! Thanks!

BTW, does anyeone know if that Gateway T-6386 has an extra drive slot so I can pop in my old one? I'm thinking no since most laptops don't and don't wanna open it up and void the warranty. Also, I can never tell with the spec sheet when they say 1 slot, if they mean 1 extra slot or 1 slot that the current drive is using...

---

### Post by Partyboi2 on 2008-08-15
> Q1. How much HD space is good for Ubuntu?? I usually store all my music/movie files on my 300GB external HDD (which has been running a bit low recently). With my old laptop, I was just using ubuntu only and if I recall, I had about 27GB of free space left with 3 months of using. With 250GB HDD, I have 167GB left with all the Vista stuff.

It really comes down to personal preference. If you plan to use Ubuntu more then vista then make the ubuntu partitions bigger. Or the other way around.    
> Q3. I read somewhere that in order to write/access the windows partition, you need some kind of application? If so, what is a good one? Say, I write a report on ubuntu using O.O. and save it on Ubuntu partition, would I be able to access/write on it using Vista? Or vice versa? (What I wanna know is, if it's possible to freely write on whichever partition using whichever OS).If you are using hardy you can read/write to ntfs partitions. So you will be able to access your vista files. To get vista to read/write ext3 (ubuntu) you will need to install a small program like [[COLOR=Blue]Ext2 IFS[/COLOR]]("http://www.fs-driver.org/") or [[COLOR=Blue]explor2fs[/COLOR]]("http://www.chrysocome.net/explore2fs") to read/write your ubuntu files.

---

### Post by jake_won on 2008-08-15
Thanks Partyboi2!!

I decided to use 17gb for storing important files and 60gb for ubuntu. I hope that'll be enough. I hardly used 40gb on my old laptop. 

Does anyone want to answer second question? I know what most people will say but I also want to hear some personal experience and find out why it slowed down.

---

### Post by Sef on 2008-08-15
> I decided to use 17gb for storing important files and 60gb for ubuntu. I hope that'll be enough. I hardly used 40gb on my old laptop.

Ubuntu needs only 8 - 10 GB.  I would do that and have the rest used as a home partition.

---

### Post by jake_won on 2008-08-19
So, I installed Ubuntu but there were some issues with screen only showing up like 3/4 of the 1280x800 resolution...
I'm still trying to fix that.
Anyways, thanks for suggestions!

---

