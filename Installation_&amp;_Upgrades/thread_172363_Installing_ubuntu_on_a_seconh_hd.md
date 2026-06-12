---
title: "Installing ubuntu on a seconh hd"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by Sofy on 2006-05-08
Hi guys...I Have a hd of 80gb with windows xp but I'd like to put in my pc another hd of 20gb where I want to install unbuntu breezy 5.1...could you help me?:D I'm not so expert so tell me what I have to do!!!!TAnks...Bye!!!!!!!!!

---

### Post by Kurt` on 2006-05-08
Well, what exactly do you need help with? Choosing which CD image to download? How to burn it to a disc?

Need more details man ;)

---

### Post by Irony on 2006-05-09
See [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) - though for a beginner I think its more simple to do what you want to do.

First unallocate your second hard drive by booting into windows going to;

*Computer management > disk management*

right click on the second hard drive and delete it. It change to an unallocated space (free space).

Now boot up from the Ubuntu disk and choose to install to the second hard drive which will be hdb (hda being the first drive).

The hdb should show up as as 20 Gig free space, install to it - choose the automatic install option which will partition the 20 Gig into root and swap partitions automatically.

Install Grub to the MBR it will detect windows.

---

