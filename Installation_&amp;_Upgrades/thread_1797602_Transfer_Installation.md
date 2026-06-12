---
title: "Transfer Installation?"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Kvothe666 on 2011-07-05
I have Ubuntu 11.04 installed and running on my laptop and was wondering if there was any way to create an install disc/usb or some other way to install Ubuntu in its current state (including all apps, updates, settings etc.) onto my desktop.

---

### Post by mörgæs on 2011-07-05
Hi, welcome to the fora.

Yes, you can try Clonezilla.

---

### Post by Kvothe666 on 2011-07-06
ok, used clonezilla to copy the partition over & it boots up, but the graphics output is not working correctly. I have it connected to a hdtv via component (from s-video socket), however the highest resolution it will allow is 1024x768(same as max for s-video & composite if im not mistaken) and the picture is VERY blue, which leads me to believe that it is only using one of the three cables to transmit the signal, any suggestions to rectify??

---

### Post by varunendra on 2011-07-06
> **Kvothe666 said:**
> ok, used clonezilla to copy the partition over & it boots up, but the graphics output is not working correctly. I have it connected to a hdtv via component (from s-video socket), however the highest resolution it will allow is 1024x768(same as max for s-video & composite if im not mistaken) and the picture is VERY blue, which leads me to believe that it is only using one of the three cables to transmit the signal, any suggestions to rectify??
It doesn't matter how graphics are while being in clonezilla live - means it won't affect your partition image that it would create. If you can work with this kind of graphics, go ahead.

By the way, the reason may be that clonezilla live is not meant for advanced graphics, so it would be expecting a simple vga monitor. As such, it simply may not be able to handle advanced graphics output like s-video. Remedy in my opinion would be - either use a VGA monitor, or take the long route (with possible hurdles), that is, use a live usb version of ubuntu or something that can handle this kind of video, then install and use clonezilla from there. ([guide for installing clonezilla on ubuntu]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/")).

Another attractive and easy option is to use [remastersys]("http://www.geekconnection.org/remastersys/"). But it is useful only if your installation can be stripped down to less than 4.4 GB (remastersys will do it automatically).

---

### Post by Kvothe666 on 2011-07-06
i was talking about when in ubuntu booted from the copied partition, am currently trying the live usb to 'update 11.04 to 11.04' to see if that corrects the issue

---

### Post by Kvothe666 on 2011-07-06
hmmm.. no change

---

### Post by varunendra on 2011-07-06
Well that means you've successfully transferred the installation from your laptop to the desktop (it's copied, and boots up). Now the graphics is a different issue.

Since the original issue has been resolved, I'd suggest to mark this thread as [Solved] and start another one for your current problem with graphics.

---

