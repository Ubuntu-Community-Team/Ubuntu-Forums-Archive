---
title: "What does this mean?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by merher on 2007-01-26
ok i tried installing the alternate cd and got this when i chose the text install and oem install:

[IMG]http://img.photobucket.com/albums/v144/Black_op51/Prob1.jpg[/IMG]

so i added noapic and got this error:

[IMG]http://img.photobucket.com/albums/v144/Black_op51/Prob2.jpg[/IMG]

what do i need to do and what does this mean?

---

### Post by an.echte.trilingue on 2007-01-26
Are you sure this machine works? (ie, have you booted it with other OSs?)

If so, what is your mobo?

---

### Post by merher on 2007-01-26
This computer is brand new and runs windows xp media center edition perfectly. 

my mobo is an [EVGA 122-CK-NF68-AR LGA 775 NVIDIA nForce 680i SLI]("http://www.newegg.com/Product/Product.asp?Item=N82E16813188009")

I also have the latest BIOS update (1/12/2007).

---

### Post by an.echte.trilingue on 2007-01-26
After a bit of googling, it looks like this is a known BIOS bug in some NVidia chipsets.  NVidia is working on it.  There is also a kernel patch in the works, but the earliest that will hit ubuntu is 7.04.

Probably the easiest way around this is to try Ubuntu 6.06 LTS (by far superior to 6.10, in my opinion) or maybe the debian etch netinstall.

Take care,
-mat

---

### Post by merher on 2007-01-27
When I got this error I was using the 6.06 alternate cd, so after your suggestion of trying a differnt alternate cd I found that the 6.10 alternate cd does work with this 680i motherboard.


so everything installed including GRUB, but the Nvidia 8800 is still not supported in the x server so I can't use Ubuntu Graphically, but I can use the command line. Is there anything I can do about this or do I have to wait until the next version of Ubuntu?

---

