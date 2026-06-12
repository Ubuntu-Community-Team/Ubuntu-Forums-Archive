---
title: "Wierd little X in the middle of my screen"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by K_Dallas on 2005-04-27
Hi!

I have a wierd problem which has been with me since I used Debian and at that time no one seemed to be able to help me. The problem is simple:

I boot and loginto my dektop then I get a cross, an X, in the middle of my screen which depending on the desktop I use, I can make it disappear by moving a terminal over it or just deal with it as it is, the case on XFCE. That is why I do not / cannot use XFCE.

I recall having read somewhere on the Ubuntu pages on the web a way to resolve this but now that I need it I do not seem to be able to find it.

Any help would be greatly appreciated.

---

### Post by nad on 2005-04-28
Read the man page for your video driver and xfce. There are usually options for configuring these types of problems.

---

### Post by az on 2005-04-28
The dreaded extra dead X pointer.

Upon installation on several Toshiba Laptops, we have had a problem with a dual pointer in X. One that works and one that sits in the middle of the screen. Mimimal research on this problem yielded the following fix.

Add the following line:

    *

      Option "HWCursor" "off"'

to your /etc/X11/XF86Config-4 in the place shown below:

::

    *

      Section "Device"
          o

            Identifier "S3 Inc. 86C270-294 Savage/IX-MV" Driver "savage" BusID "PCI:1:0:0" Option "HWCursor" "off"
      EndSection

Then Reboot X <cntrl> <alt> backspace, and you will only have one working pointer (pflint)

    *

      See also:* [http://www.ubuntulinux.org/support/documentation/faq/hwcursor](http://www.ubuntulinux.org/support/documentation/faq/hwcursor)

---

### Post by K_Dallas on 2005-04-28
Oh man! That tinny X was driving me crazy :)


I am glad it is gone and thanks very much for the help. I should have bookmarked that page but again, you guys are amongst the best technical supports that I have seen.

Thanks Azz, bunches!
K_Dallas

PS: I should have come and knocked at your door ;) We are not that far away (Montreal) afterall :):)

---

