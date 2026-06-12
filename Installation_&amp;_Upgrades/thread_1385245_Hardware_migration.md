---
title: "Hardware migration"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by adrianecole on 2010-01-19
Hi Everyone

Im running Ubuntu-server 8.04.1 LTS version

I'm replacing my old P4 home server with a new Atom based, low power setup and I was wondering if I could just move the HDD over from the old P4 and put it in the Atom Machine? Will it boot up or will the hardware differences chipset, CPU etc mean this is just destined to fail?

I don't want to re-install everything and have to move all my date over unless I have to. I have asterisk, samba, mysql, apache and a whole load of other stuff all set up and working just how I like it.

Is there an easy way to do this by any chance?

Thank for any advice!
Adrian

---

### Post by audiomick on 2010-01-19
I am far from an expert on this, but from what I have read, there is a chance that it might work. You may have to add some drivers, perhaps.

Wait for some more replies before you try anything...;)

---

### Post by mk1w86 on 2010-01-19
In theory it is possible but you might have to reconfigure some drivers.  Once on a Debian machine I changed a network card and had to manually configure it to be eth0 but I don't know if it is the same on Ubuntu. :-k

Also I am currently thinking of changing my PII and PIII servers over to Atom boards to cut down on running costs.  Out of interest what Atom hardware do you have? :biggrin:

---

### Post by adrianecole on 2010-01-20
I've gone for a D945GCLF. Its my first foray into Atoms, its not arrived yet from the supplier, I'll let you know how it goes. :)

---

### Post by Cheesemill on 2010-01-20
It should work fine, I've done this on countless Ubuntu installations.

---

### Post by mk1w86 on 2010-01-20
> **adrianecole said:**
> I've gone for a D945GCLF. Its my first foray into Atoms, its not arrived yet from the supplier, I'll let you know how it goes. :)

Thanks for that. :D

I don't want to derail your thread, but I was actually looking at the Intel D945GCLF2 which I think is a second edition of your motherboard.  The main differences I can see is that it has an Atom 330 and gigabit ethernet.

[http://www.intel.com/products/desktop/motherboards/D945GCLF2-D945GCLF2D/D945GCLF2-D945GCLF2D-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GCLF2-D945GCLF2D/D945GCLF2-D945GCLF2D-overview.htm)

I was also looking at the Asus AT3GC-1:

[http://asus.com/product.aspx?P_ID=DOQqfPDClKd1VPkC&templete=2](http://asus.com/product.aspx?P_ID=DOQqfPDClKd1VPkC&templete=2)

One of my main concerns about these motherboards is how noisy the CPU fan is; small fans are often quite loud.  I have seen some passively cooled boards but they all seem a bit pricey. :(  My previous experience with Atoms has only been in netbooks.

---

### Post by adrianecole on 2010-01-25
Actually, my board is the '2' version. It just arrived today. I pulled out my old HDD and put it in the new machine and it came straight up.

All I've had to do so far is alter some network settings, for some reason my machine insists my network interfqce is now eth2 and not eth1. this aside, which was an easy fix, it all seems to be working fine.

As to noise, well the fan is on all the time, I'm going to look into fan control now to see if its bios or software controlled.

But its been easy so far!

---

