---
title: "Inspiron 1501 and 8.04"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by canadianbaptist on 2008-05-07
Hi. I would like to hear from any Inspiron 1501 people out there regarding upgrading from 7.10 to 8.04.

Any problems, advantages or disadvantages? Does Hibernate work?

Thanks

---

### Post by Playa1313 on 2008-05-07
Hello, I have an Inspiron 1501 with an ATI 1150 integrated graphics card and an AMD Turion 64 x2 TL-50 processor.

I upgraded from Gutsy to Hardy when it was in beta and everything went perfectly. However, I wanted to do a clean install anyways, so I did. (I just transferred my files and settings over manually)

I tried Hardy 64-bit, but at the moment there are problems with the fglrx driver and the ATI 1150 on Hardy 64-bit.  These problems lead to choppy compiz cube rotation, etc. (it would not bother someone who did not use the compiz cube very much or compiz at all)

Therefor, I have stayed with Hardy 32-bit and things are working just fine.  I am yet to have suspend work, but I think Hibernate works (I will try it again after finishing this post).

Anybody with a Broadcom 43xx wireless network card (note that wired connection still works) will have to go this [tutorial/help site]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy"), which is pretty straight-forward for setting it up.

For the brightness keys (Function + Up or Down), you will need to follow these instructions:
```

To fix brightness, it's easy as just editing two script files. No bios change whatsoever.

sudo gedit /etc/acpi/video_brightnessup.sh

replace everything in the file with

#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
12)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac



sudo gedit /etc/acpi/video_brightnessdown.sh

replace everything in the file with


#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

12)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
100)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac
```

If you need any more information, a good site to go to us [http://www.ubuntu1501.com](http://www.ubuntu1501.com).  This is a blog site that gives the latest news and guides for Ubuntu on an Inspiron 1501.

---

### Post by redDEADresolve on 2008-05-13
I'm loving it. Gutsy was a mess on the 1501.

---

### Post by CheshireMac on 2008-05-22
Hey folks. I'm trying to get my friend's 64bit Inspiron 1521 to run Compiz a little more smoothly. The cube is acting really choppy. Without rotation, it shows up in triangles and it's really annoying to work around, and we ended up just turning the cube off altogether. 
I'd like to figure out a way to get it running a little smoother, and she's walking blind as I coach her on Linux. 
Thanks for any thoughts. My Compiz is running like a dream, minus the fact that my machine is older than God. She's jealous.

---

