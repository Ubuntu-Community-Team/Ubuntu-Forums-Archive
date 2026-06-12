---
title: "USB Live Stick"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by Mel_Blakey on 2015-01-13
_[COLOR=#800000]**Ubuntu 14.04**[/COLOR]_

Considering that it weighs in at just under 1Gb. Why is it that Ubuntu requires 'a memory stick with a capacity of at least 2GB' ?.

I have a 2GB stick and its actual capacity is just under. Also I wanted to partition a couple of MB to put on some Install doc's & some wallpaper in there and have the iso in the 1st partition for a friend of mine who wants to give it a try.

Thanks in advance. :KS

---

### Post by sudodus on 2015-01-13
I think the recommendation is written like that because

- 2 GB pendrives are the smallest in the market now.

- it would be good to have some extra space either for some data files like in your case, or to have space for a casper-rw file or partition in order to make a persistent live drive.

But it is certainly possible to make an Ubuntu boot USB drive of a drive that is just big enough for it to be installed (1 GB). Sometimes USB drives are slightly 'undersized' (smaller than the nominal size). It is no problem in your case :-)

-o-

You may find useful information at this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ubfan1 on 2015-01-13
The live usb startup disk creator will no longer offer a persistence file on a 2G USB stick, since the minimum size is set to 1024K, and there isn't 
that much room left.  Edit the MIN_PERSISTENCE line in the
/usr/lib/python3/dist-packages/usbcreator/misc.py file.
Setting it to 800K will allow the persistence to be set on a 2G stick.

---

### Post by Mel_Blakey on 2015-01-13
Great!!!
Thanks to both of you for your rapid replies....

Very helpful!

Regards

---

