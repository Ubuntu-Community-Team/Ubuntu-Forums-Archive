---
title: "SATA and gigabit LAN (ASUS P5S-MX) install problem"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by dwek on 2007-09-22
Hi all,

I have built a new system with the following specs:
ASUS P5S-MX motherboard (Intel® Core™2 Duo/ Pentium)
SATA1 - 80Gig Seagate HDD (Southbridge SIS968)
SATA2 - LG DVD
1 Gig of DDR2

I have been trying to install Ubuntu 7.04 Server, with no luck.
On install the SATA HDD and gigabit network card (SIS 968) are both not recognised.

I have noticed that drivers are available for Mandriva2007, RHES4.4 and sus10.1.
As my preference would be to run Ubuntu, can anyone provide some guidance with this, otherwise I will need to install one of the other Linux variants to get the machine going.

Thanks in advance.
Dwek

---

### Post by dwek on 2007-09-23
Hi...

Me again.
I have been successful getting the SATA HDD going by setting the SATA bios IDE setting to a AHCI.

Ubuntu 7.04 now recognises it.

I have given up for the time being, trying to get the gigabit NIC going.
So I have disabled it in the BIOS and put a Compaq 10/100 card in.

Dwek

---

### Post by _logic on 2007-10-25
just read this thread:

[http://ubuntuforums.org/showthread.php?t=482284](http://ubuntuforums.org/showthread.php?t=482284)

and it worked perfectly! i did start to disable the LAN in BIOS but I think my coffee made me adventurous .... :wink:

---

