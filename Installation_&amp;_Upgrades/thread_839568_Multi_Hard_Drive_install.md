---
title: "Multi Hard Drive install"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by richrock on 2008-06-24
FIGURED OUT - now I'm windows free!  Ubuntu only!

Right, after years of dithering, mucking around with Ubuntu, I'm finally ready.  I wanna ditch my windows install.  I feel savvy enough with Linux OS's to get my important stuff done, plus it works fine with my iPod, scanner and printer.  That's all I need.

But!

I need some help in planning the demise of my windows bit.  Let me outline my system :
1 x 160gb hdd - The WinXP Pro install (NTFS)
1 x 80gb hdd - a media drive (it's the same size as my iPod) (NTFS)
1 x 120gb hdd - the current Ubuntu install.

My thoughts are to install Ubuntu and apps onto the 80gb, which I would assume would be /, /usr and swap...  Then have /home on the 160gb, giving me plenty of space.  But could I extend /home over onto the 120gb?  Or would it always be a separate drive?

Any thoughts would be well appreciated.  Even if just to say that it seems right and go ahead anyway... And yes, I've backed stuff up so it's ok to reinstall/reformat/repartition....

---

### Post by komputes on 2008-06-24
Giving /home a separate partition is not a bad idea. You have to select "Manual" from the partitioning menu on the installer to get that to work automagically. As long as you have everything backed up you should be fine!

I'd do this:

80G Drive
/ = 79GB
swap = 1GB

160G Drive
/home =160GB

As for merging the 160G and 120G into a massive 280G logical partition, I think you would need to connect both drives to a RAID controller to do that. (Am I wrong? Someone please correct me if I am.)

---

### Post by richrock on 2008-06-24
Thanks!  I'd pretty much thought down those lines, although I was thinking of using the 80g with 50g / and 1g swap, then the rest for /usr...

Still stuck on the second part, maybe I'll look into the whole raid controller...

Rich

---

