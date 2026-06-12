---
title: "Failed Installation - Blank Tan Screen"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by conflabermits on 2007-09-09
I've tried i386 and 64-bit versions of Ubuntu 7.04, and can't get it to install. It hangs indefinitely at a light brown/tan screen with low resolution and a cursor after I click on "Install".

I did some checking and this post ([http://ubuntuforums.org/showthread.php?t=451419](http://ubuntuforums.org/showthread.php?t=451419)) was the most similar to the problem I'm having, but it has no definite answer.

Basics of my setup:
Dual-core Intel Xeon 3070 @ 2.66 GHz
2 sticks/4 GB Kingston PC2-5300 ECC 240-pin RAM
Asus P5M2/2GBL Motherboard
Evga e-GeForce 8600 GT at 256MB DDR3
500 GB RAID 1 with a WinXP partition

I'd be willing to answer any questions anyone has for more detail on the problem, and I'm sure I can make time to try some new solutions. Thanks in advance for any help!

---

### Post by merlinus on 2007-09-09
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can change the video driver to vesa from a command line to get to a gui, where you can search for and install the correct drivers.

---

### Post by merlinus on 2007-09-09
OTOH, you might due a search to see if 8G RAM is supported, as well as the type of raid array you are using.

---

### Post by conflabermits on 2007-09-09
Sorry, guess my stats were misleading. It's only 4 GB using 2 2GB sticks. My bad.

I'll try the alternate CD first, since that requires less time. I'll also try the normal CD after disabling the RAID or something (I have virtually nothing to lose on the WinXP partition). Thanks!

---

### Post by conflabermits on 2007-09-09
Looks like the text-based installer worked. Would that mean it was a problem with the GUI and the video card? It seemed to display correctly after installation.

---

### Post by merlinus on 2007-09-09
Quien sabe?  The text-based Alternate tries to only install, not give a test drive.

But glad it worked for you!

---

