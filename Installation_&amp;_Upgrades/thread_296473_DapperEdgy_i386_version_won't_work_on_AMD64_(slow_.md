---
title: "Dapper/Edgy i386 version won't work on AMD64 (slow + freeze)"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2006-11-09
When I try to install the i386 version of both Dapper and Edgy the computer seems to run very slow (he disk access and cd-rom access is very slow) and freezes at random times during the installation.

The AMD64 version installed just fine.

What can be the problem? I really lik to run the i386-version, as the AMD64 version seems overkill for my small media computer. And I really want everything to work nicly out of the box, and 32 bit seem more "tested".

I have an AMD Athlon 64 3500+ with 512 MB dual channel DDR2 RAM (667 MHz).
My Motherboard is a Asus M2NPV-MX GeForce 6150 nforce 430.

---

### Post by bulldog on 2006-11-09
Do you have an AM2 AMD 3500?

If not,you have the wrong RAM installed.
DDR2 isn't working with AMD processors to my knowing.

---

### Post by rsambuca on 2006-11-09
The Asus M2NPV-MX does support DDR2.

---

### Post by zooounds on 2006-11-10
> **bulldog said:**
> Do you have an AM2 AMD 3500?

If not,you have the wrong RAM installed.
DDR2 isn't working with AMD processors to my knowing.


It's a AM2 version and it does (only) support DDR2 (up to 800 MHz).

---

### Post by zooounds on 2006-11-10
A bios upgrade seemd to do the trick.

Now I was able to install the 32-bit version.

BUT

As soon as I enable AMD Cool 'n' Quiet (CPU freq stepping) things seem to freeze at random.

The last lnie in syslog before complete freeze and reset was something about changing the stepping...

Anyone have any idea?

---

### Post by rsambuca on 2006-11-10
I have a little older system than yours, but I have never had much success with the cool 'n' quiet feature.  I always had some sort of problem so I have since disabled it.

---

### Post by bulldog on 2006-11-10
I have an X2 too,but had never problems with cool and quit exept it slows down your computer quit a bit.

I turned it off and all works fine,CPU temp is 33 degree's Celsius so I can live with that.

---

