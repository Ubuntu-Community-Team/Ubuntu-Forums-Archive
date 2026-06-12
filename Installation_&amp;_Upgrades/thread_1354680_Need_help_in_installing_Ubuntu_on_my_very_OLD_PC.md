---
title: "Need help in installing Ubuntu on my very OLD PC"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by chrismt on 2009-12-14
I have a Pentium 4 PC with only 128 MB RDRAM running Windows XP, tweaked.
 
Is it possible for me to install Ubuntu 9.10 and I already have the cd that I got in my mail.
 
Can somebody guide me?
 
Chris

---

### Post by pi4r0n on 2009-12-14
> **chrismt said:**
> I have a Pentium 4 PC with only 128 MB RDRAM running Windows XP, tweaked.
 
Is it possible for me to install Ubuntu 9.10 and I already have the cd that I got in my mail.
 
Can somebody guide me?
 
Chris

Of course it is possible to install it :) just follow steps in this [link]("http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml")

---

### Post by mkvnmtr on 2009-12-14
You do not have enough ram to have a usable distro. A 512 Mb stick will make your unit run great with Ubuntu. That is what I am using on the old computer I a using now.

---

### Post by fancypiper on 2009-12-14
I installed Ubuntu 9.10 on an old eMachines with the same memory but a slower Celeron processor with the graphic installer.  It took a while to boot up from the CD, but to my amazement, it ran the live CD and installed OK. It ran gnome slightly faster than it did Windows XP and switching to fluxbox, it ran even faster!

Max out the memory if you can.

If that fails, try the alternate install

---

### Post by kellemes on 2009-12-14
> **mkvnmtr said:**
> You do not have enough ram to have a usable distro. A 512 Mb stick will make your unit run great with Ubuntu. That is what I am using on the old computer I a using now.

Indeed, upgrade RAM or use another distribution, Ubuntu won't run.
Just a couple of distributions that may run on your system..
[Puppy Linux]("http://www.puppylinux.com/")
[Absolute Linux]("http://www.absolutelinux.org/")
[SliTaz]("http://www.slitaz.org/")
[TinyMe]("http://tinymelinux.com/doku.php")

For a complete list of distributions, you can visit [DistroWatch.com]("http://distrowatch.com/").

---

### Post by lavinog on 2009-12-14
It will work, but it will be slow.  You will need to use the alternate install disk.
I know your pain...those rdram p4s are worthless to upgrade, for the cost of a ram upgrade you can buy a brand new computer.

It would be better to install a minimal ubuntu system using the server disk.
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by Bartender on 2009-12-14
lavinog spotted what I'd missed - the "R" in front of "DRAM" in the original post.

Since it's that RDRAM that's killing you, I have an alternate suggestion.  What about a new motherboard that can run modern, cost-effective RAM?  You have to be a little bit careful when shopping because there are lots of LGA 775 boards available, but quite a few of them are running newer chipsets that support the Pentium dual cores and Core 2 Duo's but not the single core Pentium's.

I'm on dial-up so it takes forever to shop around, but I think [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131394") is a good example (?)

Maybe someone can verify this for me.  I think what I'm seeing is when the South Bridge is an ICH7 chipset it'll run Pentium's but when it's ICH10 the board will only run Pentium D's.

If you've been thinking about building a PC, this might be the perfect opportunity.  You could re-use your case, power supply, optical drive, etc.  Since you'd have SATA connectors on a newer board, you could buy a board, RAM, and a SATA HDD and you'd be in business.

---

### Post by cascade9 on 2009-12-14
> **fancypiper said:**
> If that fails, try the alternate install
 
 This should work and be pretty usable...more usable than XP anyway. If it does, try this- 

> **kellemes said:**
> Indeed, upgrade RAM or use another distribution, Ubuntu won't run.
Just a couple of distributions that may run on your system..
[Puppy Linux]("http://www.puppylinux.com/")
[Absolute Linux]("http://www.absolutelinux.org/")
[SliTaz]("http://www.slitaz.org/")
[TinyMe]("http://tinymelinux.com/doku.php")

For a complete list of distributions, you can visit [DistroWatch.com]("http://distrowatch.com/").

> **Bartender said:**
> lavinog spotted what I'd missed - the "R" in front of "DRAM" in the original post.

Since it's that RDRAM that's killing you, I have an alternate suggestion.  What about a new motherboard that can run modern, cost-effective RAM?  You have to be a little bit careful when shopping because there are lots of LGA 775 boards available, but quite a few of them are running newer chipsets that support the Pentium dual cores and Core 2 Duo's but not the single core Pentium's.

I'm on dial-up so it takes forever to shop around, but I think [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131394") is a good example (?)

Maybe someone can verify this for me.  I think what I'm seeing is when the South Bridge is an ICH7 chipset it'll run Pentium's but when it's ICH10 the board will only run Pentium D's.

If you've been thinking about building a PC, this might be the perfect opportunity.  You could re-use your case, power supply, optical drive, etc.  Since you'd have SATA connectors on a newer board, you could buy a board, RAM, and a SATA HDD and you'd be in business.

Nice idea, but sorry, wont work. As far as I know, there was never a socket 775 RDRAM motherboard, so the OP cant just upgrade the board. Its probably a socket 423, theres not much chance of finding one of them new anymore.

I'd be wary of using the power supply from an old RDRAM board in something newer. Even if its not old, very tired, and low power output, lots of motherboards want 24pin ATX, not the older 20 pin ATX. Reusing the case, optical drive and hdd should be fine, provided that you get a motherboard that supports IDE (some motherboards dont have an IDE port now)

---

### Post by fancypiper on 2009-12-14
Another way I installed Ubuntu on my old machine was to download and install the server iso.  Install that, then login and command:

sudo apt-get install fluxbox

Follow the suggestions given until you can successfully command:

startx

Eventually, you should have a lean, mean machine running a pretty snappy windows manager (rather than a desktop environment).

---

### Post by lavinog on 2009-12-14
You can save the case, powersupply, hd, and optical drive...but would it be worth it.
I am assuming this system was built in 2001.
The case could be a special design that will not work with modern mobos (i know some dell systems have a special connector layout)

the powersupply would likely be inadequate, and on its last leg...changing the power demand drastically could cause it to fail...and destroy the new components.

the hd is likely near its end of life.

The optical drive could be reused, but I have found them to only be reliable up to 5 years.  Dust and drive wear leads to more read errors...even though the drive would still work, a $20 dvd burner would easily out perform it.

For the time being give ubuntu a try, but I would invest in a new computer soon. A decent machine can be found for $300 in the states.

---

### Post by Bartender on 2009-12-14
RDRAM dates all the way back to 2001?  Sheez.  In that case, you're right, probly not worth it.  

cascade mis-read my suggestion.  I was suggesting abandoning RDRAM by going to a newer board.

And, yeah, if it's a Dell, with one of those damned alternate ATX pinouts, that's another nail in the coffin.

I know lots of manufacturers have pulled off questionable proprietary tactics, but what Dell did with those ATX power supplies and motherboards was downright inexcusable.

---

### Post by i.r.id10t on 2009-12-14
I would definately recommend the RAM upgrade as well - you have a very fast CPU, but no memory to speak of.  You are driving a Porsche in a parking lot - your top speed will be 40, but you can get there *fast*.

That said, for now you can use the alternate install CD and install fine on that box.

---

### Post by lavinog on 2009-12-14
> **i.r.id10t said:**
> I would definately recommend the RAM upgrade as well - you have a very fast CPU, but no memory to speak of.  You are driving a Porsche in a parking lot - your top speed will be 40, but you can get there *fast*.

That said, for now you can use the alternate install CD and install fine on that box.

You are not familiar with rdram prices are you?

---

### Post by raymondh on 2009-12-14
You can also try MASONUX .... it is ubuntu-based and uses LXDE.  Very speedy on my P3 machine.  I have installed this little distro/derivative on 3 machines now and is reliable and consistent.

[http://sites.google.com/site/masonux/](http://sites.google.com/site/masonux/)

Forum-member EARTHPIGG is involved in its' development and is very active in maintaining MASONUX.

Regards,

---

### Post by cascade9 on 2009-12-14
> **Bartender said:**
> RDRAM dates all the way back to 2001?  Sheez.  In that case, you're right, probly not worth it.  

cascade mis-read my suggestion.  I was suggesting abandoning RDRAM by going to a newer board.

And, yeah, if it's a Dell, with one of those damned alternate ATX pinouts, that's another nail in the coffin.

I know lots of manufacturers have pulled off questionable proprietary tactics, but what Dell did with those ATX power supplies and motherboards was downright inexcusable.

All I can say about dell is *waving fist/storm cloud*

RDRAM dates back to earlier than that, late 1999 for P3s (840 chipset) , 2000 on P4 boards (850 chipset). The 850E came out in mid-2002 and that's the last chipset released using RDRAM. They started disappearing when 800Mhz P4 chips took over (850E was a 5333Mhz FSB revision of 850 @ 400, there was no 800Mhz FSB RDRAM chipsets). 

BTW, ICH7 vs ICH10, It all depednds on the northbridge in the chipset. Some northbridges with ICH7 are core 2 duo/quad only- G41/ICH7. ICH10 is only used on northbridges for core 2 duo/quad or i7/i9. 

I read your suggestion as "keep your current CPU and get a socket 775 board". Like I said, not do-able. There were no LGA 775 motherboards with RDRAM, they were all socket 423 or socket 478.

---

### Post by snowpine on 2009-12-14
Ubuntu requires 384mb minimum (more is better).

The only Linux distribution I can personally recommend for 128mb of ram is [Puppy Linux.]("http://www.puppylinux.org")

---

