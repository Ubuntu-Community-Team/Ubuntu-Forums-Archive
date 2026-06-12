---
title: "External hard disk using on 2 computers"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by vanyinet on 2010-01-18
I've 2 computers (one at the job, one at home), different motherboard types but same chipset, having AM2 AMD CPUs but different clock speed.
I don't have (I don't want to buy) internal hard disks for these computers.
 
I would like to buy one external USB HDD and install the latest Ubuntu. I will carry this HDD to my job and my home. 
Is it possible to use this HDD as boot HDD on both computer? Even they are not same just similar? Is this a problem for Ubuntu? Is there anybody who tried this solution?

Thank you.

---

### Post by bhaverkamp on 2010-01-18
Not likely to work very well. Why not just keep you personal files on this HDD. Keeping a single image for different systems will be more of a pain than it's worth.

---

### Post by audiomick on 2010-01-18
I don't know for sure how much trouble you are likely to have, but it sounds like something that would give you headaches. The problems you are likely to have are not so much CPU related as drivers, screen resolution and such like, I think.

You might want to have a look at this
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
it goes a bit in the direction you are looking at, I think.

I would bite the bullet and put the smallest HD I could find in both the computers for the system and just use the portable one for data.

An Ubuntu system only needs about 10 - 15 GB, if you exclude personal data, so the cost of the HD should be negligible compared to the cost of effort to make the thing behave right, or at least that is how it seems to me.

---

### Post by Cheesemill on 2010-01-18
It works fine, I have a 32GB USB stick with a full install of Ubuntu on that I use on multiple computers.

---

### Post by Herman on 2010-01-18
One Ubuntu installation in an external drive can boot and run just as well in almost any computer with no problems at all.

I have an SSD with Ubuntu in it and it works very well plugged into one of my  home computers by a SATA2 cable. 
I also have an external USB drive case for it and it works quite alright in that, I can plug it into most computers and run it without any problems. 

You won't get the same performance as far as read-write speeds to and from your drive as you would if you had the same drive plugged in by IDE or SATA because the USB2 interface is not as fast. It's still a lot faster than running a Live CD though.

Ubuntu is way more advanced than other operating systems, proprietary ones in particular, and can adjust to the various different kinds of hardware as it boots. It hardly even slows that boot-up down when I change from one PC to another. 

Having Ubuntu in a USB saves me the time and effort of unplugging all kinds cables and lugging laptops around every time I want to go somewhere and of course plugging everything all back in again. At the end of a day I just leave my work laptops plugged in an unplug my USB with Ubuntu in it, put in in my pocket and go home. I already have lots of computers home I can use if I want to get a little more work done when I'm home and I have no desire to be carrying around a lot of extra stuff. Ubuntu in a USB device is a great idea.

I have Ubuntu installed in several USB flash memory sticks too, just for fun.
I use real Ubuntu installations in all of my drives. I don't know why people still do 'persistence' type of installations these days. Real Ubuntu installations are better.

---

### Post by audiomick on 2010-01-18
I happily defer to cheesemill and Herman (g'day Herman!), as they both know more about this than me...:D

---

### Post by Cheesemill on 2010-01-18
> **Herman said:**
> I don't know why people still do 'persistence' type of installations these days. Real Ubuntu installations are better.
+1. Persistent installs are much more hassle than a full install.

Just make sure when you install that you put GRUB on the external drive, it defaults to installing on the first internal disk.
Just hit the 'Advanced' button on the last page of the installation screen and select your external.

---

### Post by vanyinet on 2010-01-18
> **Cheesemill said:**
> It works fine, I have a 32GB USB stick with a full install of Ubuntu on that I use on multiple computers.

Oh, thank you. It's very a good news to me. As I said I don't want to buy HDD for 2 computers and I also have a laptop, so 1 external HDD should work on all these 3 computers.

---

