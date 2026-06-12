---
title: "192 MB RAM: Trouble booting from USB"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by Jesader on 2015-02-14
I'm trying to boot Ubuntu the first time from a USB drive and I get an error message that says 
I need to update the wireless kernel and the screen goes all funny. I'm trying to boot this on my old Gateway laptop.
Please help, I really would like to try Ubuntu, but im not sure what I need to do.

---

### Post by mörgæs on 2015-02-14
Hi, welcome to the fora.
Please begin with a complete hardware description.

---

### Post by Jesader on 2015-02-14
> **mörgæs said:**
> Hi, welcome to the fora.
Please begin with a complete hardware description.
Its a Gateway laptop MX3215 Intel (R) Celeron (R) M with a 1.40GHz processor and 192 MB of RAM and its got windows XP. I have the 32 bit ubuntu on my USB. Let me know if theres any other info you need.

---

### Post by yancek on 2015-02-14
192MB of RAM won't run current releases of Ubuntu.  Minimum is 512MB, recommended is 1GB.  I'd suggest doing an online search for Linux on older computers and see if you can find some sites with recommendations like the one below:

[http://distrowatch.com/search.php?category=Old+Computers](http://distrowatch.com/search.php?category=Old+Computers)

---

### Post by mörgæs on 2015-02-15
Yes, you need to add more memory.

After that you might encounter PAE problems which is solved like this:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by sudodus on 2015-02-15
See these links for old computers with very low RAM
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

You might also try some ultra light linux distros for example ***Wary Puppy*** or ***TahrPup*** or ***Tiny Core***.

---

### Post by efflandt on 2015-02-15
There was a time when 192 MB was more than enough, for Linux.  For example when I upgraded my laptop from Jan 2000 from 128 MB to 192 MB RAM (I think 550 MHz Pentium) I did not even add swap, and it ran KDE with Netscape, etc. in SuSE 8.0 then 8.2 just fine without lag. For at least 2 years I used it as a terminal for a headless Linux PC in my basement. But it has limited video RAM and the company that made its video chip went out of business shortly after that, so I have not used it for many years. The headless PC in my basement has been running SuSE 8.2 24/7 on 333 MHz Celeron w/158 MB RAM since it was installed in 2003 (except when shut down for long power outages).

I did resurrect an old PC with K6-2/400 and 128 MB RAM a couple of years ago when I needed a backup web proxy in case our office lost its connection with our remote factory. I installed ip-cop on it which is a Linux router/firewall OS with squid proxy. I originally bought that PC as a Best Buy return for $100.00 plus a $10.00 cpu fan (broken wire) and more RAM than 64 MB it came with. It came with an LS-120 drive (120 MB floppy) which for a time I ran zipslack from (Slackware for zip drives).

So I am sure that you can find some Linux to run on it, just not full blown Ubuntu which has grown over the years, but still boots faster than Windows using less resources.

---

### Post by Jesader on 2015-02-15
Thanks everyone for the help! After reading through some of the provided link, Ive decided to get a decent refurbished laptop. I was wondering if these two would give me a no fuss boot of ubuntu since my computer skills are lacking. I would also take some suggestions in the $150 range.
Thanks again for all your help.


[http://www.bestbuy.com/site/lenovo-refurbished-14-1-thinkpad-notebook-2-gb-memory-80-gb-hard-drive-black/1311025157.p?id=mp1311025157&skuId=1311025157](http://www.bestbuy.com/site/lenovo-refurbished-14-1-thinkpad-notebook-2-gb-memory-80-gb-hard-drive-black/1311025157.p?id=mp1311025157&skuId=1311025157)

[http://www.bestbuy.com/site/dell-refurbished-14-1-latitude-notebook-2-gb-memory-80-gb-hard-drive-silver/1309132683.p?id=mp1309132683&skuId=1309132683](http://www.bestbuy.com/site/dell-refurbished-14-1-latitude-notebook-2-gb-memory-80-gb-hard-drive-silver/1309132683.p?id=mp1309132683&skuId=1309132683)

---

### Post by Bucky Ball on 2015-02-15
Welcome. Both have 2Gb of RAM so both should run whichever flavour of Ubuntu you choose. I would still stick with Lubuntu or Xubuntu as both are lighter than Ubuntu, but you can try any of them from the install media before installing and see what suits. 

Would be best to do a search for which one of the two computers you're looking at is most compatible with Ubuntu/Linux. Look particularly for graphics card and wireless (if they have it) compatibility. I found [this]("http://wesmorgan.blogspot.com.au/2011/12/thinkpad-t60-and-ubuntu-good-mix.html") and [this]("http://www.linlap.com/dell_latitude_d620"). No saying what your results will be like with newer versions of Ubuntu and its flavours. Might just work out of the box. Good luck.

---

### Post by sudodus on 2015-02-15
My experience of old IBM and Lenovo laptop computers is very good. Old Dells can be good too. With these CPUs below core 2 duo and 'only' 2 GB RAM they will probably run well with Lubuntu, Xubuntu and Ubuntu Gnome, and maybe also with standard Ubuntu.

Both computers will run ***much*** better than the old one with 192 MB RAM. Before making a dual boot system with linux, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by Topsiho on 2015-02-16
Old computers may have old graphics cards (  :)  ), without 3D-acceleration. Ubuntu 14.04 with Unity, only runs with graphics cards that are 3D-accelerated.
As far as I know the other Ubuntu's, and Mints, run well without this.
I used to have a computer (from about 2005) with an AGP-card, that ran Ubuntu 12.04 well, but not Ubuntu 14.04
So please check the graphics card of your "new" computer first, before buying it.

Topsiho

---

