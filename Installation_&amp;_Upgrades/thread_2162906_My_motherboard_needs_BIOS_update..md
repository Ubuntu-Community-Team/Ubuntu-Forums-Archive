---
title: "My motherboard needs BIOS update."
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by Ludowicus on 2013-07-16
I need the latest BIOS update for [this]("http://www.gigabyte.com/products/product-page.aspx?pid=3907#bios") motherboard, but there is no downoad for Linux.
Please tell me how I update my BIOS! Can I install Windows, run the BIOS update and then go back to Ubuntu?
Or is there another way for installing BIOS updates on Linux?

---

### Post by dino99 on 2013-07-16
that one seems to be the latest you need : [http://www.gigabyte.com/products/product-page.aspx?pid=4396&dl=1#bios](http://www.gigabyte.com/products/product-page.aspx?pid=4396&dl=1#bios)

the bios is related to the hardware; not to the running OS : you then can load all kind of OS (win, linux, osx, ...)

---

### Post by Cheesemill on 2013-07-16
> **dino99 said:**
> that one seems to be the latest you need : [http://www.gigabyte.com/products/product-page.aspx?pid=4396&dl=1#bios](http://www.gigabyte.com/products/product-page.aspx?pid=4396&dl=1#bios)

the bios is related to the hardware; not to the running OS : you then can load all kind of OS (win, linux, osx, ...)

What makes you think that?
Your link is for a different motherboard than the one in the OP.

@Ludowicus

The .exe BIOS files that you get from Giga-Byte are usually DOS executables. This means that you can use [UNetBootin]("apt://unetbootin") to create a FreeDOS bootable USB stick. Copy the BIOS file to this FreeDOS USB and then boot from it. This will get you to a DOS prompt that you can run the BIOS update from.

---

### Post by dino99 on 2013-07-16
ah my bad, i've glanced too quickly : rev1.1 card model / bios rev confusion
[http://www.gigabyte.com/products/product-page.aspx?pid=3907&dl=1#bios](http://www.gigabyte.com/products/product-page.aspx?pid=3907&dl=1#bios)

---

### Post by Ludowicus on 2013-07-16
@Cheesemill Thank you :)

---

