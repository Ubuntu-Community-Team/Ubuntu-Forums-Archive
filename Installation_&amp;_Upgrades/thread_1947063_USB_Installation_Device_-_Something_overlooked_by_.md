---
title: "USB Installation Device - Something overlooked by many. [kernel panic!]"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by Cinelli on 2012-03-26
Regarding the USB Installer issue. What is the  overall capacity of the USB stick that you're trying to use? I ask this  because I've been fiddling with this issue for the past three or four  hours trying different things. And finally I think I've come up with  something. 

  Then I started thinking about the File Systems and how it's logic  works when determining the difference between a USB Flash Drive and a  USB Hard drive. So with my 5gb USB Stick everything worked out cherry.  Then going through the same exact steps and attempting it on my 16gb USB  stick I would get the "Panic!". 

Even though when mounting a USB device, whether or not it's a flash  drive or a external hard drive, is referenced by the user the same way  the way the File System manages the amount of space has to be different  (especially when your trying to use Fat32). Try mounting it on a smaller  partition something ~5gbs or so. I tested this on 5 different larger  USB sticks and 5 different smaller (under 8gb) USB sticks and the  results stuck all the way through. 

  Let me know if you end up testing this out. Because I had this  problem for a while with multiple different distro's (Google the kernel  panic with any distribution, Gentoo, Ubuntu, Fubuntu, Mandriva, Puppy..  Pepperment... you get the idea). So I've, in my own mind at least, ruled  out it possibly being the developers. 

Also, I have confirmed that alll the USB devices that were used to attempt a "FROM  USB" (five total) that I used them with that, after creating a smaller  (4gbs is what I decided to go with) partition for the installer to be  placed on all the devices that failed now work without an issue.
  Softwares tested: Lili Live USB Creator, Pen Drive Linux, Unetbootin, & dd Linux console tool.
  

Federico Cinelli
CINELLI Motorsports LLC
Stay true.

---

### Post by mastablasta on 2012-03-26
you mean you were creating LiveUSB key using ISO image with those programmes or you want to install linux on USB?

---

### Post by Cinelli on 2012-03-27
> **mastablasta said:**
> you mean you were creating LiveUSB key using ISO image with those programmes or you want to install linux on USB?

Yes. I was creating LiveUSB devices.

---

