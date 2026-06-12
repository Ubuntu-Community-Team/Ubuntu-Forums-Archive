---
title: "Is this the ture picture?"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-09
I've just tried out the "try Ubuntu" feature in its netbook edition, and the experience is absolutely impressive. However, some of the desired feature seems not working, eg. I cannot load some linux applications.

I was wondering if there is any difference between the "try Ubuntu" and the full installation? 

BTW, I boot from a USB drive, and my netbook is Samsung N310.

---

### Post by tommcd on 2010-11-09
> **zhaotianwu said:**
> I've just tried out the "try Ubuntu" feature in its netbook edition, and the experience is absolutely impressive. However, some of the desired feature seems not working, eg. I cannot load some linux applications.
What apps are you trying to load? You should be able to load everything that is on the live CD (or usb in your case). 
> **zhaotianwu said:**
> 
I was wondering if there is any difference between the "try Ubuntu" and the full installation? 

The "try Ubuntu" option is like running from the live CD. It all runs in memory and does not install anything on the computer. After installing Ubuntu to the hard drive it will boot from and run from the hard drive. You will be able to configure things to your liking, install software and drivers, etc. The settings and apps will persist the next time you boot the computer.

Write back if you need more help.

---

### Post by sikander3786 on 2010-11-10
> I cannot load some linux applications.

I get a feel like you want to do a persistent install on your USB and save all your config/data when you reboot?

I don't exactly get what you mean by "load some applications". If the applications are not listed, you can install them from Software Center.

Or you mean you are unable to open up some of them?

---

### Post by zhaotianwu on 2010-11-10
> **sikander3786 said:**
> I get a feel like you want to do a persistent install on your USB and save all your config/data when you reboot?

I don't exactly get what you mean by "load some applications". If the applications are not listed, you can install them from Software Center.

Or you mean you are unable to open up some of them?


Yes, I'm considering using usb-boot permanantly, is it good?

---

### Post by sikander3786 on 2010-11-11
> **zhaotianwu said:**
> Yes, I'm considering using usb-boot permanantly, is it good?
Yes that can be done, except the fact that it would be a bit slower than the complete install. Some people say that it decrease the life of USB drives. Its a different debate :-)

You can do that persistent install from Ubuntu from System > Administration > Startup Disk Creator.

Otherwise you can always do a complete install on your USB drive just like you'd have installed it on a proper HDD. It is important that you install Grub (the Ubuntu bootloader) to the MBR of your USB drive. If you are not sure how to do that, it is much better and safe to disconnect all the internal HDDs during installtion to the USB, so that you do not mess up you existing systems.

---

