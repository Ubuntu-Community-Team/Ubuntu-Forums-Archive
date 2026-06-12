---
title: "Installation Help on max HDD Ubuntu Server...Please help"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by lorewap3 on 2011-09-30
I'm trying something a little extreme. I have 8 HDDs plugged into my 8 Sata slots on my Gigabyte MB:  GA-880GA-UD3H

[http://www.gigabyte.com/products/product-page.aspx?pid=3789#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3789#sp)

And a cd-rom through IDE to do the installation of 11.04.

Problem is every installation it freezes at 37% during the 'setting up the partitioner' stage.

I have a small variety of drives. 2x 2TB Seagate Green drives (the cheap 2TBs), 2x 2GB Seagate XT (the expensives ones) and 4 x 1TB Seagate Barracudas.

All I'm sure you can find very easily on newegg but I'll post some links if it'll help. I'm just trying to get this to work, as it used to with nothing but 4 x 1TB seagate barracudas. I think it's those 2 white sata ports (the gigabyte ports that are 3gb/s and not 6gb/s) that are causing the issue, but I don't know what to set my BIOS settings to to rectify it. I put the Seagate Green on those anyway since they were the only 5900 RPMs while the rest are 7200. I don't care if those are slow, I just want them for backup. I want to do a software raid and have a home media/document server that's mirrored. With 12 TB all mirror still gives 6 I wouldn't fill that for years.


But back to the problem...It won't get past 'Starting up the partitioner'
It seems I've tried every combination in the bios....but I'm open to any suggestion at all at this point of desperation.

Thanks everyone...

---

### Post by lorewap3 on 2011-09-30
Anyone? Please help?

I have a bit of CLI experience with ubuntu server but not with LVM or mdadm or even grub. Did it all through the Server GUI installer.

[B]This may help:

[/B]Before I put in the 4 x 2TB HDD I had 6x 1TB in there working in raid 1+0 perfectly. I wanted to expand but figured it would be much more complicated to try to use my current OS installation, pull out 2 HDDs, and get the other 4 working by somehow rebuilding the OS. But all 4 of the 1 TB drives still have their mdadm partitions on them.

I can't even format them in Gpartition. I boot up with GPart, and it goes into an infinite loop while just trying to search for my drives. 

I'm thinking maybe the existing partitions are causing the Server installer to hang on "Starting up partitioner"?

I beg you, anyone, throw me a bone! A clue or something like "you can never use all 8 sata ports at the same on a gigabyte MB" would even be helpful. Maybe it is he motherboard who can't handle it.

Thanks

---

