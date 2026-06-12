---
title: "Not Booting after clean install of ubuntu"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by astroboy123 on 2011-04-04
Hi All,

I install 10.10 64 bit onto my home DIY server.

but after i install the Ubuntu and boot from that HDD, it hangs on a black screen with a single flashing white line on the left hand side.

I have installed the OS on a 80 gig HDD, that is connected via a esata to sata cable.

the onboard sata ports are filled up by 6 2tb HDD and i plan to have these HDD running on ZFS-fuse.

But i cant boot into the OS after the install on to the 80 gig HDD.

Thanks in advance.

astro

---

### Post by Hedgehog1 on 2011-04-04
Please read and follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)

***The Hedge***

:KS

---

### Post by astroboy123 on 2011-04-05
hey mate, thanks.

i worked it out.

i hadn't created a /boot partition.

---

### Post by kiran1247 on 2011-04-05
Hi,

What's the purpose of "nomodeset" parameter?

I do have similar issue like unable to get login screen , instead stopped by black-screen but with different lines.

I'm assuming that this might fix my issue also , but just want to know what for this nomodeset parameter for..


thanks
kiran

---

### Post by Hedgehog1 on 2011-04-05
The boot process normally check to see what 'modes of operation' are support by your video card (640x480, 1280x1024 and so on).  This works OK with most desktop cards and and 2/3rds of the laptop cards.  Other cards hang on this check, so we turn it off in hopes of getting your PC booting.

***The Hedge***

:KS

---

