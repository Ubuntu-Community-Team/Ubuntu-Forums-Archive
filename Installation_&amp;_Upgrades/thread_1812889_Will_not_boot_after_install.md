---
title: "Will not boot after install"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by skubasteev on 2011-07-26
I have tried 11.04 and 10.10 64 bit and after I install the OS my laptop will not boot.  The install goes great after being booted from a USB but after the install when it tries to boot from the HDD all that happens is the screen lights up and goes dark repeatedly. 

Any ideas?

---

### Post by plusnplus on 2011-07-27
Hi..,
i also have same experience.
i install 10.04 64 bit alt version to my desktop.
the installation smooth.
but when the pc boot up, i only can see ubuntu word and 3 dot in the center.
after that the screen blank. i wait until 30 min, the screen still blank.
my pc only have 1 OS (the ubuntu that i just want install)

---

### Post by plusnplus on 2011-07-28
hi skubasteev,
i solved my problem by:
install 8.04 64 bit alt version.
installation smooth and i can login.
use software update, update it to 10.04.
updating smooth but the problem still same, blank screen after grub.
But at least the grub option is show.
i choose recovery mode and able to login.
use hardware driver and update the graphic card (i use ati 5670)
now i able to login with normal mode.

hope it help you.

---

### Post by Hakunka-Matata on 2011-07-28
nomodeset is what you need most likely.  This gets added to a line in the grub entry for starting your system.  It's done at the time of startup, 

It's a very common problem, try [http://www.google.com/#hl=en&cp=17&gs_id=1o&xhr=t&q=nomodeset+ubuntu+11.04&pf=p&sclient=psy&source=hp&pbx=1&oq=nomodeset+ubuntu+&aq=0&aqi=g3g-v2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=abb1f03500b21ec4&biw=1680&bih=884](http://www.google.com/#hl=en&cp=17&gs_id=1o&xhr=t&q=nomodeset+ubuntu+11.04&pf=p&sclient=psy&source=hp&pbx=1&oq=nomodeset+ubuntu+&aq=0&aqi=g3g-v2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=abb1f03500b21ec4&biw=1680&bih=884)

and see how it plays.  You can find many more posts on it by searching for "add nomodeset"

here's a post on it here in ubuntuforums:  [http://ubuntuforums.org/showthread.php?t=1613132&highlight=add+nomodeset](http://ubuntuforums.org/showthread.php?t=1613132&highlight=add+nomodeset)

---

