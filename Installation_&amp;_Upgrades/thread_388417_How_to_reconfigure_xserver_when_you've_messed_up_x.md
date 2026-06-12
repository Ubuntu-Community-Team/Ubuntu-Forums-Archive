---
title: "How to reconfigure xserver when you've messed up xorg.conf"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by DrQuincy on 2007-03-19
Hi there

I have a problem in that I've made an error in my xorg.conf file and when I boot up the screen doesn't display properly.

How do I boot up Kubuntu to the command line?  If I do that can I run dpkg-reconfigure xserver-xorg so I can get my picture back?

---

### Post by dfreer on 2007-03-19
You can either use <Ctrl><Left-Alt><F1> to change to a virtual terminal, or you can reboot and login to the recovery mode. sudo dpkg-reconfigure xserver-xorg should work... but I normally edit the xorg.conf file by hand. :) If you want help with that, you can post your video card/monitor specs and your xorg.conf file. Good luck!

---

### Post by floke on 2007-03-19
Lesson learned: always make a backup - I learned this the hard way too.
To back up: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
If anything goes wrong - to restore: sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Above post should help you fix it.

---

### Post by DrQuincy on 2007-03-19
Thanks for both those useful points.  I started a new job today and am setting up an all-round web development machine . . . the last one I did was about 18 months ago.  It's coming back to me . . . slowly.

Thanks again.

---

