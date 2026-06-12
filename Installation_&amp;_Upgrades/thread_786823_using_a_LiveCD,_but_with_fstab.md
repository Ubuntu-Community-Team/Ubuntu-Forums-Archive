---
title: "using a LiveCD, but with fstab"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by scragar on 2008-05-08
I have to work with computers that normally run windows, and I've finally given in at work, and brought in a Live CD, however I got told I was not allowed to install it, not even for a dual boot, which unfortunately means I would be completely unable to customize the system, any idea's on how to let me mount my pen drive automatically using the live CD?

I know that it's possible to use 1 or 2 programs to let you build a personal live CD, which would let me make sure the live CD contains quanta and such like, however these programs do not backup fstab with the file, so I would be unable to set this when testing...

Any ideas?

---

### Post by lemming465 on 2008-05-10
I'm not sure about post-dapper, but supposedly a USB partition with label "casper-cow" would be auto-mounted as /home by the live CD.  I'm guessing newer versions have something similar.

---

### Post by Pumalite on 2008-05-10
Maybe this helps:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

