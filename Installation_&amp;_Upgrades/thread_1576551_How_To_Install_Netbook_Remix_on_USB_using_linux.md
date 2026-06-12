---
title: "How To Install Netbook Remix on USB using linux"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by TheNewbieGeek on 2010-09-17
I want to install Ubuntu Netbook Remix on USB stick. I have made a start disk so that I can install it to the hard drive or use live but I want to use my USB flash drive as my hard drive and boot from it like it's the hard drive. You see my hard drive is only 4gb and my usb stick is 16gb.  I have a asus eeepc so it is compatible thank you. Did a search and was surprised thier was not a post on this previously.

---

### Post by jmdlcar on 2010-09-17
I did a full install on an 8gb thumb drive and now I have it on an 320gb usb drive. What I did boot up the cd and pick install.

---

### Post by sikander3786 on 2010-09-17
Yes it can be installed the same way as a regular install. Just at the last stage of the installer, just before clicking install, click Advanced button and choose your USB for the installation of GRUB.

---

### Post by mikewhatever on 2010-09-17
You'll need another media to boot the installer from, a cdrom or a usb flash stick, whatever you prefer. There are other ways, but they are a bit more advanced.
[https://help.ubuntu.com/10.04/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/10.04/installation-guide/i386/linux-upgrade.html)
[https://help.ubuntu.com/10.04/installation-guide/i386/pppoe.html](https://help.ubuntu.com/10.04/installation-guide/i386/pppoe.html)
[https://help.ubuntu.com/10.04/installation-guide/i386/pppoe.html](https://help.ubuntu.com/10.04/installation-guide/i386/pppoe.html)

---

### Post by TheNewbieGeek on 2010-09-17
I'll try this and see if I can do it. thank you.

---

### Post by uRock on 2010-09-17
This link explains how to put the image on the thumb drive and then how to install it to the machine afterwards. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Joe of loath on 2010-09-17
Why not use the persistent live USB install? It will keep the USB going much longer, as there won't be as many read/write cycles. It'll also perform faster, and be easier to boot.

---

### Post by wilee-nilee on 2010-09-17
> **Joe of loath said:**
> Why not use the persistent live USB install? It will keep the USB going much longer, as there won't be as many read/write cycles. It'll also perform faster, and be easier to boot.

Actually a full install runs faster, and boots faster. A persistent ISO loaded will eventually fill up it can't be cleaned as easily as a full boot. You also are really not advised to upgrade kernels in this setup. I know that some of these problems can be worked around, but if the OP has a 16gig thumb their on the right track.

---

### Post by TheNewbieGeek on 2010-09-19
Thanks dudes I now have installed ubuntu on my netbook :-)

---

