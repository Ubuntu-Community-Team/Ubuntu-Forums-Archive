---
title: "Ubuntu USB stick wont boot."
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by nlk22 on 2012-12-31
Hi,

I'm trying to install Ubuntu 12.10 on my macbook. I downloaded and put it on a usb stick as per [these]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") instructions. Everything seems to work fine until I restart my comp and try to boot from the USB: The only option it gives me is macintosh hd. The same happens when I try to boot it for another mac, so I know it's a probably with the USB stick and not my computer.

I've tried erasing everything on the USB drive and re-doing the whole process a few times. When I erase the drive with disk utility it wants me to choose a format, so i've been using MS-DOS (FAT)

Any ideas for what might make this work?

---

### Post by nlk22 on 2012-12-31
Oh end when i run the sudo dd command this is the results:

753+1 records in
753+1 records out
789884928 bytes transferred in 164.789517 secs (4793296 bytes/sec)

---

### Post by adityamagadi on 2012-12-31
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

similar procedure what you have but just the graphical and updated version of unetbootin this is... download it onto your mac by choosing the mac version and give it a try..and just insert an empty pendrive unet will do the required formatting...

---

### Post by nlk22 on 2012-12-31
> **adityamagadi said:**
> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

similar procedure what you have but just the graphical and updated version of unetbootin this is... download it onto your mac by choosing the mac version and give it a try..and just insert an empty pendrive unet will do the required formatting...

The Ubunutu website says the unetbootin will run on mac but the resulting USB stick will only boot on a windows machine. Is this correct?

I actually made a some progress, a friend suggested downloading a boot menu toolkit called rEFIt. This allowed me to boot Ubuntu, which then gives me the option to either run it from the USB drive or install it alongside my current OS. When I try to run it from everything just freezes.

---

### Post by adityamagadi on 2012-12-31
i dont think that is true, anyways giving a try wont hurt :)

---

