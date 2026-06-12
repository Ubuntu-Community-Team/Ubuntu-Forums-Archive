---
title: "New build, nothing but problems. Errno 5, can´t use radeon driver"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by Nymunariya on 2013-01-20
I know this errno has been posted elsewhere, but the thread has been marked solved, and I still have the issue, along with other issues and I don´t know what to do. (I also don´t know if this is the right place to post. It seemed to be a problem during installation ...)

I built a computer. AMD Phenom II 945, ASRock 990fx Professional, Corsair CL9 2x4GB ram, Saphire 6570 4GB DDR3.

I can boot into ubuntu without a problem, (half the time. The other half, apps on the live cd fail to launch) but I´ve also never had as many error reports. It´s been nothing but error reports the entire time (hardware problems?), wether installing or just using the live cd.

During installation, I get the errno 5, and I´ve tried the [ubiquity --no-migration-assistant ]("http://ubuntuforums.org/showthread.php?t=1910258"), but the error still comes up.  When getting more info, it´s a SquashFS error, and on the ([Squashfserrors ubuntuwiki page ]("https://help.ubuntu.com/community/SquashfsErrors") it said bad memory. Bad cd/dvd (running from flash), bad iso (checksum was good), bad cable (using back panel)

Ran memtest86+ on the ubuntu live cd, and got about 10000 errors per minute. So bad ram ?

I dd´d the iso onto a flash drive, so that should all be in order. And I´ve only gotten the iso´s from ubuntu.com. Tried 12.10, 12.04, and Elementary OS (12.04). I have been able to install from the iso on my macbook air without a problem. 

I´m really in over my head here and I don´t know what to do. I don´t have money to send back/get new ram until the end of the month.


Thanks.


(I also have a problem with the radeon drivers. Should I put that here too, or better in another subforum?)

---

### Post by darkod on 2013-01-20
Well, if memtest says your ram has errors, why would you doubt it? If you have two or more modules, I would take them out and check them one by one. Maybe only one is bad.

Until you get the ram sorted out, don't bother with anything else since other errors can easily be a result of the ram problem because everything goes through ram.

---

### Post by Nymunariya on 2013-01-20
I only have my two sticks, but I don´t have the money to do anything about it until the end of the month =(  I´m not doubting it ... I just can´t really do anything about the physical side right now.

But I´ll definetly try each stick separately. Better than nothing.

---

### Post by Mark Phelps on 2013-01-20
> **Nymunariya said:**
> (I also have a problem with the radeon drivers. Should I put that here too, or better in another subforum?)

Recent Ubuntu versions come with very good default Radeon drivers.  I've been using them for a while now and have no problems with them -- dual monitors, different sizes, full resolution on each.

Unless you're demanding hardware accelerated 3D graphics, or you need to control the GPU temps, you don't really need the fglrx drivers -- and with 12.10, they have shown to be a lot of problems.

I would go back to the default Radeon drivers (once you get the memory failures solved) and see how well those behave.

---

### Post by Nymunariya on 2013-01-20
> **Mark Phelps said:**
> Recent Ubuntu versions come with very good default Radeon drivers.  I've been using them for a while now and have no problems with them -- dual monitors, different sizes, full resolution on each.

Unless you're demanding hardware accelerated 3D graphics, or you need to control the GPU temps, you don't really need the fglrx drivers -- and with 12.10, they have shown to be a lot of problems.

I would go back to the default Radeon drivers (once you get the memory failures solved) and see how well those behave.

well it was only one bad stick of ram. Got that out and everything is running fine.

As for the radeon drivers, they still won´t go. I´m wondering if it´s something to do with kernel modsettings, and not being able to use it? *Shrugs*

---

### Post by joel@parke.ods.org on 2013-01-20
Many memory sticks have a LONG warranty -- check that out.  I usually buy from NewEgg and I have had very good support in replacement memory when I had one bad stick ~ 3 years ago.  Hope this helps... maybe you don't have to wait to the end of the month.

---

### Post by darkod on 2013-01-21
> **joel@parke.ods.org said:**
> Many memory sticks have a LONG warranty -- check that out.  I usually buy from NewEgg and I have had very good support in replacement memory when I had one bad stick ~ 3 years ago.  Hope this helps... maybe you don't have to wait to the end of the month.

I agree. Definitely check that, some even have lifetime warranty. Even if the shop/website where you bought it gives you like 1-2 years of warranty, if the manufacturer offers lifetime you can usually do a RMA process directly on their website.

---

