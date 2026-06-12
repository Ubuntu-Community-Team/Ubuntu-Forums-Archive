---
title: "Easycap driver install"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by zolf42 on 2010-05-22
Bought [http://cgi.ebay.co.uk/Easycap-DC60-USB-Grabber-Video-Capture-4-VHS-Camcorder-/160433992374?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item255a9c72b6](http://cgi.ebay.co.uk/Easycap-DC60-USB-Grabber-Video-Capture-4-VHS-Camcorder-/160433992374?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item255a9c72b6)

So I have tried a few things now to install the drivers to get this thing going, but all attempts have failed. Can anybody give is tips, redirect me to another thread or give me straight up problem solving (anything). I'm running 10.04.

---

### Post by rmt1947 on 2010-05-22
I don't possess this device myself, so can't offer a quick solution, just a couple of remarks.

The Ebay advert says your EasyCAP DC60+ has the Empia 2861 chip, which means the command `lsusb` should show the device ID as eb1a:2861.  According to

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.em28xx](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.em28xx)

this is supported by the em28xx driver in recent kernels.

I googled for 

easycap eb1a:2861

and got 183 hits.  Some of these could perhaps be of interest.

---

### Post by zolf42 on 2010-05-22
184 now, this thread come out on top

---

